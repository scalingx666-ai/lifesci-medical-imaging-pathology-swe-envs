# Issue

**Title:** chore(release): bump version to 2.6.3

## Description

Prepare AlbumentationsX 2.6.3 with the CPU performance changes already on main. Archive the 2.6.2 behavior notes and record the upgrade requirements for this release.

- Upgrade replay consumers before sending them new sparse `SaltAndPepper` records. This release continues to accept the older mask-based records.
- CPU conversion copies read-only NumPy buffers before wrapping them as tensors.

Local validation passed 2,418 focused tests, regression vector verification, pre-commit hooks, and wheel and sdist metadata and license checks. The required release preflight will build and verify the publishable bundle.

## Summary by Sourcery

Prepare the 2.6.3 release with replay compatibility and safer CPU tensor conversion changes.

Bug Fixes:
- Ensure CPU NumPy-to-tensor conversion safely handles read-only buffers without relying on writable storage aliasing.

Enhancements:
- Record sparse SaltAndPepper replay payload behavior while retaining compatibility with existing mask-based records.
- Archive the 2.6.2 behavior changes and reset the unreleased behavior inventory for the next release.

Build:
- Bump the package version to 2.6.3 and update the lockfile metadata.

Documentation:
- Add the 2.6.2 behavior change notes covering vector fields, geometry handling, and reduced-precision CUDA normalization.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
  * Added a 2.6.2 behavior-change inventory covering vector-field targets, validation, supported geometry and transform limitations, and eligible CUDA reduced-precision normalization behavior.
  * Updated unreleased notes to use the 2.6.2 baseline and document sparse SaltAndPepper replay payloads and read-only NumPy-to-Tensor storage behavior. Validation, Geometry, and Deprecations are marked as having no current notes.
* **Chores**
  * Updated the project version to 2.6.3.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2b760dfdac47`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.