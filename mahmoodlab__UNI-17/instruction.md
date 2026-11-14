# Issue

**Title:** Sort-prune-imports

## Description

1. removed h5py import because it was never used, but was introducing a dependency

2. removed duplicate imports, e.g. torch was imported multiple times in some files

3. sorted imports in order: built-in, installed, locally-defined

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `449f95b5dd9c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.