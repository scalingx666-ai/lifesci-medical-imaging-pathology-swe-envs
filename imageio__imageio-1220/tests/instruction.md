# Issue

**Title:** BUG: Drop Python 3.10, fix PyAV gc stall, temporarily pin pillow on pypy

## Description

- Drop Python 3.10 now that it is end of life. The minimum is 3.11, CI tests CPython 3.14, and PyPy stays on 7.3.23 until Pillow publishes `pp80` wheels.
- On close, drop PyAV's private thread-local swscale reformatter so its worker pool does not survive the container and deadlock a later fork inside `gc.collect()`.
- On close, drop the filter graph and collect it on this thread. PyAV's graph and filter contexts keep each other alive, so the destructor that joins their workers otherwise runs in a forked child and deadlocks.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8e8005462004`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.