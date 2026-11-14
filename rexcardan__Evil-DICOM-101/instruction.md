# Issue

**Title:** IdleTimeout added (SpinUpAssociation, DICOMSCP)

## Description

DICOMSCP is missing IdleTimeout. Connection breaks for large RT Dose files.
As a developer, I need to overwrite the default hard-coded timeout of 25secs, so I am able to receive large RTDose files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `027f4d19c0f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.