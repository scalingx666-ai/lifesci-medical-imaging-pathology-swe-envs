# Issue

**Title:** [BraTSPipeline] Move brain-masked image write to Skull Stripping instead of Brain Tumor step

## Description

Simply moves the step of writing out the brain-masked images up slightly, to the end of the Skull Stripping step instead of the beginning of the Brain Tumor step. 

(ignore my branch name, i used the wrong branch for this but it doesn't matter)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `716ef7f844bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.