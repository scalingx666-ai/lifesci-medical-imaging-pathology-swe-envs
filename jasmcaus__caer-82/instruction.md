# Issue

**Title:** fix yuv and luv color conversions

## Description

### Description

Ten color conversions compute a BGR intermediate and then discard it, converting the original YUV/LUV array as if it were BGR. The result is silently wrong pixel values:

- `yuv2gray`, `yuv2hsv`, `yuv2hls`, `yuv2lab`, `yuv2luv` (`caer/color/_yuv.py`)
- `luv2gray`, `luv2hsv`, `luv2hls`, `luv2lab`, `luv2yuv` (`caer/color/_luv.py`)

`caer.to_gray()`, `to_hsv()`, `to_hls()`, `to_lab()`, `to_yuv()` and `to_luv()` call these functions, so they were affected too for YUV/LUV inputs.

**Reproduction**

```python
import cv2 as cv
import numpy as np
import caer

bgr = caer.data.sunrise(rgb=False)
yuv = caer.to_tensor(cv.cvtColor(bgr, cv.COLOR_BGR2YUV), cspace="yuv")
expected = cv.cvtColor(cv.cvtColor(yuv, cv.COLOR_YUV2BGR), cv.COLOR_BGR2GRAY)

print(np.array_equal(caer.yuv2gray(yuv), expected))          # False on dev, True with this PR
print(np.array_equal(caer.yuv2gray(yuv), caer.bgr2gray(yuv)))  # True on dev: YUV data treated as BGR
```

**Tests**

The existing tests only checked the output shape and the `cspace` flag, so the bug went unnoticed. Each of the 10 affected tests in `tests/color/test_yuv.py` and `tests/color/test_luv.py` now also asserts the result equals OpenCV's `X -> BGR -> Y` conversion. These asserts fail on `dev` (10 failed) and pass with the fix. The full suite passes locally (`pytest -v ./tests`: 83 passed).

### Types of changes
- [x] Bug fix (non-breaking change which fixes an issue)
- [ ] Breaking change (fix or new feature that would cause existing functionality to change)
- [ ] Docstrings/Documentation updated
- [ ] New Feature to Caer
- [ ] New Examples to [`examples`](https://github.com/jasmcaus/caer/tree/master/examples)
- [x] New tests added to cover the changes


### Related Issues



### Checklist:
- [x] I have followed the [contribution guidelines](CONTRIBUTING.md) and code style for this project.
- [x] I have added tests covering my contributions (**important**).
- [ ] I have updated the documentation accordingly.
- [x] This PR is being made to `dev` and not `master` (**important**).
- [ ] I will squash merge this PR into `dev` (optional)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c313af561eae`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.