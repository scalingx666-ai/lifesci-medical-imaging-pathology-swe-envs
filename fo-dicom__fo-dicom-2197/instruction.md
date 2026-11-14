# Issue

**Title:** Fix JSON serialization of empty single-valued text

## Description

Fixes fo-dicom/fo-dicom#2162.

#### Checklist
- [x] The pull request branch is in sync with latest commit on the *fo-dicom/development* branch
- [ ] I have updated API documentation
- [x] I have included unit tests
- [x] I have updated the change log
- [ ] I am listed in the CONTRIBUTORS file

#### Changes proposed in this pull request:
- Omit the `Value` member for empty single-valued text in the System.Text.Json converter, as required by PS3.18 F.2.5. Keep the attribute and its type.
- Extend the existing `Count != 0` check with an empty single-valued text check. These elements report a count of one even when their text is empty. The same check also covers Universal Resource elements.
- Use the text value rather than the buffer-size check suggested in the issue. Reading `Buffer.Size` can force lazy string-to-byte encoding before target encodings are set.
- Preserve nonempty text and empty positions within multi-valued attributes.
- Add tests for empty Short Text, Long Text and Unlimited Text, plus nonempty Short Text and Long Text controls.

#### Verification
Tested the core JSON converter tests locally on .NET 8, 9 and 10. All passed. The full test suite was not run for this change.

#### Scope
This PR updates only the System.Text.Json converter. The separate Newtonsoft.Json converter is unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ea6d424d0b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.