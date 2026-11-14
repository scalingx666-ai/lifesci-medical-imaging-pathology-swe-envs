# Issue

**Title:** fix: Video frames annotations should return empty label annotation

## Description

<!-- Contributing guide: https://github.com/open-edge-platform/training_extensions/blob/develop/CONTRIBUTING.md -->

### Summary

<!--
Please add a summary of changes. You may use Copilot to auto-generate the PR description but please consider
including any other relevant facts which Copilot may be unaware of (such as design choices and testing procedure).

Add references to the relevant issues and pull requests if any like so:

 and #222.
Depends on #1000 (for series of dependent commits).
-->

The issue is that annotations and (video frames) predictions query were mapping the response to add empty label if needed but video frames annotations query doesn't. This PR fixes that.

### How to test

<!-- Describe the testing procedure for reviewers, if changes are
not fully covered by unit tests or manual testing can be complicated. -->

### Checklist

<!-- Put an 'x' in all the boxes that apply -->

- [ ] The PR title and description are clear and descriptive
- [ ] I have manually tested the changes
- [ ] All changes are covered by automated tests
- [ ] All related issues are linked to this PR (if applicable)
- [ ] Documentation has been updated (if applicable)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc031a4beadf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.