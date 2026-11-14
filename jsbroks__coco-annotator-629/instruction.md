# Issue

**Title:** Fix rabbitmq version

## Description

While the theoretical message size limit in RabbitMQ is 2GB up to 3.7.0, which 128MB is also the new max size limit in 3.8.0 and onward.
you can't upload coco json file larger than 128M in newer version.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `766818fe5caa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.