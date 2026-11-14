# Issue

**Title:** Fix/eeg tab visibility

## Description

- Show the EEG tab only in navigation mode when electrode capture is active or digitized electrodes exist.
- When assigning an occupied label, give it to the selected electrode and rename its previous owner with an available generic name.

Related to #1552

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f76560455670`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.