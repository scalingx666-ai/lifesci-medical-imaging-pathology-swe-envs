# Issue

**Title:** FIX: sets default prefetch factor to 1

## Description

Prefetch factor was set to None by default for inference which raises an error during prediction. Changed the default to 1 which is the same as training.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b76f9c91f24`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.