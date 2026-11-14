# Issue

**Title:** fix(dicom): fix FrameAnatomySequence nesting

## Description

Fix tags marked as missing/unexpected by [dicom-validator](https://github.com/pydicom/dicom-validator), e.g.:

```  
Module "Frame Anatomy":
  (5200,9229) (Shared Functional Groups Sequence) / (0020,9071) (Frame Anatomy Sequence):
    Tag (0008,0100) (Code Value) is unexpected
    Tag (0008,0102) (Coding Scheme Designator) is unexpected
    Tag (0008,0104) (Code Meaning) is unexpected
    Tag (0008,2218) (Anatomic Region Sequence) is missing
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0227e235e3ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.