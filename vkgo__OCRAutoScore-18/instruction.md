# Issue

**Title:** Use in-place Xavier uniform initialization in essay score model

## Description

## Summary
- switch the essay score model's linear layer initialization to use `torch.nn.init.xavier_uniform_`
- ensure weights are updated in place when initializing

## Testing
- not run (not requested)

------
https://chatgpt.com/codex/tasks/task_e_68c8f083b4d8832a865c828fde3352b7

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e6c1d71161ea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.