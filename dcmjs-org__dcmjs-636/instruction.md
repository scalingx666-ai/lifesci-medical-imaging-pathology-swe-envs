# Issue

**Title:** fix(core): remove the debug log of an InlineBinary value in DicomMetadataListener

## Description

## Summary

This change removes a debug `console.log` from `_basePop` in `packages/core/src/utilities/DicomMetadataListener.js`.

- When a filter set `InlineBinary` on a value, `_basePop` wrote `"********* InlineBinary already set"` to the console. The log also wrote the whole result object and the listener state.
- A filter that converts a binary value to `InlineBinary` is a valid use of the listener. Thus the log gave no useful information, and the log wrote a large amount of text for each value.
- Static-DICOMWeb has an `inlineBinaryFilter` that does the work of the base pop itself, only to prevent this log. After this change, a filter can call `next()` as usual.

The behaviour of `_basePop` does not change in other ways.

## Test results

- `npx eslint packages/core/src/utilities/DicomMetadataListener.js` passes.
- `npx jest --testPathPattern "DicomMetadataListener|AsyncDicomReader|eventStream|inline"`: 20 test suites pass, with 392 tests passed and 1 test skipped.

I did not run the full test suite.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `108d99e62bdf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.