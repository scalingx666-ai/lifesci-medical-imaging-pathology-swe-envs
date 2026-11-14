# Issue

**Title:** Fix attention notebook

## Description

Hi, this PR is supposed to help with #29 and #30, though I am not sure if it does not affect other parts of the code. 
The problem is that the usage of devices in the code is mixed (switched to `cpu` everywhere in this PR). 
Some missing imports are added. 

I don't think it is good to be merged as is, but if you have feedback I or someone else could improve it. 
Now it is more like a temporal solution.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b5f4844f2d8b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.