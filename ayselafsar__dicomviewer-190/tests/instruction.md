# Issue

**Title:** #177 Folder download (ZIP) of an external storage folder that was never scanned contains only empty folders

## Description

Fixes: #177

### Changes

Downloading a folder from external storage returned a zip with only empty directories when Nextcloud had not scanned inside that folder yet. This happens when a study is added on the storage and downloaded before anyone opens its subfolders.
Before the zip is built, the app now scans a folder whose size is still -1. Folders that are already indexed are unchanged.

### Tests

- [x] On external storage, add a folder with files inside a subfolder without opening that subfolder in Nextcloud
- [x] Download the new folder as a zip from the parent listing
- [x] Confirm the zip contains the files, not only empty directories
- [x] Download an already indexed folder and confirm it still downloads as before

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3930a8768f4b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.