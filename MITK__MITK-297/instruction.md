# Issue

**Title:** Update ITK to 5.4.2 to fix libtiff duplicate compiler error on newer MSVC versions

## Description

ITK 5.4.0 suffers from a compiler error concerning a duplicated `__ucrt_int_to_float` symbol with current MSVC compiler versions.
The most recent version ITK 5.4.2 includes a fix for this via  PR.

I'd suggest to update ITK so that MITK compiles with current MSVC versions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7c15e0cb050e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.