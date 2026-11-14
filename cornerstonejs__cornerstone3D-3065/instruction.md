# Issue

**Title:** fix(planar): correct CPU image coordinates on high-DPI displays and stop the labelmap render loop at mount

## Description

### Context

This fixes two problems on the CPU image path (`cpuImage`) of a `PLANAR_NEXT` viewport.

#### 1. Wrong canvas coordinates when devicePixelRatio is not 1

On a display with `devicePixelRatio` other than 1, `canvasToWorld` and `worldToCanvas` return wrong points. At DPR 2, `canvasToWorld([100, 120])` returns the world point that is drawn at CSS `[200, 240]`. The image itself draws correctly. Everything that uses the world point is off: zoom anchors on the wrong point and a brush stroke lands away from the cursor. Annotations still draw under the cursor because both directions carry the same error.

Two parts of the viewport disagree about the size of the CPU canvas:

- `PlanarViewport.resize()` sizes the CPU canvas in device pixels. `getCanvasCssDimensions` divides the canvas size by `devicePixelRatio` to get CSS pixels.
- `CpuImageSliceRenderPath` called the legacy `cpuFallback/rendering/resize` helper in `addData` and in `resize`. That helper refits the image, but it also resets `canvas.width` and `canvas.height` to the CSS size.

So the transforms worked with a canvas `1 / devicePixelRatio` of its real size. At DPR 1 the two sizes are equal, which is why no test saw it. Every Playwright project and the vitest browser config pin `deviceScaleFactor: 1`.

This is not a recent regression. v5.0.0 has the same error at DPR 2.

#### 2. Maximum call stack size exceeded when a labelmap mounts

With a labelmap on the same path, the console shows `RangeError: Maximum call stack size exceeded` twice at the initial mount. It happens at any `devicePixelRatio` and with one labelmap layer. The stack repeats this cycle:

```
_imageChangeEventListener        (IMAGE_RENDERED)
syncStackLabelmapActors          -> viewport.render()
CpuImageSliceRenderPath.render   -> triggerEvent(IMAGE_RENDERED)
_imageChangeEventListener        ...
```

The listener handles `IMAGE_RENDERED` once, for the initial image. It removed itself only after `syncStackLabelmapActors` returned. The CPU image path draws synchronously and fires `IMAGE_RENDERED` inside that call, so the listener ran again before it was removed. A GPU path draws on the next frame, so the listener was already gone by then.

### Changes & Results

- `CpuImageSliceRenderPath` now only refits the image with `fitToWindow`. The canvas size stays with `PlanarViewport.resize()`, the same as on the CPU volume path.
- The CPU image now draws at device resolution on a high-DPI display. At DPR 1 the screenshots are byte-identical before and after.
- `_imageChangeEventListener` now removes itself from `IMAGE_RENDERED` before it calls `syncStackLabelmapActors`. The two errors at mount are gone. The labelmap still draws on the first image and the brush still works.
- Two jest tests at `devicePixelRatio` 2 in `planarComputedCamera.jest.js`. Both fail without the canvas fix.
- New jest test `imageChangeEventListener.jest.js`. The test for a sync that renders synchronously fails without the listener fix.

Measured in Chrome on the CPU image path, with an axial CT in a 400x400 CSS px viewport. The click and the zoom start are at CSS `[100, 120]`.

| DPR | Build | `canvasToWorld` error | Brush stroke offset from the click | Drift of the point under the cursor after zoom |
| --- | --- | --- | --- | --- |
| 1 | before | 0 mm | 1.5 px | 1.0 px |
| 1.5 | before | 98 to 194 mm | 76 px | 91 px |
| 2 | before | 195 to 388 mm | 154 px | 183 px |
| 1, 1.5, 2 and 3 | after | 0 mm | 1.1 to 1.5 px | 1.0 px |

The error is the same with a global CPU backend and with a per-mount `renderBackend: 'cpu'`. After a viewport resize the error stays at 0 mm with the fix. The CPU volume path (`cpuVolume`) was already correct and gives the same numbers before and after.

Not in this PR: the legacy `StackViewport` CPU path has its own coordinate problem at DPR other than 1. It needs a separate fix.

### Testing

- `npx jest packages/core/test/planarComputedCamera.jest.js packages/tools/test/imageChangeEventListener.jest.js`
- Open `genericStackManipulationTools?cpu=true` on a high-DPI display, or with Chrome device emulation at DPR 2. Zoom with the right button and check that the point under the cursor stays there.
- Open `genericStackLabelmapSegmentation?cpu=true` and check the console at load.
- I also ran the vitest browser suite with `deviceScaleFactor: 2`. `renderPathParity` (cpuImage against the vtkImage baseline) and `viewStateSerialization` (vtkImage to cpuImage restore) fail before the canvas fix and pass after. No test goes from pass to fail at DPR 1 or DPR 2.

### Checklist

#### PR

- [x] My Pull Request title is descriptive, accurate and follows the
  semantic-release format and guidelines.

#### Code

- [x] My code has been well-documented (function documentation, inline comments,
  etc.)

#### Public Documentation Updates

- [x] The documentation page has been updated as necessary for any public API
  additions or removals.

#### Tested Environment

- [x] "OS: macOS 27.2"
- [x] "Node version: 24.15.0"
- [x] "Browser: Chrome 157.0.8103.51"

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
  * Improved image resizing on high-DPI displays, preserving canvas dimensions and keeping image coordinates aligned with displayed content.
  * Prevented duplicate labelmap synchronization when image rendering triggers another render event.

* **Tests**
  * Added coverage for high-DPI image resizing, coordinate mapping, and labelmap synchronization.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c0fb73095512`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.