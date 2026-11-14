# Issue

**Title:** refactor: use sam3_graph_compute in sam2_encode_image_hiera

## Description

`sam2_encode_image_hiera` open-coded exactly what `sam3_graph_compute` does: set the CPU thread count when the backend is CPU, run `ggml_backend_graph_compute`, and check the status. Every other stage in `sam3.cpp` already goes through the helper. The helper also logs `graph compute failed: <status>`, so the caller's own error print at this call site is dropped.

Rebased onto `main`. The earlier conflict was with #27 (RAII contexts/allocators), which had already removed the manual `ggml_gallocr_free`/`ggml_free` lines this diff sat on; the failure path is now just `return false;`.

**Verification:** a parity tool runs encode, PVS point + box, and a 3-frame visual track, then compares the output byte for byte with `main`. The SAM2.1 runs go through this function.
```
PARITY OK   edgetam_f16 gpu0
PARITY OK   edgetam_f16 gpu1
PARITY OK   sam2.1_hiera_tiny_q8_0 gpu0
PARITY OK   sam2.1_hiera_tiny_q8_0 gpu1
```
A Release build with `-DSAM3_BUILD_TESTS=ON` has no errors or new warnings.

`git diff --shortstat main`: 1 file changed, 1 insertion(+), 5 deletions(-).

Not fixed here, to keep the diff as reviewed: `sam3_encode_vit_from_preprocessed_selective` (~`sam3.cpp:7128`) still open-codes the same pattern, inside the test/debug region that #27 skipped.

Part of an over-engineering cleanup series.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01M2qLmQ9ag49hT61V6i9qAq

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0d3b1d058968`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.