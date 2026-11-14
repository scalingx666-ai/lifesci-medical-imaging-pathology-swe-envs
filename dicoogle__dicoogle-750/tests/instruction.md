# Issue

**Title:** Detect data storage failure in DicomStorage

## Description

### Motivation

This pull request implements a slightly different approach #721, invalidating #722. By catching run-time exceptions and treating null output as a failure, we can keep the SDK backward compatible and report to the SCU that the object was not stored with sufficient reliability.

At BMD we have a use case were this is critical, so we will consider pushing this for version 3.6.0.

### Summary

- catch runtime exceptions on store, treat it as a failure
- return a failure C-STORE-RSP if there were no successful stores
- exclude default-filesystem-plugin from C-STORE req handling routine, as this one does not implement store

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fbcc08e1a6b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.