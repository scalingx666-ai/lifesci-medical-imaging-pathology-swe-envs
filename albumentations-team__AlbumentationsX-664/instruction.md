# Issue

**Title:** perf(pixel): avoid binary dithering temporaries

## Description

Reduce temporary allocations in binary Dithering. Random uint8 compares the signed sum directly and writes the 0/255 result through OpenCV. The floating path quantizes the sum directly. The threshold is the predecessor of 0.5 in the input dtype, preserving the old inclusive comparison. Ordered uint8 writes the comparison result with a uint8 multiplication instead of an integer intermediate and cast.

### Compose timings

One CPU thread, Python 3.11, NumPy 2.4.6, OpenCV 5.0.0.93, Albucore 0.3.9. RGB 224×224, median µs/image. Random includes noise sampling. The baseline is AX `b0664b3`.

| Binary Dithering | Mac M4 Max | Linux |
| --- | ---: | ---: |
| Random uint8 | 852.9 → 781.1 (−8.4%) | 599.2 → 587.9 (−1.9%) |
| Random float32 | 945.8 → 849.2 (−10.2%) | 698.8 → 680.2 (−2.7%) |
| Ordered uint8 | 290.1 → 204.8 (−29.4%) | 444.9 → 356.0 (−20.0%) |

The random run used AMD EPYC 9V74 and the ordered run used AMD EPYC 7763. The tables cover 32–1024 pixel square inputs. The Linux random float32 64×64 Compose cell rose by 0.8% and the 1024×1024 cell was flat. [Random A/B](https://github.com/albumentations-team/AlbumentationsX/actions/runs/43552175568), [Ordered A/B](https://github.com/albumentations-team/AlbumentationsX/actions/runs/43552332877)

### Verification

Random outputs matched bitwise at five invocation seeds on each host. Direct checks cover negative strides, exact ties at 0.5 and 128, adjacent representable values, NaN, infinities, and int16 wraparound. Ordered outputs matched bitwise for six grayscale and RGB sizes and through Compose. All 56 Dithering tests, changed-file hooks, and the repository guidance check passed locally.

## Summary by Sourcery

Optimize binary dithering while preserving bitwise-equivalent output across supported input types and edge cases.

Bug Fixes:
- Preserve binary dithering results at threshold ties and across edge cases including special floating-point values, negative strides, and integer overflow scenarios.

Enhancements:
- Improve binary dithering performance by reducing temporary allocations and using optimized comparison and multiplication paths for random and ordered uint8 and floating-point inputs.

Tests:
- Add coverage for threshold preservation, uint8 noise behavior, and ordered dithering across grayscale and RGB inputs.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
  * Binary dithering can process supported images more efficiently.
  * Random dithering preserves expected threshold behavior for boundary values and non-finite noise, and leaves the input noise unchanged.
  * Binary random and ordered dithering continue to produce consistent results across supported image formats and channel counts.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1668e051a0a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.