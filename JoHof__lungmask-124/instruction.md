# Issue

**Title:** Fix/lobe fusion 0.2.22

## Description

- Fixed lobe fusion discarding valid fill-only lung voxels.
- Fixed label loss in masks without background and hole filling in small single-slice masks.
- Fixed crashes when selecting the largest component of an empty mask.
- Fixed slice ordering for non-axial DICOM series.
- Fixed custom model paths overriding model-name validation.
- Fixed fusion ignoring the progress-disable option.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb586878057c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.