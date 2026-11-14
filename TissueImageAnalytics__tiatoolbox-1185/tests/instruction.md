# Issue

**Title:** 🔨  Add `mypy` type check to `wsireader` files

## Description

`mypy` type check now covers all files under `wsireader/` except `base.py`. 

TODO: Improve test coverage.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd79833bf7a4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.