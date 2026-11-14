# Issue

**Title:** feat(cornerstone): the Ultrasound Directional tool measures an ECG in seconds and mV

## Description

﻿## Context

The Ultrasound Directional tool shows only `px` on an ECG viewport. The tool needs a calibration region in seconds and mV. Two problems stop that region:

- OHIF does not turn on the typed metadata providers of `@cornerstonejs/metadata`. The ECG SOP class handler builds the ECG module and stores it with `genericMetadataProvider.addRaw`. No code stores the ECG calibration in the same way.
- The OHIF `MetadataProvider` returns `{ sequenceOfUltrasoundRegions: undefined }` for every instance with no regions. This object stops the provider chain, so a later provider cannot give a calibration.

## Changes & Results

- `getSopClassHandlerModule.js`: the ECG SOP class handler gets the calibration from `buildEcgCalibrationFromInstance` and stores it with `genericMetadataProvider.addRaw`.
- `MetadataProvider.ts`: the `calibrationModule` case returns nothing when the instance has no `SequenceOfUltrasoundRegions`. An ultrasound instance with regions gets the same result as before.
- `toolbarButtonsCustomization.ts`: the Ultrasound Directional button is enabled for the `ECG` modality.
- `package.json` files and `pnpm-lock.yaml`: the `@cornerstonejs/*` dependencies change from 5.12.0 to 5.16.0.

Result: on an ECG, the Ultrasound Directional tool shows seconds for a horizontal measurement and mV for a vertical measurement. The Length tool and the other tools continue to show `px` on an ECG, because the two axes have different units.

## Dependencies

- Cornerstone3D [v5.16.0](https://github.com/cornerstonejs/cornerstone3D/releases/tag/v5.16.0) has the ECG Generic Viewport and `buildEcgCalibrationFromInstance`. The release contains Cornerstone3D PR , and the merge commit is `31c64766`.
- npm: [`@cornerstonejs/core@5.16.0`](https://www.npmjs.com/package/@cornerstonejs/core/v/5.16.0), [`@cornerstonejs/metadata@5.16.0`](https://www.npmjs.com/package/@cornerstonejs/metadata/v/5.16.0), [`@cornerstonejs/tools@5.16.0`](https://www.npmjs.com/package/@cornerstonejs/tools/v/5.16.0).
- This PR updates all `@cornerstonejs/*` dependencies to 5.16.0, so the ECG handler always gets a calibration.

## Testing

1. Run `pnpm install`. If you use a linked Cornerstone3D checkout, use `v5.16.0` or later.
2. Open a study with a 12-lead ECG in the basic viewer.
3. In "More tools", select "Ultrasound Directional".
4. Draw a horizontal measurement on a lead. The tool shows a value in `seconds`.
5. Draw a vertical measurement. The tool shows a value in `mV`.
6. Open an ultrasound study with regions. The Ultrasound Directional tool gives the same values as before.

## Checklist

- [x] The PR has a short title in the Conventional Commits format.
- [ ] The author ran the steps of "Testing" in a browser. The author did not run them.
- [ ] Unit tests: no test covers `calibrationModule` in OHIF. This PR adds no test.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
  * The ultrasound directional tool is available when viewing ECG studies as well as ultrasound studies.
  * ECG images can use available calibration information for more accurate display.
* **Bug Fixes**
  * Calibration information is omitted when required ultrasound region data is missing, preventing incomplete metadata from being used for display. When that data is available, existing calibration metadata continues to be provided.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b2ef6ffc18f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.