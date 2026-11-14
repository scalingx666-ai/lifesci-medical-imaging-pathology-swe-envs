# Issue

**Title:** Update montage2d to scikit-image 0.20

## Description

The `multichannel` field in `skimage.util.montage` has been deprecated in version 0.20.

Update function call to work with the new API.

From the relase notes for 0.20:
Remove deprecated parameter multichannel; use channel_axis instead. [...] In skimage.util, this affects montage and apply_parallel ().

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `16e3ead23ceb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.