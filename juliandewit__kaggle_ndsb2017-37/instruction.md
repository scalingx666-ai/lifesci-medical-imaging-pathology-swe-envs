# Issue

**Title:** Including "subset0" for LUNA16 processing

## Description

Unless there's a reason I haven't understood yet, I would expect to start processing with the luna_raw/subset0 directory rather than luna_raw/subset1.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d1f3433a6baf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.