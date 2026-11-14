# Issue

**Title:** Feat/eeg import without registration json

## Description

- Allows importing EEG montages without the InVesalius registration JSON, using declared coordinate systems or fiducial-based coordinate conversion.

- Adds optional projection onto an existing smoothed scalp surface, without generating one during import. Existing imports with registration metadata remain supported.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b16bf03c01bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.