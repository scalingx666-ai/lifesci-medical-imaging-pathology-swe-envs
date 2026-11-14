# Issue

**Title:** perf(pixel): reuse Diamond-Square work buffers

## Description

Reuse the interpolation and mask buffers within each Diamond–Square step. Apply the existing threshold, addition, multiplication, and normalization in the same order, with explicit output buffers. Keep the uniform draws and their order.

### Catalog recipes

Timed the [catalog recipes and AX CPU adapter](https://github.com/albumentations-team/benchmark/tree/ae173f2012d4cac9fc1573b2930aab820ebea60c) with RandomCrop224, the plasma transform, ToTensorV2, and collation. The JPEG rows include reading and decoding 16 generated RGB JPEGs per batch. The measurements stop at the CPU batch.

Median microseconds per image, one CPU thread per host, alternating paired measurements. Baseline AX `b0664b3`, Albucore 0.3.9, Python 3.11.15, NumPy 2.4.6, and OpenCV 5.0.0.93. [Linux run and raw CSV](https://github.com/albumentations-team/AlbumentationsX/actions/runs/43550768210)

| Workload | Mac M4 Max, µs | Linux AMD EPYC 9V74, µs |
| --- | ---: | ---: |
| R39 PlasmaContrast, decoded | 1,368.5 → 1,282.1 (-6.3%) | 1,277.6 → 1,243.1 (-2.7%) |
| R39 PlasmaContrast, JPEG | 4,093.2 → 4,059.4 (-0.8%) | 4,380.6 → 4,362.7 (-0.4%) |
| R40 PlasmaShadow, decoded | 1,344.0 → 1,244.2 (-7.4%) | 1,215.4 → 1,186.6 (-2.4%) |
| R40 PlasmaShadow, JPEG | 4,006.6 → 3,935.1 (-1.8%) | 4,365.7 → 4,338.8 (-0.6%) |

<details>
<summary>Generator timings at roughness 0.5</summary>

| Map size | Mac M4 Max, µs | Linux AMD EPYC 9V74, µs |
| --- | ---: | ---: |
| 32×32 | 71.7 → 72.5 (+1.2%) | 91.4 → 94.0 (+2.9%) |
| 128×128 | 282.6 → 258.7 (-8.5%) | 245.4 → 241.9 (-1.4%) |
| 224×224 | 831.9 → 755.7 (-9.2%) | 622.8 → 597.1 (-4.1%) |
| 256×256 | 835.7 → 764.7 (-8.5%) | 626.2 → 601.5 (-3.9%) |
| 512×512 | 2,999.2 → 2,691.3 (-10.3%) | 3,905.1 → 3,383.6 (-13.4%) |

</details>

### Correctness

Both hosts passed 270 bitwise comparisons of float32 plasma maps and identical final RNG state, across nine shapes, six roughness settings, and five seeds. Both catalog recipes matched bitwise at five seeds with and without JPEG. The regression test reproduces the earlier Diamond–Square update and checks map bits and RNG state. The 294 focused AX tests and affected pre-commit hooks passed.

## Summary by Sourcery

Improve plasma generation performance by reusing Diamond–Square work buffers without changing its results or random-number sequence.

Enhancements:
- Optimize Diamond–Square plasma generation by reusing interpolation and mask work buffers while preserving output and random-number behavior.

Tests:
- Add bitwise regression coverage for plasma maps and final RNG state across multiple shapes and roughness settings.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
  * Improved the efficiency of illumination pattern generation while preserving its output and randomization behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0664b345eef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.