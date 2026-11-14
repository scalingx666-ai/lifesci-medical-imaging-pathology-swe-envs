# Issue

**Title:** API: support sending original image file without JPEG compression

## Description

I have some automated tasks, done with COCO Annotator API. Some of them need to download original image file, without compressing image each time I access it. So I've added shortcut in ```/api/images/{id}``` method, so it can take optional parameter `original` (which is set to `False` by default. If `original == True`, than any manipulation with image data is bypassed and original file is sent to response stream. Hope it's useful.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9cce5d2f6494`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.