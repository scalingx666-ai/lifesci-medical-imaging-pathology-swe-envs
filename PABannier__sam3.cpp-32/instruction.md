# Issue

**Title:** refactor: reuse sam3_read_f32 for small embedding readbacks

## Description

Six places in `sam3.cpp` open-code the same readback:
```cpp
if (t->type == GGML_TYPE_F16) { read into tmp; ggml_fp16_to_fp32_row(...); } else { read F32; }
```
The tensors are `pe_gaussian`, the 4 `point_embed`s, `not_a_point_embed`, `no_mask_embed`, `no_obj_embed_spatial` and `no_obj_ptr`. `sam3_read_f32(t, dst, n)` already does exactly this, and it also dequantizes quantized tensors, which the inline copies would have misread as F32. Each site becomes one call.

**Stacked on #25** because the `no_obj_ptr` read sits inside `sam3_track_frame`, which #25 restructures. Merge #25 first; GitHub will retarget this PR to `main`. The identical readbacks in the test-API region are left alone, since #20 deletes them.

**Verification:** a parity tool runs encode, PVS point + box, and a 3-frame visual track, then compares the output byte for byte with `origin/main`. The prompt-encoder caches and the SAM2.1 `no_obj_embed_spatial` path are covered.
```
PARITY OK   edgetam_f16 gpu0
PARITY OK   edgetam_f16 gpu1
PARITY OK   sam2.1_hiera_tiny_q8_0 gpu0
PARITY OK   sam2.1_hiera_tiny_q8_0 gpu1
```
The `no_obj_ptr` read in `sam3_track_frame` (text-prompted SAM3) only has a compile check, because no full SAM3 checkpoint is available locally.

`git diff --shortstat`: 1 file changed, 7 insertions(+), 49 deletions(-).

Part of an over-engineering cleanup series.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01M2qLmQ9ag49hT61V6i9qAq

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `39bb5bc35e90`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.