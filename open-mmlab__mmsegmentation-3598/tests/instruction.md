# Issue

**Title:** [Fix] Fix cd transform

## Description

Thanks for your contribution and we appreciate it a lot. The following instructions would make your pull request more healthy and more easily get feedback. If you do not understand some items, don't worry, just make the pull request and seek help from maintainers.

## Motivation

Fix the bug that data augmentation only takes effect on one image in the change detection task.

## Modification

configs/base/datasets/levir_256x256.py
configs/swin/swin-tiny-patch4-window7_upernet_1xb8-20k_levir-256x256.py
mmseg/datasets/transforms/transforms.py

## Checklist

1. Pre-commit or other linting tools are used to fix the potential lint issues.
2. The modification is covered by complete unit tests. If not, please add more unit test to ensure the correctness.
3. If the modification has potential influence on downstream projects, this PR should be tested with downstream projects, like MMDet or MMDet3D.
4. The documentation has been modified accordingly, like docstring or example tutorials.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5465118b8c29`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.