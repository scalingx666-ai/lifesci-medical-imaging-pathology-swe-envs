# Issue

**Title:** fix(ui): track the presented video frame during playback

## Description

### Summary

The annotator draws the frame delivered by `requestVideoFrameCallback`, while its frame index rounds up from the playback clock. In a Chromium probe with a 7.5 fps video, the calculated index was one frame ahead in 9 of 20 callbacks.

Use the presented frame's `mediaTime` and round to the nearest frame index. The regression tests cover a playback clock that has advanced beyond the presented frame, a fractional frame rate, and frame zero.

### How to test

- Run `npm run test:unit -- src/modules/annotator/video-player/video-frame.component.test.tsx` from `application/ui`. Two cases fail on unchanged `develop` and all three pass with the fix.
- The review update passed 106 focused tests, scoped formatting and ESLint, TypeScript, and the import-cycle check.
- The clean Ubuntu 24.04 run passed all 1,823 UI unit tests, formatting, ESLint, import-cycle checks, TypeScript, and the web and desktop asset builds. [Validation run](https://github.com/A-P-S-Bhaidav/geti/actions/runs/43001852333)
- All eight Chromium video component tests passed against the production preview with mocked API responses.
- Two webhook tests timed out in the local macOS suite. All five tests in that file passed in isolation with the original timeouts.

### Checklist

- [x] The PR title and description are clear and descriptive
- [x] I have manually tested the changes
- [x] All changes are covered by automated tests
- [x] All related issues are linked to this PR (if applicable)
- [x] Documentation has been updated (if applicable)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc98b5077ef9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.