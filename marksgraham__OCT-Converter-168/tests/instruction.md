# Issue

**Title:** Feat/dicom export heightmap

## Description

**Summary**
Adds heightmap segmentation to the DICOM export and includes scan geometry. Due to limited example data I was able to test with E2E and FDA files. I also fixed a few bugs I encountered along the way.

**Height Map Segmentation DICOM**
- Write companion Height Map SEG instances from layer contours alongside OPT (and fundus).
- Shared Study / Frame of Reference UIDs so OPT and SEG stay linked.
- E2E export in create_dicom_from_oct; FDA height-map extraction added in a follow-up.
- Helpers in oct_converter/dicom/heightmap.py.

**Circular / volume scan geometry**
- Parse E2E circle vs volume geometry into scan_geometry.
- OPT: ScanPatternTypeCodeSequence and OphthalmicFrameLocationSequence (NONLINEAR circle / LINEAR volume) with ReferenceCoordinates.
- Heidelberg spacing from FOV → mm; fundus written first so OPT can reference it.
- Fallbacks when pixel/FOV values are missing.
- Helpers in oct_converter/readers/scan_geometry.py.

**Optional B-scan registration (0x271C)**
- Parse Heidelberg registration and warp B-scan pixels + contours when apply_registration=True (default False), in read_oct_volume / create_dicom_from_oct.
- New oct_converter/readers/registration.py.

**Other changes**
- Prefer current ContourSegment chunks over 0x2713 (10019), because it has leading zeros that clock circular profiles by ~5 A-scans and skew TSNIT sectors vs Heyex. Fall back to legacy when 0x2723 is absent.
- Handle E2E files that omit patient metadata (patient_id = None; DICOM patient fields coerced to "").
- More robust fundus metadata lookup; fix E2E slice compacting.
- Shared Study UID on FDA export; correct MediaStorageSOPClassUID for color fundus.
- Consistent acquisition datetime handling across DICOM writers.
- Replace deprecated numpy.fromstring.

Docs / examples
examples/demo_e2e_heightmap_seg.py, examples/demo_fda_heightmap_seg.py, and small E2E extraction demo updates.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2cff6a40c839`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.