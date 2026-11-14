# Issue

**Title:** Streamline setup

## Description

Thank you for open-sourcing this model, and for the good paper. This PR:

- Streamlines the dependency install flow by merging two steps into one, using `pip`'s documented [requirements file options](https://pip.pypa.io/en/stable/reference/requirements-file-format/#supported-options)
- Adds to and clarifies the fine-tuning instructions, to make the language and objective more clear
- Fixes a couple typos

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ef069f94a90e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.