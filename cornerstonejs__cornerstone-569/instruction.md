# Issue

**Title:** fix(circleci): update circleci/node image

## Description

- Update config.yml to use older circleci/node sha after recent changes to latest-browsers tag
- Image tag that has been used was updated 2 days ago and broke all builds: https://hub.docker.com/layers/circleci/node/latest-browsers/images/sha256-1f63129b912afbe0a47c1d37878ed638714dae3f32abdc4d35c532299bd0e136?context=explore

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2bca56dcfeed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.