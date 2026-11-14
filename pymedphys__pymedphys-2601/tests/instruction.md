# Issue

**Title:** Explain a date that begins a kept datetime (MIDI-B Full Dates same-day holds)

## Description

<!-- claude-projects-attribution: {"github_login":"Matthew-Jennings"} -->
_Requested by **Matthew** · [project thread](https://claude.ai/code/project/chan_019N36FpZumLw3ocGFgnGw6N?thread=cmsg_019N36FpZumLw3ocGFgnGw6NKvMMuW7q6ru6WfSN8oQNaw)_

## Summary

Under any option that keeps datetimes, such as Retain Longitudinal Temporal Information with Full Dates, a removed date, or a removed datetime's date, that the residual search finds as the first eight characters of a kept datetime no longer withholds the instance. Those eight characters are the kept value's date, which the option releases anyway, and the removed value's time is not in them. The existing retained-value exemption now explains such a finding, as it already does for a datetime's date found in a kept date. A removed datetime whose time is also found, at the kept value's start or inside it, still withholds. The author reports that an earlier MIDI-B Test rerun recovered 545 GE PET instances, moving Full Dates from 24,903 to 25,448 released, equal to the Basic Profile. Those are attributed earlier-revision results; the matching rule does not change the validation boundary.

## ELI5

The GitHub corpus jobs also get enough time to finish: 60 minutes for the complete corpus in the main, minimum-version and standalone DICOM matrices. All other job budgets, test selections, individual test limits and required checks retain their existing rules.

### The problem

When the engine removes a value, the residual search keeps a copy of it and checks that it does not turn up anywhere in what is written. A date and time, such as a scanner's private "scan at 10:15 on 2 January", is searched for whole, and also by its date alone, because a date can leak without its time.

Full Dates keeps a PET image's Radiopharmaceutical Start DateTime, the injection time, such as "2 January, 09:30". A GE scanner also copies several times of the same day into its own private elements, which the Basic Profile removes. The search finds each removed time's date, "2 January", at the start of the kept injection datetime. Before this change, the engine called that a leak and withheld the file, because a found date inside a longer kept value was never explained. So 545 Test PET files were sequestered under Full Dates, although basic released them.

### What this does

Where the find is the first eight characters of a kept datetime, and the removed value is a date, or a datetime whose date is exactly those characters, the find is now explained. It is like finding the date of a removed appointment at the top of a diary page that you are publishing anyway: the page already shows that date, and nothing about the removed appointment's time.

### Why each choice was made

- **Only the first eight characters.** DICOM writes a datetime as its date, YYYYMMDD, followed by the time, so those characters are the kept value's own date. A date found later in a kept value is not its date, and still withholds.
- **The time must not be found.** A removed datetime written to the minute, such as "2 January, 09:30", is found whole at the start of a kept "2 January, 09:30:00". That match covers part of the kept time, so it still withholds, and so does a removed datetime found whole inside a kept one.
- **Every pooled value must agree.** The search pools a source's values across the patient and records one finding of it in each element, so the find is explained only where every pooled value that could be in the element is explained there. A value of another day, which is not there, does not stop the explanation.
- **Only dates and datetimes.** Removed text that happens to look like a date, found at the start of a kept datetime, still goes to review, since the engine does not know that it is a date.
- **Other spellings and ACR-NEMA dates stay held.** A date written as `2020-01-02`, or as ACR-NEMA's `2020.01.02`, is not how DICOM writes the kept value's date, so a find in that spelling is not explained.
- **A datetime written to the day counts as a date.** A removed DT holding only `20200102` reveals exactly what a removed DA does, and in a kept date it is already explained as a whole value.
- **Every option that keeps a datetime.** D-042 is one rule for every Retain option, so this also applies where Retain Device Identity keeps Calibration DateTime: a removed Acquisition DateTime of the same day found there by its date is now explained.
- **Under Modified Dates or no option, nothing changes.** Shifted dates are written by the engine, so a shifted value equal to its own source would mean that the shift failed, and nothing is explained there.
- **No new exemption name.** It is the existing retained-value exemption, so the release report's format and its `exempted_findings` codes are unchanged.

## Current decision and GitHub validation

Matthew accepted the exact reviewed date-prefix rule on 9 November 2026. The one-line design decision record in `f40463055c0018fca61e1b7ff6289eb3f3fdec10` has parent `7b88da9515111827bd46af54616fd718b32a2671`; its remote head, parent and single added documentation line are independently verified. Application source and tests are unchanged from the  and . The accepted scope retains every pooled-value, time-bearing, non-date, other-spelling, own-source, UID and Modified Dates boundary described above.

The current head `f387460bbd3d9b88d40fdb98eb3e01248ca4c2a9` adds only the standalone DICOM corpus budget to the main/floor correction in `be77a2b7`. All three `corpus-runs` contexts now allow 60 minutes. Other Ubuntu, floor and narrow-extra parts retain 30 minutes, and Windows retains its existing 60. The standalone DICOM suite keeps its four parts; it continues to run deidentify-a-o modules within `others`. No part, environment, test, assertion, per-test timeout, workflow contract, required summary or combined-report gate is removed or weakened. Application code, application tests and D-042 are unchanged from `f4046305`.

At `be77a2b7`, the manager completed required PR-head CI, all declared selected execution/provenance and actual-checkout/main-parent proof before queueing. Those content-hashed receipts remain historical for that revision. Its separate synthetic group `65442ccf62489f5c7bcde6a03c730a254c9033f4`, with parents actual main `c6fe8463` and `be77a2b7`, then hit the standalone DICOM corpus job's remaining 30-minute limit: [GitHub's annotation and cancelled job](https://github.com/pymedphys/pymedphys/actions/runs/42714916578/job/129493943178) explicitly record that limit. GitHub removed the entry at 23:27:12 UTC on 9 November for `failed_checks`; the CI Summary reports the cancelled required narrow-extra job. This source correction supplies the missing corpus budget. The cancelled suite is not completed execution, and no unchanged-head workflow or queue retry is granted.

The earlier `f4046305` group and its minimum-version corpus limit remain recorded in the validation history; that main/floor correction is retained. Current-head fresh GitHub CI and selected execution/actual-checkout-parent proof are pending. The merge manager verifies every applicable partition/environment, combined report, summary and all existing option-kept/Full Dates/guard/validator/pydicom/provenance requirements before its ordinary queue request. Old PR-head, synthetic-group and later-main results remain separate evidence. The reserved D-042 merge round stays in force until this PR actually main-merges.

Author local results, the reviewer's 173 independent pure checks and historical MIDI-B archives remain attributed earlier evidence; none was rerun or counted as current-head execution by the merge watch. The current aggregate 545-instance gain is not established by those historical archives. No local tests, scientific probes, native validators, dependency setup or benchmark dispatch were performed for this judgement.

## Why

MIDI-B Test, run 42229019914: Full Dates alone withheld 545 GE PET instances that basic released. All are `residual-datetime` findings whose sources are private datetimes of the `GEMS_PETD_01` block, (0009,100D), (0009,100E), (0009,103B), (0009,103D), and (0009,1068), and in 454 instances also (0017,1004) and (0019,1004), found by their date at the start of the kept Radiopharmaceutical Start DateTime (0018,1078) or Stop DateTime (0018,1079) inside Radiopharmaceutical Information Sequence (0054,0016), each of the same date with a different time. Counts, codes, and tags only were read; no values. Tracking issue: #2075.

## What changed

- `option_kept.retained_value`, `whole_values`, and `_values_in`: the keyword `dates: bool` becomes `kept_vr`, `"DA"`, `"DT"`, or `None`. In an element of an attribute that the pinned dictionary gives only VR DT, a source value collected as DA or DT that is a valid YYYYMMDD date, or a DT value's `date-yyyymmdd` form, counts as a whole value where it equals the first eight characters of a whole kept value. Every other form is still checked against the written bytes, which refuses the explanation where it is found.
- D-042's Retained value paragraph, its rationale, and its tests, and D-043, in the design document; the Withheld rule of the release gate's consequences; the register notes for PS3.15-E.3.6-01 and the residual search; the release gate's and exemptions' docstrings; and the conformance statement's Full Dates sentence say so. D-042's pooled-value example, which this change reverses, now uses a datetime written to the minute found whole at the start of a kept Calibration DateTime.

## Scope and what is deferred

- On 9 November 2026 Matthew explicitly accepted the reviewed date-prefix exemption in the merge-management chat. Commit `f40463055c0018fca61e1b7ff6289eb3f3fdec10` records that decision in D-042. Time-bearing matches, non-date sources, other date spellings, own-source findings and Modified Dates retain their existing outcomes.
- As it amends D-042, this pull request must not share a merge round with another D-042 change.
- Current-head aggregate MIDI-B confirmation remains follow-up evidence for the author-reported gain; no manual benchmark dispatch is part of this merge judgement.

## How was this tested?

TDD: the new and changed tests, 41 of them, failed on main fcb1a73c and pass on the branch. After merging main ac823650, the option, Full Dates, register, conformance, exemption, and release gate tests pass (549), and before that merge the related de-identification modules passed (2,468 passed). Pylint (`pymedphys dev lint`) rated 10.00, and ruff, ruff format, and pyright are clean.

The MIDI-B owner re-ran 207410a4 on the saved Full Dates holds of Test's PET (TCIA, CC BY 4.0): all 545 are released with the retained-value exemption, and the 231 instances that basic also holds stay held. Their local counts match CI's exactly.

```bash
uv run -- pymedphys dev tests tests/dicom/test_deidentify_option_kept.py tests/dicom/test_deidentify_full_dates.py
uv run -- pymedphys dev lint
uv run -- ruff check . && uv run -- ruff format --check .
uv run -- pyright
```

New and changed tests:

- a removed DA, a removed DT's date, and a DT written to the day, that begin a kept Acquisition DateTime or Radiopharmaceutical Start DateTime under Full Dates, with fractional seconds or an offset from UTC, or a kept Calibration DateTime under Retain Device Identity, are released with the retained-value exemption, also with another pooled value of the same day or of another day;
- the same with no option or under Modified Dates, a DT to the minute found whole at the kept value's start, a DT found whole inside it, a date found after the start of a kept value, a date in another spelling in a kept DT, an ACR-NEMA date found by its date, and the kept datetime's own source still withhold, and removed text that begins a kept datetime goes to review;
- under Retain Device Identity, a pooled Acquisition DateTime of the same day found by its date in the kept Calibration DateTime is now released, while one written to the minute and found whole at its start still withholds;
- a PET image whose five `GEMS_PETD_01` datetimes are of its kept Radiopharmaceutical Start DateTime's day is released under Full Dates, with each of those findings exempt there, and one whose private datetime is found whole at or inside the kept datetime is withheld;
- the conformance statement's Full Dates section says so.

## Reviewer focus

- `_values_in`: the kept dates are the first eight characters of each whole kept value, only where `kept_vr` is `"DT"`. A `value` form is explained there only where its kind is a date or datetime and it passes `_is_date`; a `date-yyyymmdd` form only where its kind is a datetime, so an ACR-NEMA DA's derived form is never explained.
- The search's matching rule means a date preceded by a digit inside a kept DT is not a finding at all, so the "date after the start" tests use a value in which no digit precedes it.
- `kept_vr` is taken from the kept element's dictionary VRs being exactly `{"DA"}` or `{"DT"}`; UID matching passes `None`.

## Breaking changes

- [x] None

## Documentation

- [x] Updated in this pull request: the design document, the register, and the conformance statement's wording.

## Checklist

- [x] The pull request is focused on one concern
- [x] Tests or other evidence are included
- [ ] `CHANGELOG.md` has an entry that ends with a link to this pull request: not added, as the programme's single release entry covers it
- [x] Documentation is updated
- [x] Breaking changes are noted

---
_Generated by [Claude Code](https://claude.ai/code/session_01XKtVKaGMmEjrLB3aEGfFQ9)_

## Summary by Sourcery

Allow retained datetime values to explain matching dates at their YYYYMMDD prefix without exposing removed times, and give corpus validation jobs additional execution time.

New Features:
- Explain removed dates and datetime dates found at the start of kept DICOM datetime values under applicable retention options.

Bug Fixes:
- Prevent same-day PET and other retained-datetime findings from being incorrectly withheld while continuing to withhold time-bearing, malformed, differently formatted, and out-of-scope matches.

Enhancements:
- Document the retained-value exemption boundaries and behavior across conformance, requirements, design, and release-gate guidance.

CI:
- Increase GitHub corpus test job timeouts to 60 minutes while retaining existing budgets for other test partitions.

Documentation:
- Update de-identification design and conformance documentation for date-prefix exemptions in kept datetimes.

Tests:
- Add coverage for same-day date-prefix exemptions, pooled values, PET examples, retention options, and cases that must remain withheld or go to review.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac823650b690`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.