# Issue

**Title:** fix(core): record a frame delivery before the volume load events

## Description

### Context

On the OHIF viewer, the MPR views show the red "Low Fidelity" label after the volume load ends. The label is incorrect, because each frame of the volume is at full resolution. While the load runs, the label shows "Transient Low Fidelity" at "99% of data arrived".

`BaseStreamingImageVolume.updateTextureAndTriggerEvents` did these steps in this order for the last frame:

1. It fired `IMAGE_VOLUME_MODIFIED`.
2. `callLoadStatusCallback` fired `IMAGE_VOLUME_LOADING_COMPLETED`. On this event, `BaseVolumeViewport` calculated the fidelity state at once, and cached the quality record of the volume.
3. It called `recordFrameDelivery`, which raised the last frame from `ADJACENT_REPLICATE` to `FULL_RESOLUTION`.

Thus the cached record kept `lowest: 3` (`ADJACENT_REPLICATE`) with `missing: 0`, and no later event cleared the cache. A test in the browser showed the cause: the delivery record of the volume held each frame at quality 8, but `getFidelityState()` gave `lowest: 3`. After a manual clear of `viewport._fidelityRecords`, the state changed to `done`.

### Changes and results

- `updateTextureAndTriggerEvents` now calls `markFrameTexturesDirty` and `recordFrameDelivery` before it fires the events. Each listener now reads a record that includes the frame.
- A new test in `streamingVolumeDeliveries.jest.js` reads the record in a listener of `IMAGE_VOLUME_LOADING_COMPLETED`. The test fails without the fix (received 3, expected 8), and passes with the fix.

### Testing

- `npx jest packages/core/test/streamingVolumeDeliveries.jest.js packages/core/test/imageVolumeFrameMarks.jest.js packages/core/test/genericVolumeFidelityEvents.jest.js packages/core/test/renderingEngineFidelityNotify.jest.js`: 26 tests pass.
- OHIF/Viewers#6424 builds the OHIF deploy preview with this branch. On the preview, open a CT study in MPR, and wait until the load ends. No viewport must show "Low Fidelity".

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
  * Corrected image streaming completion reports so they reflect the quality of the delivered frames, including when a nearby frame was previously delivered at lower quality.
  * Updated textures before loading events are emitted, helping ensure displayed images are current when those events occur.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c0fb73095512`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.