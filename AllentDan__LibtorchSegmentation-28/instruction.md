# Issue

**Title:** LibTorchSegmentation static lib

## Description

First of all, tanks for share your awesome job!

For learn and study purposes I have been playing with this library. 
In order to increase the build speed I have splitted the project in two parts,  one is a core static library and the second is a test-demo project. CMake will install the core lib in the /usr/local/lib in order to avoid compile the whole project for every change in the test-demo project.

Due to I will keep exploring the wonderful possibilities of this project , I would like to keep the original repository as reference.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `69ce3ac4b81c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.