# Issue

**Title:** Clean and preview floating-point pixel data under the pixel options

## Description

<!-- claude-projects-attribution: {"github_login":"Matthew-Jennings"} -->
_Requested by **Matthew** · [project thread](https://claude.ai/code/project/chan_019N36FpZumLw3ocGFgnGw6N?thread=cmsg_019N36FpZumLw3ocGFgnGw6N4pA7e2YMigD8x3FFKed3i6)_

## Summary

Clean Pixel Data and Clean Recognizable Visual Features now handle Float Pixel Data (7FE0,0008) and Double Float Pixel Data (7FE0,0009), so a floating-point Parametric Map is cleaned and reviewed as an integer one is, instead of being sequestered as `uncleanable-pixel-data` under Clean Pixel Data and held without any way to release it under Clean Recognizable Visual Features. Clean Pixel Data searches each frame, blacks out its text with the frame's smallest finite value in the element that held it, and checks the written values bit for bit. The QC pack previews floating-point frames as it previews integer stored values, so a reviewer's face verdict on those previews releases the instance. It follows #2576, which brought the Parametric Map into scope.

## ELI5

### The problem

A Parametric Map is an image whose pixels are a computed quantity, such as an apparent diffusion coefficient, rather than raw scanner signal. Some systems store those pixels as whole numbers, and some as decimal ("floating-point") numbers in a different DICOM field. #2576 let the engine accept Parametric Maps, but the two options that look at pixels only understood whole numbers. So a decimal map was set aside under Clean Pixel Data, and under Clean Recognizable Visual Features it was held for ever, because the review pack could not draw a picture of it for anyone to look at.

### What changes

Both options now read decimal pixels. Think of the whole-number path as a well-tested machine for reading a page of numbers; this change teaches it a second alphabet rather than building a second machine. The same text finder, the same blackout, the same written-file check, and the same review pictures are used, with three things that only decimal numbers need.

### Numbers that are not numbers

Decimal pixels can hold "not a number" (NaN) and plus or minus infinity. Viewers draw NaN as empty and clip infinities to the brightest or darkest grey. The previews draw NaN black, as padding already is. They do not simply clip infinities, though: an infinity drawn as the brightest real value disappears wherever it sits beside pixels that already have that value, and in a map whose real values are all the same, a whole pattern drawn in infinities would disappear. So the previews draw positive infinity a clear step brighter than the brightest real value, and negative infinity a clear step darker than the darkest, where the step is the range of the real values (or the value itself, or 1, when they are all the same). The text finder gets the same treatment, with NaN one more step down, so every kind of value stands apart from the others and none is a value the finder's arithmetic cannot handle.

### Hiding places

Because NaN, padding, and (in an all-empty frame) infinities are all drawn as plain black, a face drawn in a mix of them would be invisible in every preview. The engine already refuses to count a frame as "shown" when its padding holds more than one value, for exactly this reason. Floating-point frames follow the same rule: if the undrawn pixels are of more than one kind, the instance has no reviewable digest and stays held. Different NaN bit patterns count as one kind, since no viewer can tell them apart.

Previews normally set their contrast from the middle 99% of a picture's values. When a picture is almost entirely one value, that middle 99% is a single value, and a small pattern of another value used to be drawn the same grey as everything else. The previews now spread their contrast over the whole range in that case, so a small pattern still shows, however large the numbers are. They also do their arithmetic on halved values, so that two values at opposite ends of what a decimal pixel can hold, whose difference is too large to store, no longer turn the whole picture black.

### What the blackout writes

Whole-number frames are blacked out with their smallest stored value. Decimal frames are blacked out with their smallest finite value, padding included, exactly as for whole numbers. We did not use NaN, because many viewers read NaN as "missing data" and draw it as transparent, and we did not use 0.0, because zero can be a bright mid-range value in a map with negative values.

### Checking the result

After writing, the engine reads the file back and checks that every pixel outside the boxes is exactly what it was, and every pixel inside is the fill. For decimals it compares the raw bits, not the numbers, because NaN is never equal to itself and minus zero equals zero. That way a NaN keeps its exact bits and a zero its sign.

## Current integration and GitHub validation

Current merge `ec48c035aa161b971332fa0024d48949f3556786` combines the author's `94e1f56a997d4b0efa0bb094d53ac28f8fd8d84d` with actual main `c6fe84631ff13f2e59fd067e1161d48148acbdc7`, the merge of #2588. Both parents are independently verified. All three recorded predecessors, #2571, #2581 and #2588, have actually merged into main. The integration preserves main's six Presentation States, Encapsulated PDF, first five second-generation RT IODs, three delivery instructions, Enhanced RT Image pair, Surface Segmentation and map support: **60 supported IODs and 65 corpus files**, with 193 reviewed omitted-text attributes and 335 Basic Profile text attributes. Report format 60 and disabled preset/project-key activation are unchanged.

The reviewed floating-point production and regression files are unchanged from the assessed branch. The only conflicts were the scope description and D-010's prose: the resolution retains main's Presentation State/PDF restrictions and this PR's existing floating-point support. D-042 equals actual main, so this integration does not introduce another D-042 policy change while #2601 has its reserved round. The bit-preserving OF/OD path, finite-minimum fill, non-finite search/preview levels, sparse/uniform/large-range contrast, unsupported-layout refusals, complete-preview, own-verdict and block-confirmation rules remain intact. Mixed undrawn kinds and frames that float32 cannot represent remain unreviewable. Float masks/overlays and arbitrary-quantity CT face cleaning remain refused or deferred.

Fresh applicable GitHub CI and selected execution/actual-checkout-parent proof are pending for this head. The manager must verify every applicable unit partition/environment, combined report and CI/Security Summary, all retained float/Parametric Map/render/preview/digest/face cases, full-corpus checks, pydicom provenance and validator conditions. The declared evidence plan also retains main's Presentation State/reference/annotation/date/ICC, PDF-refusal, second-generation RT and instruction safeguards. Skipped rendering or validator cases do not count as execution. Earlier-head proofs and passing check metadata remain historical; synthetic merge-group and later-main evidence are separate.

The author's previous `94e1f56a` check hit the **30-minute minimum-version corpus-job limit**, explicitly recorded in [GitHub's annotation and failed job](https://github.com/pymedphys/pymedphys/actions/runs/42581885199/job/129042609150). Current actual main already gives the complete corpus 60 minutes in both main and floor matrices and requires the matching workflow contract. This integration inherits that correction unchanged, with every case, assertion, environment, per-test limit and required gate retained. No unchanged-head workflow or queue retry is granted.

The earlier `b4118127` queue departure at 03:54:40 UTC was explicitly `merge_conflict`, with no synthetic head of its own. The source dependency hold is now addressed by integrating its actual-main predecessors. The manager still requires fresh head CI and proof before its ordinary queue request; no feature branches were merged together and no direct queue action was performed here.

Main's document-bearing PDFs remain wholly sequestered under every policy; the document-free header fixture is a separate test. Presentation State annotations and overlays retain their holds, required image references remain kept, and creation-date/time and RGB ICC restrictions remain explicit. Surface's face hold and the exact seven-file face-review cohorts and twelve current/future outcomes are preserved alongside the separate full 65-file corpus. Existing legacy-validator limitations, radiation output-comparison gaps, delivery-instruction fixture/comparison limits and deferred RT decision cards remain explicit; synthetic evidence establishes no clinical, viewer or vendor-acceptance assurance.

All local commands, numerical checks and public 691-map counts below remain attributed author/reviewer evidence for their recorded revisions. They were not rerun or counted as current-head GitHub execution. The merge watch ran no local tests, linters, numerical/native probes, benchmarks or project/artefact code. Existing completed scientific/layout reviews are reused. The concurrent Sourcery guide edits were read fully and preserved; they add no substantive finding or authority.

## Why

The coordinator approved this follow-up at 13:31 UTC on 7 November 2026, after Matthew was told of the floating-point limit on #2576. Without it, any floating-point Parametric Map is lost to a run that uses either pixel option, which are the options that a release of head images needs.

## What changed

- `pixel_cleaning.py`:
  - `Layout` gains `floating` and `element`; for floating-point layouts `dtype` is little-endian `f4` or `f8`, `word_of` keeps the value, and `fill` is the frame's smallest finite value, or 0.0 where it has none.
  - New `float_layout_of` reads the frames: exactly one of Pixel Data, Float Pixel Data, and Double Float Pixel Data; a native transfer syntax; one sample of MONOCHROME2; Bits Allocated 32 for Float Pixel Data and 64 for Double Float Pixel Data. Anything else is `uncleanable-pixel-data`, as before.
  - New `searched_values` gives the finder each frame divided by the power of two at or above its largest finite magnitude (exact for 32-bit values), with positive infinity above the largest finite value and negative infinity below the smallest, each by the finite range (or by 1 where the finite values are all one value or absent), and NaN below negative infinity by the same step; padding is searched as it is, as for integer frames. New `beyond` makes each step at least one float64 apart.
  - `redaction_problem` checks the redaction's own element, refuses an output holding any other pixel-data element, and compares floating-point values bit for bit.
  - No overlay and no defacer's mask is written into floating-point pixel data (`ValueError` and `uncleanable-pixel-data` respectively); no IOD in scope combines them today.
- `instance_transform.py`: `_with_redaction` writes a floating-point redaction to the element that held it, as OF or OD.
- `qc_previews.py`: floating-point pixel data are described and decoded as integer pixel data are, with Float or Double Float Pixel Padding Value and Range Limit as padding; NaN is undrawn, infinities are drawn beyond the frame's finite extremes by their range (or by their magnitude or 1, whichever is larger, where they are all one value), and a frame whose undrawn values are of more than one kind leaves its instance out of `pixels_shown`. A double-float frame whose values float32 cannot hold apart, or whose infinities would be drawn beyond float32, is listed as not previewed by the existing contrast check. A cleaned frame's review frame is drawn from the same decoded values, NaN as padding. Every preview's percentile window now falls back to the full range where its two percentiles are not apart as float32, as where all but a few values are one value, and a uniform image's window widens with its magnitude, so that a small pattern on one value, of any magnitude, is not drawn as that value; this applies to integer frames too. `_grey` halves each value and window limit before subtracting and dividing, which is exact, so that values that float32 holds but whose difference it does not, such as -3e38 and 3e38, are not drawn black.
- `text_evaluation_sources.py`: the text-detector evaluation skips floating-point frames as `float-pixel-data`, since it reads integer stored ranges; they were skipped before as refused.
- `conformance_values.py`, `reasons.py`, `scope.py`, and the design document (the Parametric Map passage, the QC pack's previews and their window, Clean Pixel Data's layouts, and its tests) describe the new behaviour.
- Tests:
  - New `test_deidentify_float_pixel_cleaning.py`: 32-bit and 64-bit frames, in Explicit and Implicit VR Little Endian, blacked out with the smallest finite value, with every other value's bits kept (a NaN payload, both infinities, and both zeros); frames without text written as they were; each frame searched as scaled finite values, scaled exactly by a power of two; values near the largest double searched without overflow; positive infinity, negative infinity, and both, on finite values that are all one value or on NaN, searched as values of their own, in both precisions, including finite extremes one float64 apart; a frame with no finite value searched apart and filled with 0.0; a changed NaN payload and pixel data moved to another element found as problems; and refusals for the wrong Bits Allocated, Double Float Pixel Data of 32 bits, both float elements, MONOCHROME1, three samples, no rows, no frames, short data, overlays, and a defacer's mask.
  - `test_deidentify_parametric_map_scope.py`: the corpus Parametric Map as 32-bit and 64-bit floats is cleaned under Clean Pixel Data and held for review with its text blacked out; on a reviewer's approved regions it satisfies Clean Pixel Data with Burned In Annotation NO; under Clean Recognizable Visual Features it is held without a verdict, previewed whole, and released on a face verdict bound to its written pixel data, with Recognizable Visual Features NO. The two tests that pinned the old refusal are replaced.
  - `test_deidentify_qc_previews.py`: a seven-slice synthetic head with a nose, as 32-bit and 64-bit floats, gives byte-identical PNGs (cine, projection, surface renders, full resolution) to its integer copy and is shown whole.
  - New `test_deidentify_qc_float_previews.py` (split from `test_deidentify_qc_previews.py`, which passed its 1,000-line limit): NaN is black and infinities are drawn beyond the finite extremes; positive infinity, negative infinity, and both, among finite values that are all one value (0, -7.5, and 30,000), in both precisions, are drawn at levels of their own in every full-resolution preview and in the review frame, with the instance shown whole; an infinity that would be drawn beyond float32 leaves the frame not previewed; float padding, with and without a range limit, is left out of the window; undrawn values of more than one kind are not shown whole while two NaN payloads are; a double beyond float32 is not previewed; and a 10-pixel pattern on a 64 by 64 frame of one value (negative infinity on 1e20 and on -3e30, positive infinity on 1e20, a value 2**-6 above 1e20, and 1e-10 on 0), in both precisions, drawn apart from the background in every preview with the instance shown whole, and a uniform image of 1e20, -7.5, or 0 drawn mid-grey under both windows; and, in both precisions, a 64 by 64 frame of -3e38 with ten +3e38 pixels and the reverse drawn 0 and 255 apart and shown whole, a 4 by 8 frame of -2e38, -1e37, and positive infinity drawn at three increasing levels, and `_grey` of -3e38, 0, and 3e38 giving 0, 128, and 255.
  - `test_deidentify_qc_pixel_digests.py`: a floating-point frame that Clean Pixel Data cleaned is shown beside its frame as received, followed by its review frame; `test_deidentify_text_evaluation.py`: floating-point frames are skipped by why.

## Scope and what is deferred

- In scope: Float Pixel Data and Double Float Pixel Data of one MONOCHROME2 sample in Explicit or Implicit VR Little Endian, which is what the Floating Point and Double Floating Point Image Pixel Modules allow a Parametric Map.
- Unchanged: a Parametric Map in a defaced CT frame is still held until its own previews show no face, since defacing an arbitrary quantity has no single right "air" value; the face-review digest already covered both float elements, so verdict binding needed no change.
- Public evidence is a local run, not a test: all 691 floating-point Parametric Maps of the `tcga_gbm360` analysis results in NCI Imaging Data Commons (CC BY 4.0), described under "How was this tested?". A hand-run workflow that runs the same check on them, counts only, is on a branch of its own and follows as a separate pull request. The tests' end-to-end evidence remains the corpus Parametric Map converted to floats.
- The floating-point feature adds no format constant, corpus file, UID block, or design decision number. The current integration inherits main's existing 65-file corpus unchanged.

## How was this tested?

```bash
uv run -- pymedphys dev tests tests/dicom -n 4
uv run -- ruff format lib/pymedphys/_dicom/deidentify lib/pymedphys/tests/dicom
uv run -- ruff check lib/pymedphys
uv run -- pyright <changed modules>
uv run -- pylint --rcfile lib/pymedphys/.pylintrc <changed modules and tests>
uv run -- pre-commit run --files <changed files>
```

The new and changed tests pass, and ruff, pyright, pylint, and pre-commit are clean on the changed files. The full `tests/dicom` run on the first commit gave 17,860 passed and 27 failed; the same 27 failed on #2576's head (a5fd2d89) without this change, and #2576 fixed them (90572cd7, 1b392978, b7525d28). After merging #2576's head 951335b9 (which carries main, with the redaction review frames and review modes), the affected modules (float and integer pixel cleaning, Parametric Map scope, QC previews, pixel digests, redaction previews and review, visual features, text evaluation, compressed redaction, embedded overlays, corpus end to end, and conformance) gave 1,520 passed, none failed. After the fix for the first review's finding (924e778a), the same modules with every QC preview, pack, and verdict module and the Parametric Map pixel-risk module all passed, none failed, and ruff, pyright, pylint, and pre-commit are clean on the changed files. After the fix for the second review's finding (865c385b), the same modules with the face validation modules gave 3,092 passed, none failed. After the fix for the third review's finding (58e9c0b3), they gave 3,099 passed, none failed.

I also ran this branch locally on all 691 public floating-point Parametric Maps of the `tcga_gbm360` analysis results in NCI Imaging Data Commons (collection TCGA-GBM, CC BY 4.0; pathology-derived AI maps, each one frame of 32-bit Float Pixel Data in MONOCHROME2), counting outcomes only. Under Clean Pixel Data with the default text detector, every map was written in Float Pixel Data with its data type and shape kept: 389 had regions found, were blacked out, and were held for review, and 302 had none and were written unchanged. Two of the 389 that I inspected had boxes on tissue texture, not text, so the detector's false positives on these maps fall to the reviewer, as they do for integer frames. Under Clean Recognizable Visual Features, all 691 were held without a verdict, previewed and shown whole, and released on a face verdict with Recognizable Visual Features NO. None of the 691 holds NaN or an infinity, so drawing and searching infinities apart from the finite values, the fix for the first review's finding, leaves these outcomes as they were; the second and third fixes change only how previews are windowed and drawn, not whether these maps are shown whole; a run of the follow-up's check module on a fresh download gave the same counts.

## Reviewer focus

- `_drawn_floats` in `qc_previews.py`: the rule that a frame whose undrawn values are of more than one kind is not shown whole, and the step by which infinities are drawn beyond the finite extremes. The first is the floating-point counterpart of the mixed-padding rule; check that no other combination lets a pattern hide in values that every preview draws alike. NaN, drawn black, beside negative infinity, the darkest drawn value, is drawn alike, as integer padding is beside the smallest stored value.
- `_window`, `_full_range`, and `_grey`: the full-range fallback where the percentiles are not apart, which also changes how an integer frame that is almost all one value is drawn (over its full range rather than a fixed window of width 1), and the halved arithmetic.
- The fill choice, smallest finite value with padding included, and the finder's input from `searched_values`. The handoff suggested feeding the finder the 8-bit preview window; I kept the finder's own windowing and filters on the scaled values instead, because quantising to 8 bits before the finder would lose low-contrast text in a high-dynamic-range map and would differ from how integer frames are searched.
- The PS3.3 constraints that `float_layout_of` enforces (one sample, MONOCHROME2, Bits Allocated 32 or 64 by element) and that float pixel data are native only. I checked these against the handoff's PS3.3 2026d notes; the NEMA site was unavailable when I tried to re-read C.7.6.24, C.7.6.25, and PS3.5 Annex A, so please confirm.

## Breaking changes

- [x] None
- [ ] Yes (describe below)

Floating-point pixel data that were sequestered or held for ever are now cleaned or reviewable. Integer previews also retain the sparse-value and extreme-range contrast corrections described above.

## Documentation

- [ ] Not needed (say why)
- [x] Updated in this pull request
- [ ] Follow-up change needed

## Checklist

- [x] The pull request is focused on one concern
- [x] Tests or other evidence are included, or I explained why not
- [ ] `CHANGELOG.md` has an entry that ends with a link to this pull request (the programme keeps one M6 entry, written at release)
- [x] Documentation is updated, or I explained why not
- [x] Breaking changes are noted

---
_Generated by [Claude Code](https://claude.ai/code/session_01XKtVKaKT3LquRkwce6oCMs)_

## Summary by Sourcery

Support cleaning, previewing, and reviewing native floating-point pixel data so Parametric Maps receive the same de-identification workflow as integer images.

New Features:
- Add Clean Pixel Data support for native 32-bit and 64-bit floating-point pixel data, including text detection, redaction, validation, and bit-preserving writes.
- Enable QC previews and face-review release workflows for floating-point Parametric Maps, including handling of padding, NaN, infinities, sparse values, and extreme numeric ranges.

Bug Fixes:
- Prevent floating-point Parametric Maps from being unnecessarily sequestered or held indefinitely when pixel cleaning or visual-feature review is enabled.
- Improve preview contrast for sparse or extreme-value images so meaningful pixel patterns remain visible.

Enhancements:
- Enforce supported floating-point image layouts and retain existing refusal behavior for unsupported combinations, overlays, and defacer masks.
- Skip floating-point images in integer-specific text-detector evaluation and update conformance and design documentation.

Documentation:
- Update de-identification conformance and design documentation to describe floating-point pixel cleaning and preview behavior.

Tests:
- Add comprehensive coverage for floating-point cleaning, Parametric Map scope, QC previews, pixel digests, and text-evaluation handling.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c6fe84631ff1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.