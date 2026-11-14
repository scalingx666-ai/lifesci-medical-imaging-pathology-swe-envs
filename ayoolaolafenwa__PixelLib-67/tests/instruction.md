# Issue

**Title:** Create function to set detection threshold for instance segmentation

## Description

Dear Ayoola,

Thanks for creating pixellib! I have a small pull request to change the detection threshold for the instance segmentation.

If you accept the pull request, I will be able to call pixellib with:
```python
segment_video = instance_segmentation()
segment_video.set_detection_confidence(0.1) # new strategy
segment_video.load_model("mask_rcnn_coco.h5")
segment_video.segmentImage("frame.png", output_image_name = "out.jpg")
``` 
Please let me know if you want me to make any changes. Best regards, Daniel

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `727a073c4ce9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.