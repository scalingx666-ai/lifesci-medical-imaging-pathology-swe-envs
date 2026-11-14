# Issue

**Title:** Accept SDK names in CMAKE_OSX_SYSROOT

## Description

CMAKE_OSX_SYSROOT accepts SDK names such as macosx as well as filesystem paths. The existing existence check rejects SDK names as missing files. Limit this guard to absolute paths, preserving the error for a missing absolute SDK path while allowing CMake to resolve SDK names.

Validation: retained focused synthetic CMake script evidence fails on macosx before the change and passes afterward; the same check also confirms that a missing absolute SDK path still fails. No unchanged checks were rerun for publication.

This verifies the configuration guard only. Native compilation and Apple Silicon hardware behavior were not tested; the change is not ARM64-specific.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5571494a1441`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.