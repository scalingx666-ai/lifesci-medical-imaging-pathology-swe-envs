# Issue

**Title:** fix(suv display): fix scaling of non-SUV PT images

## Description

Currently PT images that are not in SUV are not rescaled at all. This is problematic because PT images can be in units of e.g. counts or Bq/ml, so it's important that the rescaling is applied in those cases.

cc @sedghi this is the same fix as in

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b8092fc20f6c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.