# Issue

**Title:** Fix the case that labels are all ignored

## Description

An error occurred in line 177 ( `C = probas.size(1)` ) when input labels are all ignored, because labels got empty.
This PR deal with such problems.

One thing I concerned about is the difference between the lines I added and below lines
```
        if len(labels) == 0:
            # only void pixels, the gradients should be 0
            return logits.sum() * 0.
```

Above is a part of the original implementation of lovasz_flat. This doesn't exclude void labels for calculation the loss. Is it excepted behavior?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bd7e01717369`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.