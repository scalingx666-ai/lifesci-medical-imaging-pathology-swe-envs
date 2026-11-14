# Issue

**Title:** Ensure single character recognition model respects device availability

## Description

## Summary
- add a device attribute to the single character recognition model so it can run on CPU or GPU
- move the model weights and inference inputs onto the detected device

## Testing
- python -m compileall OCRAutoScore/scoreblocks/singleCharacterRecognition.py

------
https://chatgpt.com/codex/tasks/task_e_68c8f07745fc832a9598f0e747f73303

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e6c1d71161ea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.