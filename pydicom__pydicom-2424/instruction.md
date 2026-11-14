# Issue

**Title:** Document and test stop_when VR argument in data_element_generator

## Description

#### Summary
Updated docstring of stop_when in data_element_generator to indicate the correct number and names of arguments. The docstring also explicitly mentions that vr is None for implicit VR files and  tests are added to check the same.


#### Further details
- `data_element_generator` docstring now says the `stop_when` callable takes `(tag, vr, length)` and that `vr` is `None` for implicit VR data. The other docstrings point to this one.
- New tests in `TestDataElementGenerator`:
  - `test_stop_when_rewinds_to_start_of_element`: implicit VR, explicit VR with a 2-byte length, and explicit VR with a 4-byte length (OB). Checks the file is rewound to the start of the stopped element.
  - `test_stop_when_receives_none_vr_for_implicit_vr`: `vr` is `None`.
  - `test_stop_when_receives_vr_for_explicit_vr`: `vr` is the VR string.
- The existing `# XXX` comment in `filereader.py` is unchanged.

#### Tasks
- [x] Author has created all code and/or has reviewed AI-generated code line by line
- [x] Unit tests added that reproduce the issue or prove feature is working
- [ ] Fix or feature added
- [x] Code typed and mypy shows no errors
- [x] Documentation updated (if relevant)
  - [ ] No warnings during build
  - [ ] Preview link (CircleCI -> Artifacts -> `doc/_build/html/index.html`)
- [x] Unit tests passing and overall coverage the same or better

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5eecada40460`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.