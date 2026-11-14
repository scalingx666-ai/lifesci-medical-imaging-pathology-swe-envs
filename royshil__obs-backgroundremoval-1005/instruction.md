# Issue

**Title:** Add actions.lock

## Description

This change locks the external actions on our CI pipelines. I'd like to harden CI/CD processes with the first-party toolings.

## Changes

- Ran `gh actions-lock`
- Added `.github/workflows/actions.lock` to REUSE.toml for license compliance.

## Pull Request Checklist

Please read our latest [CONTRIBUTING.md](https://github.com/royshil/obs-backgroundremoval/blob/main/CONTRIBUTING.md).

- [x] I have read the latest CONTRIBUTING.md.
- [x] I have acknowledged the licensing and patent grant policy.
- [x] I have included the required license headers.
- [x] I am confident with my code integrity.
- [x] I have signed off and verified all my commits.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a211d35662c6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.