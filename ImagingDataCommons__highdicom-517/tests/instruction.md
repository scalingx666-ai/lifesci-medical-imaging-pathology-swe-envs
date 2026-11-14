# Issue

**Title:** Split match_geometry tol parameter

## Description

Adds finer-grain control over tolerances for the `match_geometry` method, and changes to more permissive defaults. This is in response to various reports that the default tolerance is too tight for many real-world DICOM datasets (e.g. in the IDC).

Specifically the tol parameter of ``highdicom.Volume.match_geometry() is deprecated. It previously governed both the voxel spacing and the position comparisons using a very tight default of 1e-5 that often caused spurious failures with real DICOM data. It is replaced by three more specific parameters:

- ``spacing_tol`` (default 1e-3): the ratio of the two volumes’ voxel spacings must be within spacing_tol * n of the nearest integer n, so the tolerance is relative to the step size.

- ``position_tol`` (default 1e-2): the translation between the volumes must be within this fraction of a voxel of a whole number of voxels. This is also applied to the misalignment at the far end of the grid, so that small spacing differences that accumulate across a volume are detected.

- ``parallel_tol``: the tolerance used when deciding whether direction vectors are parallel.

Passing ``tol`` still works but emits a DeprecationWarning and sets both spacing_tol and position_tol to the given value. To update code, users should replace ``tol`` with the new parameters. This is documented in the release notes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `750a0682d270`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.