# Issue

**Title:** fix(core): keep a private block whose creator holds a line break

## Description

## What this changes

. A private block is stored under the key `group:creator`, but the pattern that reads that key back (`BLOCK_KEY`) did not match a line break, so a block whose creator holds one (`"AC\nME"`) was dropped on write with only a warning. This adds the `s` flag to `BLOCK_KEY`, and makes `copyPrivateAliases` split its `key + "\n" + element` entries at the last line break, so an element deleted from such a block stays deleted after `deepCloneInstance`.

## The idea, in plain terms

A private block is like a labelled drawer; the label is the creator name. If the label had a line break in it, the code that reads labels could not read it, so the whole drawer was left out when the data was saved. This follows Option 1 of the issue: the label is kept exactly as it was read, which is what `docs/specs/naturalized-dataset.md` says the block key holds (NAT-U-PRIV-1, NAT-U-PRIV-8).

## Try it

```js
import { DicomMetaDictionary } from "@dcmjs-org/core";

const n = DicomMetaDictionary.naturalizeDataset({
    "00290010": { vr: "LO", Value: ["AC\nME"] },
    "00291001": { vr: "US", Value: [7] }
});
console.log(n["00291001"]); // [7]           (was: undefined)
console.log(DicomMetaDictionary.denaturalizeDataset(n));
// { "00290010": { vr: "LO", Value: ["AC\nME"] },
//   "00291001": { vr: "US", Value: ["7"] } } (was: {} and a warning)
```

## API

No public API change. `parsePrivateBlockKey` now accepts a creator with a line break (`\n`, `\r`, ` `, ` `); keys without one parse as before.

## Evidence

- `npx jest test/core/privateBlocks.test.js`: 25 passed. The 7 new tests (newline, CRLF, trailing newline and U+2028 creators; a plain and a newline creator in one group; `deepCloneInstance` after a delete; a Part 10 write and read) fail on `1.0-beta` (`d3e1bd2`) and pass with this change. With only the `BLOCK_KEY` change, the `deepCloneInstance` test still fails, which is why the split changes too.
- Full suite (`jest .`, Windows, Node 22.16.0): 1242 passed, 12 skipped, 2 failed. Both failures (`bundle-size` and `naturalizedRules` "committed projections are fresh") also fail on unmodified `1.0-beta` on that Windows checkout (CRLF line endings), so they are local, not from this change.
- Bundle size: the change adds about 236 bytes to `dcmjs.js`; the last `1.0-beta` CI run had about 1,184 bytes of headroom under the ×1.066 ceiling.
- `eslint`, `prettier --check`, `check:types` and `build` pass. Not run locally on Node 24; CI will cover it.

## Breaking changes

None.

## Fixtures used

None.

## Checklist

-   [ ] CI is green (tests on Node 22 and 24, lint, format, audit)
-   [x] The title is a conventional commit (`feat:`, `fix:`, `docs:`, …)
-   [x] Pure file moves are in their own commits and declared above (none)
-   [x] The prose is plain, direct English — jargon defined on first use

Note: `RELEASE_PLAN.md` describes staging branches (`release/1.0-beta-core`) for small PRs, but recent `fix(core)` PRs target `1.0-beta`, so this one does too. Happy to retarget.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3e1bd286245`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.