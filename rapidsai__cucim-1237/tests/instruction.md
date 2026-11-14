# Issue

**Title:** Forward-merge release/26.12 into main

## Description

Forward-merge triggered by push to release/26.12 that creates a PR to keep main up-to-date. If this PR is unable to be immediately merged due to conflicts, it will remain open for the team to manually merge. See [forward-merger docs](https://docs.rapids.ai/maintainers/forward-merger/) for more info.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7fa698916c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.