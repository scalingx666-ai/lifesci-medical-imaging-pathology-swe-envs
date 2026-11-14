# Issue

**Title:** fix(segmentation): keep the slice-rendered labelmap on rotated and oblique planar views

## Description

### Context

On a `PLANAR_NEXT` viewport a labelmap with `useSliceRendering` disappears when the view leaves the voxel grid of the labelmap. A 30 degree in-plane rotation does it. An oblique orientation does it too. The labelmap comes back when the view is aligned again and the segmentation data is not touched.

The slice path copies one slice of voxels along the axes of the volume. `getSliceState` only finds that slice when the right, up and normal directions of the view each match a volume axis. The legacy `VolumeViewport` leaves the slice path for an oblique view, because `canRenderVolumeViewportLabelmapAsImage` returns false there. The planar viewport has no such check. The slice path stays selected, no slice is found and no actor is mounted.

I think the planar viewport should keep the 2D texture here and not fall back to the volume path. The volume path needs the whole labelmap on the GPU, which is the cost that slice rendering avoids.

The CPU volume rendering already samples any plane on the CPU, in `PlanarCPUVolumeSampler`. This PR does not add a second sampler for the labelmap. It moves the sampling into one core utility that both use, and makes it faster.

### Changes & Results

Core:

- New `utilities.sampleVolumeGrid`. It samples a volume on a regular grid of points with nearest or linear lookup. A grid in a plane gives one slice image in any orientation.
- It reads the typed array of each slice directly, from the one array of the volume or from the slice view of the voxel manager (`_getSliceView`). Any other slice is read through `getAtIJK` of the voxel manager: a dynamic (4D) volume, an RLE image, a missing image or a scaled image. Both ways give the same values. A dynamic volume thus shows its current dimension group.
- Each row is split into runs of columns. The columns well inside the volume are sampled in a loop without checks. Only the few columns near the border of the volume take the checked path.
- `PlanarCPUVolumeSampler` uses it for the oblique scalar case. It keeps its own loop only for color volumes. The border, tie, limit and rounding rules are the same as before, so the CPU image does not change.

Tools:

- New `volumeLabelmapResampledSliceData.ts`. It only works out the geometry of the slice image. The pixels come from `utilities.sampleVolumeGrid` and the pixel size from `utilities.getEffectiveSpacingAlongDirection`.
- A view rotated in its own plane still gets an exact copy of one slice of voxels. The image is placed in world coordinates, so the rotated camera draws it.
- The exact copy is used only when the view normal follows a volume axis within rounding error. A view with a small tilt is sampled on its own plane. The 0.999 alignment tolerance of the aligned copy accepts tilts up to 2.5 degrees, and at 2 degrees that copy lies up to 8.7 mm off the view plane.
- The slice geometry uses double precision. `vec3.create()` holds single precision, which is too coarse for world positions.
- An oblique view takes the nearest voxel for each pixel of the view plane. The image covers the part of the plane that cuts the volume. Its pixel size is close to the voxel size, with a limit of 2048 pixels per side.
- Each row of the slice image is the line where the view plane meets one slice of the volume. A row is read from one slice image, which keeps the reads close together in memory. The image does not change when an oblique view rotates in its own plane.
- `getVolumeLabelmapImageMapperRepresentationUIDs` keeps the planar UID for an off-axis view, so the actor stays mounted.
- On a planar viewport, the render key of the labelmap does not hold `viewUp`. The slice image is in world coordinates, so a turn of the view in its own plane does not resample the slice. The legacy `VolumeViewport` key keeps `viewUp`.
- The slice functions take the camera as an argument, so one update reads the camera one time.
- Only the planar viewport changes. The legacy `VolumeViewport` path is the same.

Sagittal viewport of `genericLabelmapSliceRendering` on 5.17.1:

| View | Before | After |
| --- | --- | --- |
| Aligned | 512 x 135 image | 512 x 135 image |
| Rotated 30 degrees in its plane | no labelmap actor | 512 x 135 image, exact copy |
| Tilted 2 degrees | 512 x 135 copy of one voxel slice, up to 8.7 mm off the view plane | 513 x 135 image, resampled on the view plane |
| Oblique, normal `[0.906, 0.423, 0]` | no labelmap actor | 566 x 135 image, resampled |

The GPU cost stays one small 2D texture for each layer. For a 512 x 512 x 135 labelmap the oblique slice is 0.07 MiB. The volume texture would be 33.75 MiB for each layer.

#### Sampling speed

Chrome 157 on an Apple M2 Ultra. Volumes of 512 x 512 x 135, one oblique plane, median time in ms. The old loop is a copy of the per-voxel loop that the CPU sampler ran before this PR. Both give the same pixels in every row of the table.

| Case | Output | Old per-voxel loop | `sampleVolumeGrid` | Faster by |
| --- | --- | --- | --- | --- |
| CT, nearest | 512 x 512 | 16.3 | 2.1 | 7.8x |
| CT, nearest | 1024 x 1024 | 58.0 | 8.0 | 7.3x |
| CT, nearest | 2048 x 2048 | 220.9 | 31.8 | 6.9x |
| CT, linear | 512 x 512 | 46.9 | 3.0 | 15.6x |
| CT, linear | 1024 x 1024 | 177.3 | 11.6 | 15.3x |
| CT, linear | 2048 x 2048 | 707.8 | 46.2 | 15.3x |
| Labelmap, nearest | 512 x 512 | 12.6 | 2.1 | 6.0x |
| Labelmap, nearest | 1024 x 1024 | 49.5 | 5.0 | 9.9x |
| Labelmap, nearest | 2048 x 2048 | 197.2 | 19.8 | 10.0x |

In the pipeline the labelmap slice is much smaller than these outputs. The oblique slice of the demo, 565 x 136 when I measured it, takes 0.4 to 0.8 ms for each layer. The 512 x 135 copy of a rotated view takes 1.0 ms.

A loop written only for the labelmap case is still about 1.3 times faster at 1024 x 1024, 4.0 ms against 5.0 ms. I kept the one shared sampler.

#### Checks

- CPU volume path: I hashed the CPU canvas of two oblique views of `genericPetRenderBackendGrid` with linear and with nearest sampling. The four hashes are the same before and after.
- Labelmap slice path: I compared every pixel of the mounted slice image with a separate nearest-voxel lookup, on a labelmap with two layers. Aligned, rotated 30 degrees, tilted 25 degrees, and tilted 25 degrees plus rotated 40 degrees: 0 pixels differ and every pixel lies on the view plane.
- Tilted 1 and 2 degrees: 0 pixels differ and the image lies on the view plane. Before the review fix the copy differed from the view plane in up to 192 pixels of this test labelmap.
- Scroll while tilted: the slice follows the new plane and 0 pixels differ.
- Sphere brush while tilted: the segment grew from 267,768 to 309,108 voxels and the slice was redrawn with 0 pixels differing.

Things this does not cover:

- A view with a slab still uses the volume path, as before.
- Color volumes on the CPU path still use the old per-voxel loop.
- On the exact border between two voxels the sampler uses the tie rule that the CPU path already had.

### Testing

- Run `pnpm run example genericLabelmapSliceRendering` and use the console:

```js
const viewport = cornerstone
  .getRenderingEngine('myRenderingEngine')
  .getViewport('CT_SAGITTAL');

viewport.setViewState({ rotation: 30 });
viewport.render();
```

The labelmap stays on the sagittal view. Then make the view oblique:

```js
viewport.setViewState({ rotation: 0 });
viewport.setOrientation({
  viewPlaneNormal: [0.906, 0.423, 0],
  viewUp: [0, 0, 1],
});
viewport.render();
```

- For the CPU path run `pnpm run example genericPetRenderBackendGrid` and set the same oblique orientation on the `PET_SAGITTAL_CPU` viewport.
- For a dynamic volume on the CPU path run `pnpm run example genericDynamicVolume` with `?cpu=true`, set an oblique orientation on the `PT_4D_VOLUME_GENERIC` viewport, and move the "Dimension Group Number" slider. The oblique image changes with the group.
- Unit tests in `packages/core`: `npx jest test/sampleVolumeGrid.jest.js test/planarCpuVolumeRenderPath.jest.js`.
  - New `sampleVolumeGrid.jest.js` with 19 tests. It compares the sampler with the old per-voxel sampling on 2,600 random grids, for nearest and linear lookup and for four ways to reach the voxels.
  - The 19 existing tests of the CPU volume render path pass unchanged.
- Unit tests in `packages/tools`: `npx jest src/tools/displayTools/Labelmap`.
  - New `volumeLabelmapResampledSliceData.spec.ts` with 22 tests. They run against the real `sampleVolumeGrid` and cover the three slice axes, a volume that is turned and shifted in the world, a small tilt, a volume far from the world origin, the size limit and a plane that misses the volume. The ways to read the voxels are tested in core only.
  - 7 new tests in `volumeLabelmapImageMapper.spec.ts` for the planar wiring. Three of the tests in that file fail without the change.
  - 1 new test in `labelmapImageMapperSupport.spec.ts`: the planar key does not change when the view turns in its own plane.
  - The 15 spec files under `displayTools`, `eventListeners/segmentation` and `stateManagement/segmentation` pass, 148 tests in total.
  - Not covered yet: a test of a dynamic (4D) volume through `sampleVolumeGrid`.

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
- [x] "Browser: Chrome 157"

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
  * Labelmap overlays now support planar views with aligned, rotated, and oblique slices, extending display support across viewport orientations.
  * Volume data can be sampled on a regular grid using nearest-neighbor or linear interpolation, with configurable handling for values outside volume bounds.
* **Improvements**
  * Planar labelmap slices use available slice data and fall back to an indexed slice when needed.
  * In-plane rotations preserve planar labelmap mapper state, keeping overlays consistent as the view turns.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34c5aad882d7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.