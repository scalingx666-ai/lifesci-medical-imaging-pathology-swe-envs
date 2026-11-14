# Issue

**Title:** ENH: Faster DICOM indexing and fixes for tag cache and empty patient ID handling

## Description

DICOM database indexing: faster import, correct tag cache lookups, and fewer misleading log messages. Found while importing large 4D flow MRI studies (5 series × 5400 files) in 3D Slicer.

## Changes

**BUG: Store tags to precache in upper case**
`setTagsToPrecache()` stored the tags verbatim, but the tag cache is queried in upper case and `tagsToExcludeFromStorage` is upper case. Tags given with lower-case hex digits (for example `7fe0,0010` or `0019,100c`, as several Slicer DICOM plugins do) were never found in the cache, so every `fileValue`/`fileValues`/`fileValueExists` query re-read the files. For a 5400-file series, 3 of the 36 tag queries of Slicer's DICOM plugins took 24 s each instead of 0.15 s. The tags are now normalized to upper case. `ctkDICOMIndexerTest1` checks lower-case tags after indexing, and it now uses a temporary database file, because the indexer worker thread opens the database by file name.

**PERF: Parse DICOM files and extract cached tag values in parallel during indexing**
DCMTK parsing (1.4 to 5 ms per file) ran single-threaded and took about 75% of the indexing time. Files are now parsed in batches by a thread pool (`std::thread`). Results are pushed in file order, so progress reporting, cancellation, and the periodic database writes are unchanged. Parsed datasets are freed in a background thread, because freeing memory allocated by another thread is slow. The values of the tags to precache are extracted in parallel, and all tags of an instance are written with one multi-row `INSERT`. Indexing a 5400-file series: 21.9 s → 5.6 s.

The number of threads that read and parse files is set by the new `ctkDICOMDatabase::indexingThreadCount` property (the indexer uses the setting of its database). Extracting the tag values works on the datasets in memory, so it uses the number of logical processors minus 2. The default, 0, means 6 threads, but at most the number of logical processors minus 2 (at least 1), which leaves processing capacity for the user interface and other applications. The read-only `effectiveIndexingThreadCount` property returns the number that is actually used. Import time of a 4D flow study (27000 files, 4.4 GB, not in the file cache) in 3D Slicer:

| Threads | SSD | Hard disk | Network share |
|---|---|---|---|
| 1 | 185 s | 261 s | 1504 s |
| 2 | 134 s | 176 s | 1098 s |
| 4 | 69 s | 160 s | 885 s |
| 6 | 60 s | 160 s | 717 s |
| 10 | 45 s | 176 s | 466 s |
| 18 | 38 s | 172 s | 412 s |

Hard disks are fastest with 3-7 threads; SSDs and network shares keep getting faster with more threads. 6 threads is a compromise; applications can set a higher number (for example, from a user setting) when the data is on an SSD or a network share.

**BUG: Log the empty patient ID warning once per study and import instead of once per file**
"Patient ID is empty, using studyInstanceUID ... as patient ID" was logged for every file of an anonymized study, thousands of times per import. It is now logged by `updateDisplayedFields`, which processes all files of an import at once: one line per study, with the file count and an example file.

**BUG: Fix displayed fields update of patients with empty patient ID or name**
When the patient ID is empty, the patient is inserted with the study instance UID as a substitute ID. The displayed fields update still used the empty tag value, so the patient was not found. This logged "Unable to locate the patient due to missing values for PatientsName and/or PatientID..." at the end of every import, and the patient's displayed fields were not updated. The substituted values are now used.

**COMP: Use Python 3.12 in the lint workflow**
The lint job failed before running any check, because Python 3.9 is not available on the Ubuntu 26.04 image that `ubuntu-latest` now refers to (this affects every PR since that image change). The hooks pass locally with Python 3.12.

**COMP: Build Qt 5 on Ubuntu 24.04 and Qt 6 with CMake 3.22 in CI**
The build jobs failed at configuration on Ubuntu 26.04: its Qt 6 requires CMake 3.22 or later (the workflow used CMake 3.20.6), and its VTK is built with Qt 6, so it cannot be used in the Qt 5 build. The Qt 5 build now runs on `ubuntu-24.04` with CMake 3.20.6 (the minimum version required by CTK), and the Qt 6 builds on `ubuntu-latest` with CMake 3.22.6. The job names change accordingly, which matters if branch protection requires specific checks.

## Testing

- All 31 CTKDICOMCore tests pass (CTKData).
- Verified in 3D Slicer with Siemens, GE, and Philips 4D flow studies.

Draft: the fixes can also be split into separate PRs if preferred.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6d47c6339162`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.