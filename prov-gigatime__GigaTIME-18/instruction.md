# Issue

**Title:** Add GigaTIME-Flash inference tutorial and README section

## Description

Adds an inference-only tutorial (`scripts/gigatime_flash_testing.ipynb`) that loads GigaTIME-Flash from HuggingFace (`prov-gigatime/GigaTIME-flash`) and runs tiled H&E->mIF inference with colorized per-channel visualization, plus a README section linking the new model card.

GigaTIME-Flash is 6x faster, uses 8x less GPU memory, and improves prediction quality over the original CNN-based GigaTIME.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3bc2d882d1d4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.