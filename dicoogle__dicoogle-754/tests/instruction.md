# Issue

**Title:** Update access control requirements for deprecated Web endpoints

## Description

### Summary

- require admin user to access `/indexer` and `/settings`

### Open concerns

- Whether to also tighten access control for the legacy endpoints (`/legacy/*`). They are implemented in Restlet, and one of the services includes force-indexing. Restraining specific services within the legacy restlet app could be more complex, so if anything I could just restrain access control to all of them.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1ed8c3ad1a6c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.