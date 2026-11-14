# Issue

**Title:** Release v6.3.0

## Description

- versions: CITATION.cff, package.json and the distribution manifest say 6.3.0
- tag-pinned links in the READMEs, docs/install.md and MIGRATION-v6.md point at v6.3.0
- CHANGELOG: the Unreleased section becomes 6.3.0, opening with a note on the AO2 "comparable to" suggestion in earlier versions and what to re-check

Release content: #709 (review probes for diagnostic-accuracy, prediction-model and DTA meta-analysis manuscripts; editor block; probe statement fixes).

Checks run locally: `check_version_consistency.py`, `check_release_cadence.py --strict`, `gen_distribution_manifest.py --check`, `gen_skills_catalog_json.py --check`, `gen_detectors_catalog_json.py --check`, `validate_catalog_consistency.py`, and the full pre-commit validation.

Blind review: 1 round, no findings.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01RhVYtV27NhWBBoTQCURKgD

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4e7b3d08e0d1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.