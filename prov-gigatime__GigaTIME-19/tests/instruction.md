# Issue

**Title:** Add TCGA whole-slide inference tutorial for GigaTIME-Flash

## Description

Smaller follow-up to the GigaTIME-Flash PR. Adds `scripts/gigatime_flash_tcga_wsi_inference.ipynb`, which tiles a TCGA slide at native 512 resolution, runs GigaTIME-Flash (or the original GigaTIME) per tile, and stitches the predictions into a slide-level virtual mIF map across all 23 channels. Also adds a one-line pointer in the New: GigaTIME-Flash README section.

Note: stacked on top of the GigaTIME-Flash branch; GitHub will retarget this PR to main once that PR merges.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ab4d06a10536`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.