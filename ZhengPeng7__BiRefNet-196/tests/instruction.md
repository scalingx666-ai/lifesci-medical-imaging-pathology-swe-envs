# Issue

**Title:** Handle non-RGB Pillow images

## Description

Hi, a small PR for the notebook demo when the selected images are not interpreted as RGB images (i.e., 4 channels, etc.) to avoid that kind of error : 

> RuntimeError: The size of tensor a (4) must match the size of tensor b (3) at non-singleton dimension 0

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a20130621432`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.