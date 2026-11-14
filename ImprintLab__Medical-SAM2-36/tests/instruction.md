# Issue

**Title:** fix: typo and reshaping func in 2d data

## Description

- fix some typos in readme
- in func_2d/function.py file, reshaping vision_feats_temp is causing runtime error
- fixed by changing .view() func to .reshape()

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ccc234ed578a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.