# Issue

**Title:** Bump eslint from 10.13.0 to 10.14.0

## Description

Bumps [eslint](https://github.com/eslint/eslint) from 10.13.0 to 10.14.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/eslint/eslint/releases">eslint's releases</a>.</em></p>
<blockquote>
<h2>v10.14.0</h2>
<h2>Features</h2>
<ul>
<li><a href=""><code>d23a7f9</code></a> feat: fix property descriptor handling in <code>func-name-matching</code> (<a href="">#21400</a>) (xbinaryx)</li>
</ul>
<h2>Bug Fixes</h2>
<ul>
<li><a href=""><code>4a12580</code></a> fix: require minimatch <code>10.2.6</code> to avoid vulnerable brace-expansion (<a href="">#21460</a>) (lumir)</li>
<li><a href=""><code>827a8f3</code></a> fix: <code>no-restricted-globals</code> crash on global objects as property values (<a href="">#21449</a>) (xbinaryx)</li>
<li><a href=""><code>161558a</code></a> fix: handle LS, PS and empty hashbang comments (<a href="">#21419</a>) (lumir)</li>
<li><a href=""><code>6194939</code></a> fix: <code>no-invalid-this</code> crash on <code>accessor</code> fields without initializer (<a href="">#21442</a>) (xbinaryx)</li>
<li><a href=""><code>9155e14</code></a> fix: Update <code>@​humanfs/node</code> dependency version (<a href="">#21434</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>cb2b9d4</code></a> fix: avoid invalid object-shorthand fixes for super methods (<a href="">#21323</a>) (dvd233)</li>
<li><a href=""><code>5ee3915</code></a> fix: yoda invalid autofix at statement start (<a href="">#21424</a>) (Daniel Pinto)</li>
</ul>
<h2>Documentation</h2>
<ul>
<li><a href=""><code>0f94f47</code></a> docs: remove <code>zh-hans</code> from docs language switcher (<a href="">#21437</a>) (lumir)</li>
<li><a href=""><code>dab466e</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>97431f8</code></a> docs: replace <code>--rulesdir</code> with a virtual plugin in custom rules docs (<a href="">#21452</a>) (Pixel)</li>
<li><a href=""><code>7697550</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>0c699d5</code></a> docs: Remove Tidelift commercial support (<a href="">#21416</a>) (Milos Djermanovic)</li>
<li><a href=""><code>0880666</code></a> docs: update loadESLint() documentation for v10 (<a href="">#21374</a>) (Minseon Kim)</li>
<li><a href=""><code>e06fe87</code></a> docs: Revise AI acknowledgment options in PR template (<a href="">#21414</a>) (Nicholas C. Zakas)</li>
</ul>
<h2>Chores</h2>
<ul>
<li><a href=""><code>0e2ab70</code></a> ci: disable <code>eslint-plugin-unicorn</code> ecosystem test (<a href="">#21462</a>) (Francesco Trotta)</li>
<li><a href=""><code>6e3f988</code></a> chore: update github/codeql-action action to v4.39.1 (<a href="">#21450</a>) (renovate[bot])</li>
<li><a href=""><code>a031c40</code></a> chore: update ecosystem plugins (<a href="">#21445</a>) (ESLint Bot)</li>
<li><a href=""><code>67d2ca2</code></a> chore: add troubleshooting page URL to circular fixes warning message (<a href="">#21429</a>) (Milos Djermanovic)</li>
<li><a href=""><code>276021d</code></a> chore: update github/codeql-action action to v4.39.0 (<a href="">#21432</a>) (renovate[bot])</li>
<li><a href=""><code>449724e</code></a> chore: update ecosystem plugins (<a href="">#21420</a>) (ESLint Bot)</li>
<li><a href=""><code>8ffeb8c</code></a> chore: update dependency prettier to v3.9.10 (<a href="">#21417</a>) (renovate[bot])</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>12cbff4</code></a> 10.14.0</li>
<li><a href=""><code>6b696e7</code></a> Build: changelog update for 10.14.0</li>
<li><a href=""><code>0e2ab70</code></a> ci: disable <code>eslint-plugin-unicorn</code> ecosystem test (<a href="">#21462</a>)</li>
<li><a href=""><code>4a12580</code></a> fix: require minimatch <code>10.2.6</code> to avoid vulnerable brace-expansion (<a href="">#21460</a>)</li>
<li><a href=""><code>0f94f47</code></a> docs: remove <code>zh-hans</code> from docs language switcher (<a href="">#21437</a>)</li>
<li><a href=""><code>dab466e</code></a> docs: Update README</li>
<li><a href=""><code>827a8f3</code></a> fix: <code>no-restricted-globals</code> crash on global objects as property values (<a href="">#21449</a>)</li>
<li><a href=""><code>97431f8</code></a> docs: replace <code>--rulesdir</code> with a virtual plugin in custom rules docs (<a href="">#21452</a>)</li>
<li><a href=""><code>6e3f988</code></a> chore: update github/codeql-action action to v4.39.1 (<a href="">#21450</a>)</li>
<li><a href=""><code>161558a</code></a> fix: handle LS, PS and empty hashbang comments (<a href="">#21419</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/eslint/eslint/compare/v10.13.0...v10.14.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=eslint&package-manager=npm_and_yarn&previous-version=10.13.0&new-version=10.14.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c90cf65dd3fd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.