# Issue

**Title:** fix(security): patch high and critical dependency vulnerabilities

## Description

<!-- Do Not Delete This! pr_template -->

### Context

Fixes the high/critical findings from the latest `pnpm audit`

- [decode-uri-component vulnerable to denial of service via quadratic replacement of percent-encoded runs](https://github.com/advisories/GHSA-qr28-fpjm-wq7f)
- [body-parser vulnerable to Denial of Service via trailing bytes after a compressed request body](https://github.com/advisories/GHSA-27r3-jxmh-p828)
- [follow-redirects sensitiveHeaders regex escaping can expose credential headers](https://github.com/advisories/GHSA-8r9p-f939-6h3c)
- [follow-redirects: Cross-realm sensitiveHeaders arrays are discarded and custom credentials can follow redirects](https://github.com/advisories/GHSA-mrwp-f3q8-3g9p)
- [follow-redirects array-form headers bypass cross-origin credential stripping](https://github.com/advisories/GHSA-q3jh-wrc6-jgq8)
- [joi: quadratic-time split in `string().email({ multiple: true })` allows denial of service](https://github.com/advisories/GHSA-4528-x5fx-h6hg)
- [launch-editor: `fs.existsSync()` existence check can be bypassed on Windows](https://github.com/advisories/GHSA-587h-7wmj-h5pm)
- [Zod can exhaust memory while validating oversized constrained collections](https://github.com/advisories/GHSA-mrhx-c7xc-m3w5)

### Changes & Results

All were fixed with `pnpm-workspace.yaml` overrides except decode-uri-component. It ships in the viewer through `query-string@6`, and its only fixed version is ESM-only, which v6 can't load. Instead, `query-string` is upgraded to 10.0.0 (in `@ohif/app`, `@ohif/core` and `@ohif/extension-default`), which drops the dependency entirely. No source changes were needed.

### Testing

- Dependency audit is clean: all of the above resolved; only the advisories already in `ignoreGhsas` remain.
- `MetadataProvider` and `preserveQueryParameters` unit tests pass; type check shows no new errors; production build passes.
- Manual: study list URL filter/sort/pagination round-trip (default and legacy study lists), preserved query parameters, DICOM JSON study loading, and general study viewing.
- CI checks will verify the upgraded packages overall.

### Checklist

#### PR

- [x] My Pull Request title is descriptive, accurate and follows the
  semantic-release format and guidelines.

#### Code

- [x] My code has been well-documented (function documentation, inline comments,
  etc.)

#### Public Documentation Updates

- [x] The documentation page has been updated as necessary for any public API
  additions or removals.

#### Tested Environment

- [x] OS: Windows 11 Pro
- [x] Node version: 24.15.0
- [x] Browser: Chrome 156.0.8078.80

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
  * Updated supporting packages used by the app and extensions, including query-string handling and request, redirect, editor, and schema-validation utilities.
  * These updates keep the app’s underlying package versions current.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `76d1da61e4ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.