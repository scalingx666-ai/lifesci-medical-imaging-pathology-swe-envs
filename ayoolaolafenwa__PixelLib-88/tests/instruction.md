# Issue

**Title:** Adding function to extract masks and other information in semantic segmentation

## Description

This pull adds a modification on the main function "segmentAsAde20k()", the purpose of this modification is to allow to get information about masks, pixel % ratios of segmented objects, class names, class index, and their respective color.

Now, after running the function segmentAsAde20k, you will have 3 outputs:

segmap (mapped mask), output (resulting image (overlayed or not), and a list of masks segmented.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7e4da962468f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.