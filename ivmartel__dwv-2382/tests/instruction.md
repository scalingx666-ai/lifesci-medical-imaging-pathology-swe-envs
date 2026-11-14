# Issue

**Title:** Bump tar from 7.5.2 to 7.5.22

## Description

Bumps [tar](https://github.com/isaacs/node-tar) from 7.5.2 to 7.5.22.
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>2a22bfc</code></a> 7.5.22</li>
<li><a href=""><code>df1cd8d</code></a> Allow transform to be falsey</li>
<li><a href=""><code>0cd9cc3</code></a> 7.5.21</li>
<li><a href=""><code>631ae59</code></a> list: prevent unbounded recursion</li>
<li><a href=""><code>ebbb720</code></a> 7.5.20</li>
<li><a href=""><code>2f27196</code></a> fix: fully disable and dispose of unzip when aborting parser</li>
<li><a href=""><code>be440da</code></a> 7.5.19</li>
<li><a href=""><code>2812e93</code></a> add maxDecompressionRatio guard against explosive decompression</li>
<li><a href=""><code>9ecd4d2</code></a> 7.5.18</li>
<li><a href=""><code>9e78bf0</code></a> refuse to let header size be less than 0</li>
<li>Additional commits viewable in <a href="https://github.com/isaacs/node-tar/compare/v7.5.2...v7.5.22">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by <a href="https://www.npmjs.com/~isaacs">isaacs</a>, a new releaser for tar since your current version.</p>
</details>
<details>
<summary>Install script changes</summary>
<p>This version adds <code>prepare</code> script that runs during installation. Review the package contents before updating.</p>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=tar&package-manager=npm_and_yarn&previous-version=7.5.2&new-version=7.5.22)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c90cf65dd3fd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.