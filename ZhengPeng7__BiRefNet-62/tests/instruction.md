# Issue

**Title:** fix issue run_sh_file when empty

## Description

i want to run only inference , but when i call

from models.birefnet import BiRefNet

got error in config.py , 
```with open(run_sh_file[0], 'r') as f:
IndexError: list index out of range```

add fix for that issue

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24b8dadfee14`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.