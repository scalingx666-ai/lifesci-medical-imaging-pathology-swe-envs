# Issue

**Title:** #159 DICOM Viewer allows image export as JPG/PNG even when download is disabled on shared folder

## Description

Fixes: #159 

### Changes 

Guests and other logged-in recipients open the viewer through /dicomjson, which never set hideCapture. Public links already did. The logged-in endpoint now checks the share the current user is opening and hides the Capture button when that share does not allow download. The owner's own files still show it.

### Tests

- [x] Share a DICOM folder with a guest and turn download off. The Capture button is hidden.
- [x] Turn download back on for that share. The Capture button is visible again.
- [x] Open the same file as the owner. The Capture button stays visible.
- [x] Open a public link with download hidden. Capture stays hidden.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3930a8768f4b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.