# Issue

**Title:** Check the pixel options on public floating-point Parametric Maps

## Description

_Requested by **Matthew** · [project thread](https://claude.ai/code/project/chan_019N36FpZumLw3ocGFgnGw6N?thread=cmsg_019N36FpZumLw3ocGFgnGw6N4pA7e2YMigD8x3FFKed3i6)_

## Summary

Adds a hand-run workflow, `Pixel Options on IDC Parametric Maps` (`.github/workflows/parametric-map-check-idc.yml`), and its module, `pymedphys._dicom.deidentify.parametric_map_check`. Together they run Clean Pixel Data and Clean Recognizable Visual Features on the 691 public floating-point Parametric Maps of the `tcga_gbm360` analysis results in NCI's Imaging Data Commons (collection TCGA-GBM, [doi:10.5281/zenodo.17470190](https://doi.org/10.5281/zenodo.17470190), CC BY 4.0) and count what each option does. Only counts, codes, digests, versions, the text finder's method, and the data set's public identifiers leave the runner. The data set is pinned by IDC's index wheel and by one SHA-256 over all its files. This pull request now targets `main`, which contains the actual merge of #2596 whose floating-point support it exercises.

## ELI5

### The problem

#2596 teaches the two pixel options to read decimal ("floating-point") pixels, the kind a Parametric Map often holds. Its tests use a synthetic map: the corpus Parametric Map converted to decimals. That shows the code does what it should on data we built. It does not show the code copes with maps that a real system produced, which can have value ranges, padding, and quirks we did not think to build. The only real evidence so far is a local run in a development container, written up in #2596's description, which leaves no record on GitHub that a reviewer can inspect.

### What this adds

A workflow that anyone with write access can start by hand on GitHub. It downloads a fixed set of 691 real, publicly licensed decimal Parametric Maps from the US National Cancer Institute's Imaging Data Commons. It runs both pixel options on every one and posts a table of counts: how many had text found and blacked out, how many were written unchanged, and how many were held, previewed, and released on a face verdict. It is the same kind of check the repository already runs by hand for the HaN-Seg and PDDCA head scans.

### Making sure it is the same data every time

A public data set can change under you. The check pins the list of maps by the exact file of IDC's index that names them, checked by its SHA-256. It refuses to run unless that list holds exactly 691 maps, all of that analysis, licence, and DOI. After downloading, it refuses to run unless one combined SHA-256 over every file matches the pinned value. So a run either uses exactly the maps of the first run or stops and says why.

### Keeping patients' data private

These are scans of real patients, even though they are public and openly licensed, and this repository's logs are public. So the workflow publishes nothing read from the images, not even file names or paths. Only counts, outcome codes, digests, software versions, and the data set's public identifiers are shown in the job summary and the uploaded result files. Every command's normal output goes to files that stay on the runner. If the check crashes, the existing redacting wrapper (`run_redacted.py`) reports only the error's type and where in the code it happened. The maps are never cached or uploaded.

### What it does not show

These maps are pathology-derived AI maps of glioblastoma, not head images, so they show that the options work on real decimal data. They do not show that a face would be found. Face detection on real head scans is checked by the existing HaN-Seg, PDDCA, and Keating workflows.

## Current integration and GitHub validation

#2596 actually merged into main as `395d0605d111bdb8aa8539605fed4b17932b716a` on 10 November 2026. The main retarget and current merge `e4f6b02a9be8f75f64d6f6ca1d4f9e33b04efce7`, with parents reviewed `72a2ba6423edc58654df42ab2f4852737bcc49f8` and that actual main, are independently verified. Six reviewed implementation/workflow/test/documentation files are unchanged; the workflow contract retains its new harness checks alongside main's existing corpus-budget contract, and the design retains both the manual-check paragraph and main's scope/restrictions. The standalone DICOM corpus budget carries the already-assessed 60-minute correction from #2601, with its four parts, other budgets, all tests/assertions/environments/per-test limits and every required gate retained. No data pin, dependency version, application policy, conformance claim or result-format change is introduced by this integration.

The  and  are reused for the unchanged harness. Fresh applicable GitHub CI is pending for this main-targeted revision. The approval condition still requires CI Summary, Security Summary and every applicable unit partition/environment and combined report, including a successful minimum-version corpus job. The manager must verify selected non-skipped synthetic selection/refusal/accounting/digest/output-privacy tests, inherited floating-point checks, pydicom provenance and actual checkout/main parents before queueing. Old logs and the review's 16 historical archives remain evidence for their own revisions; no archive or local probe campaign was repeated.

The native-data workflow remains manually triggered and has not been dispatched by the merge watch. The 691-map counts below remain author-reported local outcomes. Its generated absent verdict exercises verdict binding; it is not a human review or evidence that a face is absent. Detector proposals on these microscopy-derived maps do not measure text-detection sensitivity or specificity, and map counts are not independent-patient counts. Hosted native pin verification, model execution and resource requirements remain unverified follow-up evidence, without changing the bounded harness's approval condition.

The review also records the existing advisory Mypy limitation: some broadly typed structured refusals lack `.value`, so the diagnostic can count a crash and stop that file's remaining checks. No demonstrated trigger was found in the pinned population. This remains a diagnostic limitation, rather than a claim that a rejected map was processed. The optional Mypy policy is unchanged. No clinical, viewer or vendor acceptance is established. The merge watch ran no local tests, linters, native/scientific probes, dependency setup, benchmarks or project/artefact code, and preserves the concurrent Sourcery summary and guide.

## Why

The autopilot asked for this follow-up at 21:55 UTC on 8 November 2026, after the 691-map local run for #2596. The aim is to turn that run into evidence anyone can repeat, as for the other public-data checks. The slot for this pull request was granted at 07:40 UTC on 9 November 2026.

## What changed

- New `lib/pymedphys/_dicom/deidentify/parametric_map_check.py`:
  - `select` reads the pinned idc-index-data wheel and keeps its Parametric Map Storage rows. It refuses them unless every row is of analysis result `tcga_gbm360` in collection `tcga_gbm`, under CC BY 4.0 and that DOI, with one instance per series, a UUID series identifier, and an `s3://idc-open-data/<uuid>/*` URL in IDC's public bucket; it also refuses duplicates and any count other than 691. It writes `selection.json` (counts alone) and an s5cmd manifest that places each series in a folder of its own.
  - `check` refuses the downloads unless the SHA-256 of their sorted per-file SHA-256s is the pinned value. It then runs each map through Clean Pixel Data, with the default text finder, and Clean Recognizable Visual Features, with no verdicts and then with a face verdict of absent bound to the written pixel data. It counts:
    - each Clean Pixel Data outcome;
    - whether each map is written in its own element with its data type and shape;
    - the regions blacked out, in bins of 0, 1, 2, 3 to 5, 6 to 10, and 11 or more;
    - under Clean Recognizable Visual Features, whether each map is held without a verdict, previewed and shown whole, and released;
    - crashes, by code site.

    It writes `parametric-map-check.json` and `parametric-map-check.md`, labelled `pymedphys-deid-parametric-map-check/1`.
  - A `Finder` protocol lets the tests pass a stub finder in place of the ONNX model.
- `text_evaluation_idc.index_rows` takes the columns to read, so the check can read the analysis-result and licence columns from the same pinned index.
- New `.github/workflows/parametric-map-check-idc.yml`:
  - Runs on `workflow_dispatch` only, with `contents: read` and `persist-credentials: false`.
  - Installs the `user` and `text-detection` extras and the hash-pinned pyarrow and s5cmd from `.github/text-evaluation/requirements.txt`.
  - Downloads and checks the index wheel, then runs `select`, the s5cmd download, and `check` through `run_redacted.py`, with output sent to private files on the runner.
  - Uploads only the results folder, kept for 90 days.
- `.github/scripts/test_workflow_contracts.py`: a contract test that the workflow only reads the repository, is started by hand, pins its actions and tools, and uploads only its results.
- `.github/text-evaluation/requirements.txt` (header comment), `lib/pymedphys/docs/contrib/info/workflows.md` (tree and section), and the design document's Parametric Map passage describe the check.
- New `lib/pymedphys/tests/dicom/test_deidentify_parametric_map_check.py`:
  - `select`'s order and its refusals (another analysis, collection, licence, DOI, instance count, bucket, folder, or identifier; too few maps; a series listed twice), and a destination that is not a plain path.
  - `check`'s counts on three synthetic floating-point Parametric Maps with a content-based stub finder, its refusal of files other than the pinned ones, and how the files' digest is formed.
  - The command: its page is the JSON's Markdown and is what it prints, neither names any map's UIDs, path, or folder, and an existing output folder is refused.

## Scope and what is deferred

- In scope: the manually triggered native-data workflow and its development module. Regular CI runs the synthetic tests; native data are not downloaded automatically for pull requests or scheduled runs. The conformance claim and public CLI remain unchanged.
- The workflow has not yet been run on GitHub. A `workflow_dispatch` workflow can only be started once it is on the default branch, so its first run follows the merge. The counts below come from running the same module locally.
- No format constant, corpus file, UID block, or design decision changes. The result format is a new family, `pymedphys-deid-parametric-map-check/1`.

## How was this tested?

```bash
uv run -- pytest -n auto lib/pymedphys/tests/dicom/test_deidentify_parametric_map_check.py lib/pymedphys/tests/dicom/test_deidentify_text_evaluation.py .github/scripts/test_workflow_contracts.py
uv run -- ruff check lib/pymedphys/_dicom/deidentify/parametric_map_check.py lib/pymedphys/_dicom/deidentify/text_evaluation_idc.py
uv run -- pre-commit run --from-ref origin/main --to-ref HEAD
python -m pymedphys._dicom.deidentify.parametric_map_check select <idc-index-data 25.0.5 wheel> --downloads <dir> --out <dir>
s5cmd --no-sign-request run <manifest.s5cmd>
python -m pymedphys._dicom.deidentify.parametric_map_check check <dir> --out <dir>
```

The tests pass, and ruff and pre-commit are clean. Locally, after a fresh s5cmd download of all 691 maps, the files' digest matched the pin and the module gave these counts, in about 31 minutes:

| Outcome | Maps |
| --- | --- |
| Clean Pixel Data: regions found, blacked out, held for review | 389 |
| Clean Pixel Data: no text found, written unchanged | 302 |
| Written in Float Pixel Data with data type and shape kept | 691 |
| Clean Recognizable Visual Features: held without a verdict | 691 |
| Previewed and shown whole | 691 |
| Released on a face verdict, Recognizable Visual Features NO | 691 |
| Crashes | 0 |

Regions blacked out per map: 0 in 302, 1 in 122, 2 in 105, 3 to 5 in 113, 6 to 10 in 37, and 11 or more in 12. These match the earlier local run reported in #2596. Two of the 389 maps with regions, inspected by eye in that run, had boxes on tissue texture rather than text; those are detector false positives that the reviewer rejects, as for integer frames.

## Reviewer focus

- What leaves the runner. Check `markdown` and the JSON that `check` writes, the workflow's redirections, and the upload path. Nothing read from a map should be logged or uploaded, apart from counts, codes, digests, versions, the finder's method, and public identifiers.
- The pins: the index wheel's URL and SHA-256 (shared with the text detector evaluation), the 691 count, and `FILES_SHA256`, the SHA-256 over the sorted per-file SHA-256 hex strings, each followed by a newline.
- The time limits: 120 minutes for the job, 30 for the download, and 60 for the check. Locally, in a 4-core container, the check of 691 maps took about 31 minutes, against the check step's 60. A hosted runner's time has not been measured yet, so the first run may show that the limits need to change.

## Breaking changes

- [x] None
- [ ] Yes (describe below)

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

Add a manually run, privacy-preserving validation of pixel de-identification options on pinned public floating-point Parametric Maps.

New Features:
- Add a manually triggered workflow and development module to validate pixel de-identification options against 691 pinned public floating-point Parametric Maps from IDC.
- Generate privacy-preserving JSON and Markdown results containing aggregate outcomes, dataset integrity information, software versions, and finder metadata.

Enhancements:
- Pin and verify the IDC index and downloaded files, redact command output, and ensure only non-sensitive results are published.
- Extend IDC index loading to support selecting specific columns.
- Add workflow contract and synthetic-data coverage for map selection, integrity checks, de-identification counts, and output privacy.

CI:
- Add contract coverage for the new manually triggered workflow and increase the corpus test job timeout to accommodate standalone DICOM corpus runs.

Documentation:
- Document the new IDC Parametric Map validation workflow and its privacy and retention behavior.

Tests:
- Add tests covering Parametric Map selection, dataset pins, aggregate checks, digest computation, command output, and sensitive identifier suppression.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `395d0605d111`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.