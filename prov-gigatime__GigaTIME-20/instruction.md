# Issue

**Title:** Add TCGA whole-slide inference tutorial (GigaTIME-Flash) to main

## Description

Re-targets the TCGA tutorial to main. PR #19 was accidentally merged into the GigaTIME-Flash branch instead of main, so these changes never landed on main.

Adds scripts/gigatime_flash_tcga_wsi_inference.ipynb (native-512 tiling, GigaTIME-Flash/GigaTIME per-tile inference, slide-level stitched virtual mIF across all channels) plus a one-line pointer in the New: GigaTIME-Flash README section.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ef49dbbe9659`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.