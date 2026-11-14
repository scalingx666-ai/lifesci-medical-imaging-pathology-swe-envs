# Issue

**Title:** Fix segmentation cropping and feature map restore issues during inference

## Description

Include fixes for segmentation cropping and feature map restores, as indicated in issues #319 and #155 See lines 451-457 in patching.py and lines 143-145 in restore.py

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0504dc6daa0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.