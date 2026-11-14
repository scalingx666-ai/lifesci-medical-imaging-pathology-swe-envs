# Issue

**Title:** Fix: Resolve dependency version conflict in Colab notebooks

## Description

# Description
After the Codalab update on April 9th, 2025, users reported dependency conflicts when running our demo notebooks in Google Colab:

```python
ERROR: pip's dependency resolver does not currently take into account all the packages that are installed. This behaviour is the source of the following dependency conflicts.
thinc 8.3.6 requires numpy<3.0.0,>=2.0.0, but you have numpy 1.26.4 which is incompatible.
```

The error was caused by MONAI's dependencies. This PR modifies setup.py to loosen MONAI's dependency specification. Both inference and training now run smoothly in Colab notebooks with this change.

# Issues this PR resolves
* #385
* #389

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b9db486e77bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.