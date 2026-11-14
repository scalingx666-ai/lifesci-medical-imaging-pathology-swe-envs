# Issue

**Title:** refactor: RAII ownership for per-stage ggml contexts and allocators

## Description

## What
Function-local graph contexts and allocators now use ggml's own smart-pointer aliases from `ggml-cpp.h` (`ggml_context_ptr`, `ggml_gallocr_ptr`; they compile fine under C++14). Early-return paths no longer repeat `ggml_gallocr_free(galloc); ggml_free(ctx0);`.

Functions covered: `edgetam_encode_image`, `edgetam_perceiver_forward` (both sub-graphs), `sam2_encode_image_hiera`, `sam3_encode_image`, the 5 `sam3_segment_pcs` sub-graphs, `sam3_segment_pvs`, `sam3_propagate_single`, `sam3_encode_memory`.

## Why
The manual cleanup was copy-pasted onto every failure branch (about 50 frees). That's easy to get wrong when adding a new early return, and it hides the actual logic.

## Behaviour
- **Free timing is unchanged.** Each owner is destroyed at the same scope exit where the manual frees used to be (the end of each sub-graph block, or the end of the function). Graph outputs are still read before the allocator goes away. Destruction order is the same as before (allocator first, then context). No function freed a ctx/galloc partway through, so no `.reset()` calls were needed.
- `sam3_encode_image` hands ownership to `sam3_state` with `release()`.
- `sam3_state`, `sam3_tracker` and `sam3_model` members keep their current ownership.
- These regions are byte-identical because sibling PRs delete them: the test/debug API and the EdgeTAM profiler.

## Verification
- Parity tool, byte-compared against deterministic origin/main baselines. It covers encode_image, segment_pvs (point and box), visual tracker add_instance and propagate_frame:
  ```
  PARITY OK   edgetam_f16 gpu0
  PARITY OK   edgetam_f16 gpu1
  PARITY OK   sam2.1_hiera_tiny_q8_0 gpu0
  PARITY OK   sam2.1_hiera_tiny_q8_0 gpu1
  ```
- Full Release build: no errors and no new warnings. The only warnings are the existing ones in ggml and stb.
- `sam3_benchmark --filter tiny --n-frames 3`: every CPU row is OK. On Metal, the q8_0 and q4_0 rows are OK at about 790 ms/frame, the same as origin/main. The q4_1 Metal rows crash with SIGSEGV on origin/main too, so that bug already existed.
- Not tested at runtime: the text/PCS path (`segment_pcs`, `track_frame`). There's no full SAM3 model locally, so it was only compiled and its diff reviewed by hand.

```
$ git diff --shortstat origin/main
 1 file changed, 63 insertions(+), 150 deletions(-)
```

## Merge order
This PR touches many lines, some of them near the regions changed by the sibling cleanup PRs. It should **merge last** and be rebased on main at that point.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01M2qLmQ9ag49hT61V6i9qAq

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01832ef85fcc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.