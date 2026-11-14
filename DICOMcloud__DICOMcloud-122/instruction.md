# Issue

**Title:** [STOW] Fix the issue when StatusMessage exceeds the max length of ReasonPhrase

## Description

Fix #121 
When there are too many duplicated DICOM files in the POST, DICOMcloud will write exceptions repeatedly in `storeResult.StatusMessage`, such as:
```
SOP Instance already exists;SOP Instance already exists;SOP Instance already exists;SOP Instance already exists;SOP Instance already exists;SOP Instance already exists;SOP Instance already exists;SOP Instance already exists;SOP Instance already exists;...(and more)...
```
Which will exceed the max length (512) of `HttpResponseMessage.ReasonPhrase`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e7b32a98567d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.