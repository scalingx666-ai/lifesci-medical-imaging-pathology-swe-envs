# Issue

**Title:** Group Dependabot updates and schedule quarterly version bumps

## Description

**Description**

Replace the individual-update PR noise seen in #1531–#1533 with grouped updates.

- **Version updates:** Change the existing combined GitHub Actions and uv group from monthly to quarterly.
- **Security updates:** Group fixes within each ecosystem. These remain event-driven; GitHub does not apply quarterly schedules to security updates.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5dcb1b1d8f48`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.