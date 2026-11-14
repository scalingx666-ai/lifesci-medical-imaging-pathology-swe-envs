# Issue

**Title:** Update WholeSlideImage.py

## Description

Reduce minimum number of patches per slide from 2 to 1. This is particularly useful when using large patches, such as the 4096x4096 patches of HIPT_4K.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9482cbc72df5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.