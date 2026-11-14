# Issue

**Title:** fix(legacy): skip the value length of command group elements in AsyncDicomReader

## Description

## Summary

This PR ports the fix of #597 to the `1.0-beta` branch. Iman974 found the defect and wrote the fix in #597.

## Problem

`AsyncDicomReader.read()` skips the value of two types of element:

- a command group element `(0000,xxxx)`
- the `DataSetTrailingPadding` element `(FFFC,FFFC)`

The reader called `stream.increment(tagObj.length)`. The `Tag` class has no `length` property, so the stream offset became `NaN`. The read loop compares the offset with a limit, and a comparison with `NaN` is always false. Thus the read stopped without an error, and the reader lost all tags after that element.

## Change

- `packages/legacy/src/AsyncDicomReader.js`: the reader uses `length` from the tag header, and not `tagObj.length`.
- `test/issues/pr597-async-reader-skip.test.js`: a new test writes a file with a `(0000,0002)` element. The test checks that the async reader skips that element, and reads `Rows` and `PixelData` after it.

## Tests

- The new test fails without the fix, and passes with the fix.
- `test/async-data.test.js`, `test/sync-async-parser-equivalency.test.js`, and `test/issues/` pass: 123 passed, 10 skipped.
- Prettier and ESLint pass on the two files.

Related: #597

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f6b54cd2b722`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.