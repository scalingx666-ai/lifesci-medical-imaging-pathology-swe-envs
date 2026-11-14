# Issue

**Title:** Use setup-miniconda action

## Description

- using another action alone did not help (but may be needed)
- checking if Python 3.10 has to be removed (EOL) - nope

_Edit:_ The setup-miniconda action works fine, but needs bash as a shell (`sh` does not work).
Also changed the PR workflow to test both the first and last supported Python versions.

#### Tasks
- [x] Fix or feature added
- [x] Unit tests passing and coverage at 100% after adding fix/feature

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd0a91eb1e27`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.