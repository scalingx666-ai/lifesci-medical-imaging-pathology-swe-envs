# Issue

**Title:** Fix DSdecimal NaN equality to match DSfloat

## Description

## Summary

* `DSfloat.__eq__` (and `DataElement.__eq__`) were fixed in #2296 so that two
  `NaN`-valued **DS** elements compare equal, since `float('nan') != float('nan')`
  isn't a useful default for structural dataset comparison (e.g.
  `ds == deepcopy(ds)`).
* That fix only touched the `DSfloat` backing class. `DSdecimal` (used when
  `config.use_DS_decimal = True`) has the exact same problem, since
  `decimal.Decimal('NaN') == decimal.Decimal('NaN')` is also `False`, and it
  was never patched.
* This PR mirrors the `DSfloat.__eq__` NaN handling in `DSdecimal.__eq__` so
  both backing classes behave the same way, and adds a regression test
  (`TestDSdecimal.test_comparison_with_nan`) that fails on `main` and passes
  with this change.

## Test plan

- [x] Added `tests/test_valuerep.py::TestDSdecimal::test_comparison_with_nan`,
      confirmed it fails without the fix and passes with it
- [x] `pytest tests/test_valuerep.py tests/test_dataelem.py` (707 passed)
- [x] `ruff check src/pydicom/valuerep.py`
- [x] `ruff format --check src/pydicom/valuerep.py tests/test_valuerep.py`
- [x] Added a `doc/release_notes/v3.1.0.rst` entry

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `652ec68a24de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.