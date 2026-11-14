# Issue

**Title:** [dump] Add aliases for `until` in CLI

## Description

This option is relatively useful, but it has been difficult to memorize. This PR adds `--stop «tag»` and `--stop-at «tag»` as aliases for `--until «tag»`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `065cd3a8fb08`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.