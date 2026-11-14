# Issue

**Title:** fix HDF4 detection in CMake (for newer versions of HDF4). closes #2230

## Description

This fixes Issue #2230 so that gnudatalanguage can properly detect and compile with the latest HDF4 version 4.4.0. Older HDF4 should still work too.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `26bf9ab7bb4b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.