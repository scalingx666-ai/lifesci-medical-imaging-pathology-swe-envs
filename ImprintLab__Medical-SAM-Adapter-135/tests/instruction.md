# Issue

**Title:** Fix critical bugs and add evaluation features

## Description

## Bug Fixes

### Bug1: random click (x, y) order
**Fixed coordinate order mismatch between point prompts and SAM's expectation.** 
In function `random_click` np.argwhere returns indices in (y, x) format, while SAM requires (x, y) format. The fixing will increase training performance and efficiency.

### Bug2: Incorrect GT_mask during validation
**Fixed GT mask modification issue during visualization that affected evaluation accuracy.**
In some validation epoch, `vis_image` is used for showing the prediction. But in `vis_image`, the `gt_masks` used in `eval_seg` is modified by `gt_masks[i,0,p[i,0]-5:p[i,0]+5,p[i,1]-5:p[i,1]+5] = 0.5`, because the passed `gt_masks` is not a *cloned* version. The bug changes the `gt_masks` by adding gray pixels on it wrongly and affects the validation result accuracy.

### Bug3: Align Pre/post-processing with SAM
**Added missing SAM pre/post-processing steps in training pipeline.**
For pre-processing, in original implementation, the image is transformed by `ToTensor`, which is resized to [0, 1]. While in SAM, an input image is in [0, 255] style, which is normalized with a pre-defined pixel-mean and pixel-std. For post-processing, bilinear interpolate is used to resize pred to mask shape instead of nearest. Add pre-processing to training pipeline to keep the same with SAM.

### Bug4: Random seed not taking effect properly
**Support set random seed for reproducibility.**
In `function.py`, `seed` is inited by `torch.randint(1,11,(args.b,7))`. While the `seed` is not used anywhere. The PR support user providing seed and set seed for torch, numpy and random. The fixed code can ensure reproducibility. 

### Bug5: Incorrect dimension expansion
**Fixed incorrect dimension expansion in one-point prompt scenarios.** 
In `function.py`, when one-point prompt is given, the code `coords_torch, labels_torch, showp = coords_torch[None, :, :], labels_torch[None, :], showp[None, :, :]` expand Tenser `B*N` to `1*B*N`. However, the following code in SAM (transformer), will expand the Tensor to `B*B*N` automaticaly. The original expansion operation wrongly forecasts all points to each in-batch data item in fact. The solution is expanding tensor in dim 1, i.e.,   `coords_torch, labels_torch, showp = coords_torch.unsqueeze(1), labels_torch.unsqueeze(1), showp.unsqueeze(1)`. The fixed operation expands the tensor from `B*N` to `B*1*N`, also aligning with `B*P*N` in multi-point scenarios.

### Bug6: Logging training loss for last-batch only
**Fixed training loss logging (last-batch -> average).**
In `train_sam`, the return is last-batch loss, written into logging file. The fixed code logs the average during training. 

### Bug7: Incorrect metrics calculation
**Change metric calculation from batch-level to item-level.** 
The `eval_seg` function  calculate the in-batch average metrics, and in `validation_sam`, the average metrics is averaged by validation steps. While, considering a case that the last-batch has only one-item, and other batches have 1024 items in each, the last-batch is over-weighted 1024 times and influence the metrics calculation. The fixed code takes this in consideration and calculate the item-level metrics.

### Bug8: Incorrect for-loop implementation in vis
**Fixed incorrect for-loop implementation in multi-point prompting scenarios.** The original for-loop is:
```
for i in range(b):
    ...
    for p in ps:
        operation(p[i, 0])
```
The ps is a tensor of Shape `B*P`, the two for-loop is both for batch-level loop and will cause Error when multi-point prompting. The fixing change the second for-loop to point-level loop.

## New Features

### Feat 1: Applied Sigmoid to predictions during evaluation to normalize values between 0-1
 Noting that the evaluation threshold is set to (0.1, 0.3, 0.5, 0.7, 0.9). If the pred range form ($- \inf$ to $+ \inf$), the threshold makes nonsense. So the fixing code applies Sigmoid to pred.

### Feat2: Evaluation before Training
To show SAM adapter's zero-shot performance and validate evaluation code correctness, the committed code conducts evaluation when `epoch == 0`.

## Impact
- Improved model reliability and evaluation accuracy
- More robust handling of various prompt scenarios
- Better metric calculation and logging
- Enhanced validation pipeline with zero-shot testing

## Experiments
### Dataset
To verified the committed code, experiments are also conducted on `ISIC` and a dataset called `SHAPE` created by @JaireYu. The `SHAPE` dataset is consisted of random multiple isolated Convex polygons and Ellipse drawn on 1024X1024 canvas.  The dataset is attached [here].([SHAPE.zip](https://github.com/user-attachments/files/19801001/SHAPE.zip))

### Results
##### IOU @ ISIC
|code version| SAM-Adapter | batch_size = 1| batch_size = 4|
|---| --- |--- |--- |
|origin code| Before Training| 13.71 | 19.58 |
|PR code|Before Training| 12.73 | 12.99 |
|origin code|Max in 5 epoch| 85.21 | 85.42|
|PR code|Max in 5 epoch| 86.10 | 86.75 |

##### IOU @ SHAPE
|code version| SAM-Adapter | batch_size = 1| batch_size = 4|
|---| --- |--- |--- |
|origin code| Before Training| 9.29 | 6.84 |
|PR code|Before Training|  81.61 | 81.20 |
|origin code|Max in 5 epoch| 80.69 | 14.23 |
|PR code|Max in 5 epoch|  96.92 | 97.58 |

Note: the above PR code evaluation does not include pred Sigmoid feature to make fair comparison.

### Analysis

The Model trained on PR code shows better or comparable performance without any training and with 5 epoch traing, especially on SHAPE dataset. Referring to BUG 1, the reason is that in ISIC, almost all masks are placed at center of the images, which means flipping (x, y) is acceptable. However, for the SHAPE data, the masks are placed randomly, flipping (x, y) is unacceptable. The following two images support this point.
|origin code (before training)|PR code (before training)|
|---| --- |
|![Clipboard_Screenshot_1744921211](https://github.com/user-attachments/assets/0768d728-f970-484e-8d75-0134a4701bf4)|![Clipboard_Screenshot_1744921177](https://github.com/user-attachments/assets/4bc5012b-d59b-4dcb-a29c-32ca302c43bc)|

Another interesting thing is: using the origin code, batch size = 4 performs much worse than batch size = 1 (14.23 v.s. 80.69). Referring to BUG 5, the reason is that all points in batch are gathered and fed into SAM. The incorrect data processing makes the model hard to converge. The following is the visualization:
|origin code (5 epoch)|PR code (5 epoch)|
|---| --- |
|![Clipboard_Screenshot_1744922997](https://github.com/user-attachments/assets/4c5d4181-9bae-4093-91ea-be7288c06d8a)|![Clipboard_Screenshot_1744923108](https://github.com/user-attachments/assets/e0c0a621-5364-46a2-8214-d42b9a279ba2)|

## Attention
Because the `net.preprocessing` (pixel-mean and pixel std normalization) is introduced in training pipeline, `get_decath_loader` may be needed to changed slightly.

Please review and test thoroughly before merging. 

Moreover, I noticed these fixes might affect some of the experimental results and conclusions in your paper. If you plan to update the paper or release a report addressing these corrections in the future, I would appreciate being involved in the discussion, as these modifications could be significant to the research findings.

Feel free to contact with me if you'd like to discuss the impact of these changes on the research conclusions. I'm happy to contribute further to ensure the academic record accurately reflects these important technical details.

Merge it and help the people in the research community!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4dcdc63c65c5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.