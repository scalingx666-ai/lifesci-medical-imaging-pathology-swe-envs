# Issue

**Title:** Bump picomatch from 4.0.3 to 4.0.7

## Description

Bumps [picomatch](https://github.com/micromatch/picomatch) from 4.0.3 to 4.0.7.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/micromatch/picomatch/releases">picomatch's releases</a>.</em></p>
<blockquote>
<h2>4.0.7</h2>
<h2>What's Changed</h2>
<ul>
<li>fix: handle terminal globstars in parenthesized patterns by <a href="https://github.com/mrmlnc"><code>@​mrmlnc</code></a> in <a href="">micromatch/picomatch#198</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/micromatch/picomatch/compare/4.0.6...4.0.7">https://github.com/micromatch/picomatch/compare/4.0.6...4.0.7</a></p>
<h2>4.0.6</h2>
<h2>What's Changed</h2>
<ul>
<li>fix: scan full pattern when tokens are requested by <a href="https://github.com/mrmlnc"><code>@​mrmlnc</code></a> in <a href="">micromatch/picomatch#197</a></li>
<li>fix: return complete pattern parts from scan by <a href="https://github.com/mrmlnc"><code>@​mrmlnc</code></a> in <a href="">micromatch/picomatch#199</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/micromatch/picomatch/compare/4.0.5...4.0.6">https://github.com/micromatch/picomatch/compare/4.0.5...4.0.6</a></p>
<h2>4.0.5</h2>
<h2>What's Changed</h2>
<ul>
<li>fix: preserve all branches when rewriting risky repeated extglobs by <a href="https://github.com/MerlijnW70"><code>@​MerlijnW70</code></a> in <a href="">micromatch/picomatch#182</a></li>
<li>fix: honor the windows option when matching basenames by <a href="https://github.com/MerlijnW70"><code>@​MerlijnW70</code></a> in <a href="">micromatch/picomatch#183</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/MerlijnW70"><code>@​MerlijnW70</code></a> made their first contribution in <a href="">micromatch/picomatch#182</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/micromatch/picomatch/compare/4.0.4...4.0.5">https://github.com/micromatch/picomatch/compare/4.0.4...4.0.5</a></p>
<h2>4.0.4</h2>
<p>This is a security release fixing several security relevant issues.</p>
<h2>What's Changed</h2>
<ul>
<li>Fix for <a href="https://github.com/micromatch/picomatch/security/advisories/GHSA-c2c7-rcm5-vvqj">CVE-2026-33671</a></li>
<li>Fix for <a href="https://github.com/micromatch/picomatch/security/advisories/GHSA-3v7f-55p6-f55p">CVE-2026-33672</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/micromatch/picomatch/compare/4.0.3...4.0.4">https://github.com/micromatch/picomatch/compare/4.0.3...4.0.4</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/micromatch/picomatch/blob/master/CHANGELOG.md">picomatch's changelog</a>.</em></p>
<blockquote>
<h2>4.0.7 (2026-08-24)</h2>
<h3>Fixed</h3>
<ul>
<li>Fixed terminal globstars in parenthesized patterns (<a href="">#142</a>, <a href="">e279bd7</a>).</li>
</ul>
<h2>4.0.6 (2026-08-24)</h2>
<h3>Fixed</h3>
<ul>
<li><code>scan()</code> now scans the full pattern when tokens are requested, instead of merging the remaining path segments into the final token (<a href="">#62</a>, <a href="">5f5819d</a>).</li>
<li><code>scan()</code> now returns complete pattern parts, including leading and trailing empty segments, and handles nested and escaped parentheses correctly (<a href="">#58</a>, <a href="">f201165</a>).</li>
</ul>
<h2>4.0.5 (2026-07-02)</h2>
<h3>Fixed</h3>
<ul>
<li>Preserved every branch when safely rewriting repeated extglobs (<a href="">#182</a>, <a href="">6289307</a>).</li>
<li>Honored the <code>windows</code> option when matching basenames (<a href="">#183</a>, <a href="">ab8bc4d</a>).</li>
</ul>
<h2>4.0.4 (2026-03-23)</h2>
<h3>Security</h3>
<ul>
<li>Prevented regular expression denial of service (ReDoS) from crafted repeated or nested extglob quantifiers by safely rewriting or treating risky patterns as literals. The new <code>maxExtglobRecursion</code> option defaults to <code>0</code>; positive numeric values allow limited nesting, while <code>false</code> disables the safeguard (<a href="https://github.com/advisories/GHSA-c2c7-rcm5-vvqj">CVE-2026-33671</a>, <a href="">5eceecd</a>).</li>
<li>Prevented inherited object properties from being interpreted as POSIX character classes (<a href="https://github.com/advisories/GHSA-3v7f-55p6-f55p">CVE-2026-33672</a>, <a href="">4516eb5</a>).</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>6bb4067</code></a> 4.0.7</li>
<li><a href=""><code>fdfb155</code></a> Merge pull request <a href="">#198</a> from micromatch/issue-142</li>
<li><a href=""><code>38c6b7a</code></a> 4.0.6</li>
<li><a href=""><code>ada9d3f</code></a> Merge pull request <a href="">#199</a> from micromatch/issue-58</li>
<li><a href=""><code>9b74f6f</code></a> Merge pull request <a href="">#197</a> from micromatch/issue-62</li>
<li><a href=""><code>f201165</code></a> fix: return complete pattern parts from scan</li>
<li><a href=""><code>e279bd7</code></a> fix: handle terminal globstars in parenthesized patterns</li>
<li><a href=""><code>5f5819d</code></a> fix: scan full pattern when tokens are requested</li>
<li><a href=""><code>4f41a8e</code></a> 4.0.5</li>
<li><a href=""><code>02cfc1b</code></a> Update .verb.md and run verb to generate README documentation</li>
<li>Additional commits viewable in <a href="https://github.com/micromatch/picomatch/compare/4.0.3...4.0.7">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=picomatch&package-manager=npm_and_yarn&previous-version=4.0.3&new-version=4.0.7)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/ivmartel/dwv/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb0818279862`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.