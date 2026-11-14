# Issue

**Title:** Performance/itk array

## Description

Replace array copy operations with `np.ascontiguousarray` to improve performance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f7ea7814c043`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.