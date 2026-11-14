# Issue

**Title:** Bump Docfx.App from 2.78.5 to 2.81.0

## Description

Updated [Docfx.App](https://github.com/dotnet/docfx) from 2.78.5 to 2.81.0.

<details>
<summary>Release notes</summary>

_Sourced from [Docfx.App's releases](https://github.com/dotnet/docfx/releases)._

## 2.81.0

## What's Changed

### ✨ Features & Platform Support

* Allow custom templates to override `search.min.js` in the modern template by @​filzrev in .
* Add `metadata.sourceLinkExclude` to exclude selected source paths from **View Source** links without removing API documentation by @​vicancy in .
* Record the DocFX build version in the `docfx_version` field of `manifest.json` by @​vicancy in .
* Add a .NET 11 RC target, including support for the .NET 11 Razor source generator, while retaining .NET 8, 9, and 10 targets by @​vicancy and @​filzrev in  and .

### ⚡ Performance & Reliability

* Reduce JavaScript template processing overhead and memory allocations by reusing parsed scripts and improving model conversion. Add execution limits to prevent runaway scripts from hanging builds by @​lahma in .
* Avoid unnecessary exceptions and repeated file reads when loading `toc.yml` by @​filzrev in .

### 🐛 Bug Fixes

* Restore source links for partial types extended by source generators by @​vicancy in .
* Fix local namespace links in managed reference documentation by resolving them through xrefs during site generation by @​vicancy in .
* Preserve nested XML blocks when inserting Markdown separators, preventing content from incorrectly rendering as code blocks by @​vicancy in .
* Preserve explicit `false` and `0` values when overwriting nullable properties by @​vicancy in .

### 📦 Dependency Updates

* Update Jint to **4.16.3** in .
* Update Markdig to **1.4.0** in  and .
* Update YamlDotNet to **18.1.0** in .
* Update PdfPig to **0.1.16** in .
* Update ICSharpCode.Decompiler to **11.1.0.9782** in .
* Update System.Composition to **10.0.12** in .

### Upgrade Notes

Custom JavaScript template preprocessors now enforce a **30-second timeout** and a **50-million-statement limit** for each `getOptions` or `transform` invocation. Long-running custom scripts may need adjustment.

**Full Changelog**: https://github.com/dotnet/docfx/compare/v2.80.1...v2.81.0

## 2.80.1

<!-- Release notes generated using configuration in .github/release.yml at main -->

## What's Changed
### 💪 Other Changes
* fix: preserve thematic breaks in overwrite Markdown by @​vicancy in
* fix: XML comment parse logics for block element that is adjacent to markdown content by @​filzrev in
* chore: Update Roslyn and Microsoft.Build package dependencies by @​filzrev in
* fix: preserve indentation around XML comment code blocks by @​vicancy in
* fix: stop metadata generation when restore fails by @​vicancy in
* fix: clarify empty .NET API diagnostics by @​vicancy in
* fix: share tool templates across target frameworks by @​vicancy in
* fix: honor TOC metadata while preserving file metadata overrides by @​vicancy in
* fix(deps): update esbuild to 0.28.1 and tsx to 4.22.4 by @​dependabot[bot] in
* feat(pdf): allow footer and header on cover and toc by @​sergimos in
* chore(deps): bump actions/setup-dotnet from 5 to 6 by @​dependabot[bot] in
* chore(deps): bump actions/checkout from 6 to 7 by @​dependabot[bot] in
* Bump Markdig from 1.1.0 to 1.1.1 by @​dependabot[bot] in
* deps: Update JsonSchema.Net dependency to 8.0.5 by @​filzrev in

## New Contributors
* @​sergimos made their first contribution in

**Full Changelog**: https://github.com/dotnet/docfx/compare/v2.78.6...v2.80.1

## 2.78.6

<!-- Release notes generated using configuration in .github/release.yml at main -->

## What's Changed
### 💪 Other Changes
* chore(deps): bump dependabot/fetch-metadata from 2.3.0 to 2.5.0 by @​dependabot[bot] in
* chore(deps): bump paulhatch/semantic-version from 5.4.0 to 6.0.1 by @​dependabot[bot] in
* chore(deps-dev): bump minimatch from 3.1.2 to 3.1.5 in /templates by @​dependabot[bot] in
* Bump Jint from 4.6.0 to 4.6.1 by @​dependabot[bot] in
* chore(deps): bump actions/upload-artifact from 6 to 7 by @​dependabot[bot] in
* chore(deps): bump actions/download-artifact from 7 to 8 by @​dependabot[bot] in
* Bump Markdig from 1.0.0 to 1.1.0 by @​dependabot[bot] in
* chore: remove unnecessary using to fix the Lint check by @​lahma in
* Make xref archive download test hermetic by @​vicancy in
* fix: treat different ports as external links by @​vicancy in
* chore: cleanup YamlSerializationTest.cs by @​filzrev in
* chore(deps-dev): bump follow-redirects from 1.15.11 to 1.16.0 in /templates by @​dependabot[bot] in
* chore(deps): bump postcss from 8.5.6 to 8.5.14 in /templates by @​dependabot[bot] in
* chore(deps): bump uuid and mermaid in /templates by @​dependabot[bot] in
* chore(deps-dev): bump lodash from 4.17.23 to 4.18.1 in /templates by @​dependabot[bot] in
* chore(deps): bump fast-uri from 3.1.0 to 3.1.2 in /templates by @​dependabot[bot] in
* chore(deps): bump mermaid from 11.15.0 to 11.16.1 in /templates by @​dependabot[bot] in
* chore(deps): bump dompurify from 3.3.1 to 3.4.13 in /templates by @​dependabot[bot] in
* chore(deps-dev): bump js-yaml from 4.1.1 to 4.3.1 in /templates by @​dependabot[bot] in
* chore(deps): bump postcss from 8.5.14 to 8.5.26 in /templates by @​dependabot[bot] in
* chore(deps): bump fast-uri from 3.1.2 to 3.1.5 in /templates by @​dependabot[bot] in
* chore(deps-dev): bump socket.io-parser from 4.2.5 to 4.2.7 in /templates by @​dependabot[bot] in
* chore(deps): bump ws, engine.io-client, engine.io and socket.io-adapter in /templates by @​dependabot[bot] in
* chore(deps-dev): bump brace-expansion from 1.1.12 to 1.1.18 in /templates by @​dependabot[bot] in
* deps: Update playwright version to 1.60.0 by @​filzrev in
* deps: Update roslyn package versions to 5.6.0 by @​filzrev in
* fix(deps): apply compatible npm security updates by @​vicancy in
* Bump the spectre group with 2 updates by @​dependabot[bot] in
* Bump the xunit group with 1 update by @​dependabot[bot] in
* Fix typo in Schema Document Processor overview by @​smartcaveman in
* Bump coverlet.collector from 8.0.0 to 8.0.1 by @​dependabot[bot] in
* chore(deps): bump paulhatch/semantic-version from 6.0.1 to 6.0.2 by @​dependabot[bot] in
* chore(deps): bump dependabot/fetch-metadata from 2.5.0 to 3.0.0 by @​dependabot[bot] in
* chore(deps): bump actions/deploy-pages from 4 to 5 by @​dependabot[bot] in
* chore(deps): bump azure/login from 2 to 3 by @​dependabot[bot] in
* Bump Jint from 4.6.1 to 4.6.3 by @​dependabot[bot] in
* chore(deps): bump dorny/test-reporter from 2.5.0 to 3.0.0 by @​dependabot[bot] in
* Bump AwesomeAssertions from 9.4.0 to 9.5.0 by @​dependabot[bot] in
* chore(deps): bump dependabot/fetch-metadata from 3.0.0 to 3.1.0 by @​dependabot[bot] in
* chore(deps): bump paulhatch/semantic-version from 6.0.2 to 6.0.3 by @​dependabot[bot] in
* chore(deps): bump actions/upload-pages-artifact from 4 to 5 by @​dependabot[bot] in
* chore(deps): bump codecov/codecov-action from 5 to 7 by @​dependabot[bot] in
* chore(deps): bump actions/github-script from 8 to 9 by @​dependabot[bot] in
* Bump the xunit group with 1 update by @​dependabot[bot] in
* Bump coverlet.collector from 8.0.1 to 10.0.1 by @​dependabot[bot] in
* Bump Microsoft.NET.Test.Sdk from 18.0.1 to 18.9.0 by @​dependabot[bot] in
 ... (truncated)

Commits viewable in [compare view](https://github.com/dotnet/docfx/compare/v2.78.5...v2.81.0).
</details>

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=Docfx.App&package-manager=nuget&previous-version=2.78.5&new-version=2.81.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

Dependabot will resolve any conflicts with this PR as long as you don't alter it yourself. You can also trigger a rebase manually by commenting `@dependabot rebase`.

[//]: # (dependabot-automerge-start)
[//]: # (dependabot-automerge-end)

---

<details>
<summary>Dependabot commands and options</summary>
<br />

You can trigger Dependabot actions by commenting on this PR:
- `@dependabot rebase` will rebase this PR
- `@dependabot recreate` will recreate this PR, overwriting any edits that have been made to it
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ea6d424d0b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.