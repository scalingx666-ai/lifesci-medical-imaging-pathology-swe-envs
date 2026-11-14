# Issue

**Title:** Fix device mismatch errors in torchstain color space conversion functions

## Description

The `rgb2lab()` and `lab2rgb()` functions in `torchstain/torch/utils/` were failing with `RuntimeError: Expected all tensors to be on the same device` when processing CUDA tensors.

This occurred because:
Constant tensors (`_rgb2xyz`, `_white`, `_xyz2rgb`) were created on CPU by default

Input tensors were on CUDA devices
PyTorch operations between tensors on different devices are not allowed

**Solution**
Modified both functions to automatically detect the input tensor's device and move constant tensors to the same device:
1. `rgb2lab.py`: Added device detection and moved `_rgb2xyz` and `_white` tensors to input device
2. `lab2rgb.py`: Added device detection and moved `_white` and `_xyz2rgb` tensors to input device

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7c2a95f87fd5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.