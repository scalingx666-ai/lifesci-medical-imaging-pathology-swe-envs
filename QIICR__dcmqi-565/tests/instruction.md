# Issue

**Title:** Use DCMTK for all CIELab/RGB color conversions.

## Description

This changes the colors, not only the precision. DICOM stores the Recommended Display CIELab Value in the same way as the ICC Profile Connection Space, so the values are relative to the D50 illuminant. Both old implementations (dcmqi's ColorUtilities and DCMTK up to commit 88105877c from September 2026) computed CIELab relative to D65 instead. DCMTK now converts sRGB -> XYZ (D65)-> Bradford adaptation to D50 -> CIELab. It uses the matrices from the CSS Color Module Level 4 sample code (taken over from PixelMed code).

Effect on existing files: SEG objects written by older versions contain D65-based CIELab values. When this version reads them, the RGB values in the JSON metadata differ a little for colored segments. The largest change is for pure blue. Gray values do not change. Files written by this version are read back exactly (the 8-bit round trip is exact for all 16.7 million RGB values).

Other fixes included: results outside the sRGB range are now clamped (before, they wrapped around in unsigned), results are rounded instead of truncated, and the integer division bug in the old inverse f function (black was read back as 36,36,36) is gone together with the old code.

This PR updates DCMTK to 4e89d4f (including mentioned 88105877c), whose IODCIELabUtil now computes CIELab relative to the ICC PCS white point (D50) like PixelMed (), and drop dcmqi's own ColorUtilities, which used D65.

- Convert Recommended Display RGB/CIELab values via IODCIELabUtil
- Derive the fallback CIELab value from the default RGB 128,174,128
- Encode background black as 0/32896/32896 (a*=b*=0), not 32768
- Round palette LUT entries instead of truncating them
- Remove the Java reference implementation of the old conversion.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5571494a1441`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.