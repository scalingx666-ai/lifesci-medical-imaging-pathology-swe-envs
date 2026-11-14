# Issue

**Title:** CI: let the artifact upload retry actually retry

## Description

The package upload in each build job is guarded by a retry step that re-runs `actions/upload-artifact` under the same artifact name when the first attempt fails. That only helps when the first attempt failed *before* it registered the name.

## What went wrong

On the Intel macOS job of [run 34611736400](https://github.com/QIICR/dcmqi/actions/runs/34611736400/job/103303995650) the upload got a `403 Forbidden` at the **FinalizeArtifact** stage — which runs after `CreateArtifact`, so `dcmqi-macos-x86_64-package` was already registered on the run. The retry then failed with

```
Failed to CreateArtifact: Received non-retryable error: Failed request:
(409) Conflict: an artifact with this name already exists on the workflow run
```

and because the retry — unlike the first attempt — has no `continue-on-error`, the job went red even though the build succeeded and all 93 tests passed.

## What changes

Each of the four upload retries (`linux`, `linux-arm64`, `macos`, `windows`) gets:

- **`overwrite: true`** — deletes a matching artifact before uploading, and is [documented](https://github.com/actions/upload-artifact/blob/main/action.yml) as *"Does not fail if the artifact does not exist"*, so the one setting covers both failure modes: the name was registered, or it was not.
- **`continue-on-error: true`** — matching what the first attempt already has. Packaging is not what these jobs exist to verify, and a transient upload error should not fail a job whose build and tests passed.

No other behaviour changes; the artifact names, paths and `if:` conditions are untouched.

## Verification

All five workflow files still parse, and each retry step now carries both keys:

```
cmake-linux.yml: retry steps -> [(build-linux, True, True), (build-linux-arm64, True, True)]
cmake-macos.yml: retry steps -> [(build-macos, True, True)]
cmake-win.yml:   retry steps -> [(build-windows, True, True)]
```

The failure itself is a first occurrence — the last dozen macOS runs on `master` are all success or cancelled — so this is about the retry being able to do its job when the flake recurs, not about a persistent breakage.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0ed03e9d67fc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.