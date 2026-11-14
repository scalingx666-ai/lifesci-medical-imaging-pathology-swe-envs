# Issue

**Title:** BUG: Fix crash in ctkDICOMItem::Decode when called from multiple threads

## Description

Since #1460, the DICOM indexer extracts tag values in parallel, so `ctkDICOMItem::Decode` is called from several threads at the same time. `Decode` filled a static map of encoding names on first use without synchronization, and kept stateful `QTextDecoder` objects in a static map that all threads shared. As a result, concurrent first calls could:

- crash in `QMap<QString,QString>::insert` (worker thread stack: `ctkDICOMItem::Decode` ← `GetAllElementValuesAsString` ← indexer worker lambda);
- find the map partially filled, print `DICOM dataset contains some encoding that we never thought we would see (ISO_IR 100). Using ASCII encoding.`, and replace non-ASCII characters with `?`.

Fix:
- The map of encoding names is filled at the first call by the thread-safe initialization of a static local variable, and is only read afterwards.
- The codec of each encoding is looked up at its first use and cached in each thread (`thread_local`), so decoding needs no lock. The cache holds pointers to codecs owned by Qt, so nothing leaks when a thread exits.
- Values are converted with the stateless `QTextCodec::toUnicode` instead of a shared `QTextDecoder`. This also stops decoder state from carrying over from one tag value to the next.

`QTextCodec` is in Qt Core in Qt 5 and in `Core5Compat` in Qt 6, which CTK already links. Qt 6's native `QStringDecoder` was not used: it does not exist in Qt 5, and without ICU it cannot decode the ISO-8859-x, ISO 2022-JP and EUC-KR encodings used in DICOM.

Testing in 3D Slicer, where each run imported the `dataset1_Thorax_Abdomen` DICOM test data (291 files, `ISO_IR 100`) in a new process with `indexingThreadCount = 16`:
- without the fix: crashed in 2 of about 8 runs (debug build); `py_RSNAVisTutorialTest` also crashed once during a parallel ctest run;
- with the fix: 30 of 30 runs clean (debug build), with no encoding warnings. Slicer's DICOM tests pass (`py_DICOMReaders`, `py_DICOMPluginTests`, `py_RSNAVisTutorialTest`, `py_RSNAQuantTutorialTest`, `py_JRC2013VisTest`, ...).
- Import time (release build, 10 runs each) is the same as with a mutex that serializes all decoding: median 161.8 ms vs. 162.3 ms.

`TranslateDefinedTermPatientPosition` and `TranslateDefinedTermModality` use the same lazily filled static map pattern. They are not called by the indexer, so this PR leaves them unchanged.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0d63a39f9d7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.