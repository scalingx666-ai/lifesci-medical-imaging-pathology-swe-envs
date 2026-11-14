# Issue

**Title:** Add IBSI2 GUI, fix compatibility with CaPTk

## Description

Adds the GUI elements from IBSI2. 
Also changes the IBSI2 function to create output subdirectories to hold the image outputs from the IBSI-2 executable, so that they don't overwrite.
Also tells users that more output will be generated.

~~Having tested the IBSI2 features triggered in this way, I can't get the process to complete (seems to hang up on Gabor filters and never complete after a few hours on my machine). However, the extrafeatures executable is getting invoked properly.~~

This is working now. Binaries have been replaced on NITRC.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `321a8b9853b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.