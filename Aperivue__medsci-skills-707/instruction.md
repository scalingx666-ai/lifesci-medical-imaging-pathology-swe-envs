# Issue

**Title:** Release v6.2.0

## Description

## Summary

Release v6.2.0: 28 commits since v6.1.0 (#678–#706).

- Versions: `CITATION.cff` (and `date-released`), `package.json` and the distribution manifest say 6.2.0.
- Tag-pinned links in the three READMEs, `docs/install.md` and `MIGRATION-v6.md` point at v6.2.0. Historical mentions of 6.1.0 (the wait removed in 6.1.0) are unchanged.
- CHANGELOG: `[Unreleased]` becomes `[6.2.0] - 2026-11-01`, opening with a note on the two `/deidentify` defects that 6.1.0 shipped (an ID-shaped source value written out as a replacement, #704; a repeated column name dropping the earlier column, #701) and what to re-run.

User-facing changes in this release include `/deidentify --mapping-in` and the Spanish locale pack, the `render_pandoc.sh` journal-abbreviation warning and the `fill_journal_abbrev.py` fixes, new CSLs (JMIR, MIM), journal profiles (JAMA Surgery, JAMIA) and figure exemplars (funnel, raincloud).

## Checks

- `check_release_cadence.py --strict`: "Release pending: 6.2.0 (last: v6.1.0, 28 day(s) ago) — OK".
- `gen_distribution_manifest.py --check`, `gen_skill_docs.py --check`, `validate_catalog_consistency.py`: pass.

After merge: tag `v6.2.0` on the merge commit, approve the `release` environment, then verify the GitHub Release (2 ZIPs), npm `latest`, the `release-verification-v6.2.0` report and Zenodo.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01VFFx8HMrY9Pb6KGwrgvyPd

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `90fd12bef031`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.