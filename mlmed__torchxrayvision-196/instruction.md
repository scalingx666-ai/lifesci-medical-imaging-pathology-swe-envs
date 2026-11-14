# Issue

**Title:** Document official PhysioNet VinDr-CXR files in VinDr_Dataset docstring

## Description

Docs-only change to the `VinDr_Dataset` docstring.

## What

- Notes that the bundled default CSV (`vinbigdata-train.csv.gz`) is the Kaggle challenge training set: 15,000 images, each read independently by 3 radiologists.
- Explains that the official PhysioNet release (https://physionet.org/content/vindr-cxr/1.0.0/, credentialed access) also includes a 3,000-image test set labelled by the consensus of 5 radiologists, and how to load it: point `csvpath` at `annotations/annotations_train.csv` or `annotations/annotations_test.csv` and `imgpath` at the matching `train` or `test` folder. Only the classes the loader already lists are read; the extra local labels in those files (e.g. Rib fracture, Emphysema) are ignored.
- Adds the PhysioNet link alongside the Kaggle challenge link.
- Fixes the source hospitals: the data came from Hanoi Medical University Hospital and Hospital 108 (per the paper and the PhysioNet page), not Bach Mai Hospital.

The PhysioNet files are not bundled, since they are covered by the PhysioNet Credentialed Health Data Use Agreement.

## Checked

With the current loader, `VinDr_Dataset(imgpath=..., csvpath=<official annotations CSV>)` loads 15,000 images from `annotations_train.csv` and 3,000 from `annotations_test.csv`, and the PhysioNet folder layout (`train/<id>.dicom`, `test/<id>.dicom`) matches what `__getitem__` expects.

Independent of #195 (no overlapping lines; they merge cleanly in either order).

Made with [Cursor](https://cursor.com)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bd41a6ce24c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.