# Issue

**Title:** Release 0.5.2

## Description

- Fixed #131 - ASSD computation raises errors
- Added tests for ASD and ASSD metrics
- Fixed obsolete use of `np.array(*, copy=False)`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91d31a7e2707`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.