# Issue

**Title:** BUG: Do not rebuild layout when a layout with the same content is set

## Description

`ctkLayoutManager::setLayout()` returns early if the new layout document equals the current one, but `QDomDocument::operator==()` only checks whether the two documents refer to the same underlying data, not whether their content is the same. Setting a newly parsed document with identical content therefore always called `refresh()`, which removed all views from the layout and added them again.

Slicer creates a new document from the layout node's description every time the layout node is modified (for example when a scene view is restored). Each of these rebuilt the whole layout, hiding and showing every view. A render request made at that time could be dropped while the view was hidden, so the 3D view kept showing stale content until the user interacted with it (see Slicer/Slicer#9450).

`setLayout()` now also compares the serialized content and skips the rebuild if it is unchanged. The new document is still stored, so `layout()` returns the document that was set. `refresh()` remains available to force a rebuild.

`ctkLayoutManagerTest1` is extended: setting a document with the same content must not hide the views, and setting a different layout must still rebuild. The new check fails without the fix and passes with it. Slicer's layout and view tests also pass with the fix.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c7bc5859d138`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.