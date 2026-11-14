# Issue

**Title:** fix JointTransform2D applied to train dataset

## Description

In train script, there are two JointTransform2D instances while only `tf_val` is used for both train/val datasets. It seems that `tf_train` need to be applied for the train datasets.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `10fb5a705d41`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.