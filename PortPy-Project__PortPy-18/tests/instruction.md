# Issue

**Title:** Add prediction-based dose mimicking APIs to VMAT column generation

## Description

### Summary
This PR extends column generation to support VMAT dose mimicking, using a workflow consistent with the existing implementation.

### Key changes
- Supports both PTV and OAR dose mimicking during column generation
- Predicted dose is incorporated as an optional input

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `da638032adb1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.