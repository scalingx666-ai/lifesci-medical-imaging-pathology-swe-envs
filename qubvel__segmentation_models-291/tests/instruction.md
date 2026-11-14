# Issue

**Title:** Allow passing keyword arguments to backbone models

## Description

Make kwargs supported (#230)

Instead of writing custom ```get_submodules_from_kwargs``` function, I decided to filter arguments passed to this function but the basic idea is same.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a6fbf2d5ea21`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.