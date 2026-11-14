# Issue

**Title:** ENH: Drop legacy EXECUTABLE_OUTPUT_PATH/LIBRARY_OUTPUT_PATH handling

## Description

Removes GDCM's handling of the old `EXECUTABLE_OUTPUT_PATH` / `LIBRARY_OUTPUT_PATH` variables, whose compatibility block is already marked *"This should be removed in the future"*. GDCM requires CMake >= 3.9.2, while the superseding `CMAKE_*_OUTPUT_DIRECTORY` variables have existed since CMake 2.6 — the legacy path cannot be reached by any supported configuration.

The public `GDCM_EXECUTABLE_OUTPUT_PATH` / `GDCM_LIBRARY_OUTPUT_PATH` defines in `gdcmConfigure.h` are **retained**, with unchanged values.

⚠️ **Behavior change:** setting `EXECUTABLE_OUTPUT_PATH` or `LIBRARY_OUTPUT_PATH` no longer redirects GDCM's output — it is now silently ignored. See the open question below; happy to adjust.

Builds on #226 (the OpenJPEG cache-entry fix) and should merge after it.

<details>
<summary>Rationale</summary>

CMake documents both variables as the *"Old executable location variable"* and *"Old library location variable"*, superseded by the `RUNTIME_OUTPUT_DIRECTORY`, `LIBRARY_OUTPUT_DIRECTORY` and `ARCHIVE_OUTPUT_DIRECTORY` target properties and their `CMAKE_*_OUTPUT_DIRECTORY` initializers. Those replacements are documented as far back as CMake 2.6 (2008) — roughly nine years before GDCM's own `cmake_minimum_required(VERSION 3.9.2...3.13.4)` floor (`CMakeLists.txt:4`).

To be precise: CMake does **not** deprecate these variables and emits no warning of its own — they remain documented and functional. The `message(WARNING)` calls removed here were GDCM's own. The argument for removal is not that CMake forbids them, but that GDCM's minimum CMake version makes the compatibility path dead code.

</details>

<details>
<summary>What changed</summary>

- Removed the compatibility block that read the old variables into `CMAKE_*_OUTPUT_DIRECTORY` (and its two `message(WARNING)` calls).
- Removed the "legacy internal usage" block that populated the old variables from the modern ones.
- Internal consumers now read the modern variables directly. `GDCM_LIBRARY_DIR` and `GDCM_LIBRARY_DIRS` use a new internal `GDCM_LIBRARY_OUTPUT_DIR`, preserving the previous shared/static distinction between `CMAKE_LIBRARY_OUTPUT_DIRECTORY` and `CMAKE_ARCHIVE_OUTPUT_DIRECTORY`.
- `gdcmConfigure.h.in` now substitutes `@CMAKE_RUNTIME_OUTPUT_DIRECTORY@` and `@GDCM_LIBRARY_OUTPUT_DIR@` in place of the old variables.

</details>

<details>
<summary>Public API is preserved</summary>

The two defines are consumed, so they are kept rather than removed:

- `Testing/Source/Common/Cxx/TestSystem1.cxx:148-151` uses `GDCM_EXECUTABLE_OUTPUT_PATH`.
- `TestKakaduDecompressionMD5.py` and `TestDCMTKMD5.py` use `gdcm.GDCM_EXECUTABLE_OUTPUT_PATH` via the SWIG bindings.

For any configuration that does not set the old variables, the generated values are byte-identical to before — both resolve to `<build>/bin`, verified by diffing the generated `gdcmConfigure.h` against `master`. `TestSystem1` passes.

</details>

<details>
<summary>Testing</summary>

Linux, GNU Make generator, `GDCM_BUILD_TESTING=ON`.

| | ctest | `TestSystem1` |
|---|---|---|
| master | 195/198 | pass |
| this PR | 195/198 | pass |

The failing set is identical before and after (`TestSCUValidation`, `TestEcho`, `TestFind` — pre-existing network-DICOM failures unrelated to this change). Also verified re-configure idempotency across three `cmake . && make` passes.

</details>

<details>
<summary>Open question: silent vs. warned</summary>

With this change, a project that still sets `LIBRARY_OUTPUT_PATH` gets it silently ignored: libraries land in `<build>/bin` and `GDCM_LIBRARY_DIRS` agrees, so the result is internally consistent — but the setting quietly loses effect, where previously it was honored (with a warning).

I kept the patch minimal, but silently ignoring an explicitly-set variable is arguably worse than the status quo. If you prefer, I can add a short warning along the lines of:

```cmake
if(EXECUTABLE_OUTPUT_PATH OR LIBRARY_OUTPUT_PATH)
  message(WARNING "EXECUTABLE_OUTPUT_PATH/LIBRARY_OUTPUT_PATH are ignored. Use CMAKE_RUNTIME_OUTPUT_DIRECTORY, CMAKE_LIBRARY_OUTPUT_DIRECTORY and CMAKE_ARCHIVE_OUTPUT_DIRECTORY.")
endif()
```

That would only fire for projects that genuinely set them (nothing writes those cache entries once #226 lands). Your call — happy to add it, drop this PR, or reduce it to just the `GDCM_LIBRARY_OUTPUT_PATH` define, which has no consumers at all.

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `69b7aea5ff1f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.