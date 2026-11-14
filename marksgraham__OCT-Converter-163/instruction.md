# Issue

**Title:** fix(dicom): fix invalid value for VR DS

## Description

Fix tags marked with invalid values by [dicom-validator](https://github.com/pydicom/dicom-validator), e.g.:

```
Module "Plane Position (Patient)":
(5200,9230) (Per-Frame Functional Groups Sequence) / (0020,9113) (Plane Position Sequence):
  Tag (0020,0032) (Image Position (Patient)) has invalid value '0.30000000000000004' for VR DS
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a87498c03c4f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.