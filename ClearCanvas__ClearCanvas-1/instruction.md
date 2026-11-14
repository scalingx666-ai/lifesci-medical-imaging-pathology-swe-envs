# Issue

**Title:** Initial set up of file for interoperability

## Description

for hg-git interopation. .gitignore created to ignore
Mercurial subrepository ReferencedAssemblies, and
.gitattributes created to suppress any newline
normalization as I suspect that this would break
interoperation. README.md also updated with the most
basic build instructions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `895f36fe7832`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.