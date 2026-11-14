# Issue

**Title:** feat: Implemented support for MultiMacenkoNormalizer across all backends

## Description

.

## Changes
- [x] Implement support for TensorFlow
- [x] Implement support for NumPy
- [x] Added new tests for checking that different backends produce the same result
- [x] Minor refactoring

## Testing
To test code, you can either run directly or do what I do in the tests. See these examples:
* https://github.com/andreped/torchstain/blob/feat/multitarget-macenko-support-all-backends/tests/test_torch.py#L131
* https://github.com/andreped/torchstain/blob/feat/multitarget-macenko-support-all-backends/tests/test_tf.py#L84

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e10af229999`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.