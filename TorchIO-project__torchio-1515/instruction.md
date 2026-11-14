# Issue

**Title:** Lock CI dependencies with uv

## Description

**Description**

Prevent CI failures caused by unplanned formatter, linter, and type-checker releases.

- **Reproducible CI**
  - Commit `uv.lock` and require locked dependency resolution.
  - Run tox environments through `uv-venv-lock-runner`.
  - Move CI tools into dependency groups tracked by the lockfile.
- **Managed updates**
  - Configure Dependabot to update uv and GitHub Actions dependencies monthly in one grouped pull request.

**Checklist**

- [ ] I have read the [`CONTRIBUTING`](https://github.com/TorchIO-project/torchio/blob/main/CONTRIBUTING.md) docs and have a developer setup ready
- Changes are
  - [x] Non-breaking (would not break existing functionality)
  - [ ] Breaking (would cause existing functionality to change)
- [ ] Tests added or modified to cover the changes
- [ ] In-line docstrings updated
- [ ] Documentation updated
- [x] This pull request is ready to be reviewed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ced7e41bf796`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.