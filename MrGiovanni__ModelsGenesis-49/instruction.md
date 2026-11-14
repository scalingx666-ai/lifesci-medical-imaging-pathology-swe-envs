# Issue

**Title:** Major refactoring and bugfixes to allow data preprocessed by nnUNet

## Description

Refactoring:
- move steps to generate a single pair to a separate function, generate_single_pair and update generate_pair.
- rename data_augmentation to random_flip_all_axes and update generate_pair.
- added documentation about expected inputs and outputs

Bugfixes for data preprocessed by nnUNet:
- change axes of random_flip_all_axes from [0, 1, 2] to [-1, -2, -3] to allow any number of preceding dimensions (e.g., multiple MRI modalities)
- change points in nonlinear_transformation to allow z-score normalisation (instead of [0, 1] range)
- apply local_pixel_shuffling to all modalities instead of the first only
- update image_in_painting and image_out_painting to work with a single modality, allowing per-modality in & out painting

Cleanup: 
- remove unnecessary imports
- PEP8

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13932523d175`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.