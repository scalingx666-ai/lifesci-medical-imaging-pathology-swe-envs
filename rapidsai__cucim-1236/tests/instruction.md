# Issue

**Title:** Avoid CMake 4.5 CUDA target export incompatibility

## Description

## Description

Constrain CMake to `<4.5` in build dependencies and regenerate dependency files. CMake 4.5 exports CUDA link dependencies using `CUDAToolkit::` target names, which breaks consumers using older CMake versions.

Contributes to

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `da1bba43c680`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.