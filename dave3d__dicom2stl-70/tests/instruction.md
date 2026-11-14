# Issue

**Title:** Fix --anisotropic being ignored after other filter options

## Description

## Problem

`--anisotropic` is silently ignored if another filter option has already populated `args.filters`. For example:

```sh
dicom2stl --disable shrink --anisotropic -i 128 -o surface.stl volume.nrrd
```

On main this runs without the `Anisotropic Smoothing` stage, despite explicitly requesting it. The same happens after `--largest`, `--enable median`, or `--disable anisotropic`.

## Change

Append the requested filter to the existing ordered list, matching the other filter actions. Add parser regression cases, including the standalone flag.

## Validation

- New regression test: four subcases fail on the installed main baseline; all pass with the fix.
- Installed CLI, entirely synthetic 16³ volume: the command above skips smoothing on main and executes it with the fix; STL readback has finite geometry and nonzero triangles (76 before, 75 after).
- `python -m unittest discover -s tests`: 16 tests pass.
- CI fatal flake8 selection passes; new test passes flake8; repository advisory lint remains warning-only.
- Local platform: Windows, Python 3.13. Linux/macOS CI not run locally. No patient data, clinical validation, or GUI acceptance testing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e01d05e75974`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.