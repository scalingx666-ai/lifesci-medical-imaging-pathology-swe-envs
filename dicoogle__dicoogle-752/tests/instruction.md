# Issue

**Title:** Extend plugin set dead condition to failures on platform injection

## Description

If one of the plugins or the entire plugin set throws an exception during platform injection, mark it as dead, or shut down Dicoogle entirely if the kill-switch is enabled.

This makes serious problems with the plugins less likely to be overlooked.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5451de4e8265`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.