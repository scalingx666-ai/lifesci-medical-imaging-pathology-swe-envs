# Issue

**Title:** build(deps): bump ncipollo/release-action from 1.12.0 to 1.14.0

## Description

Bumps [ncipollo/release-action](https://github.com/ncipollo/release-action) from 1.12.0 to 1.14.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/ncipollo/release-action/releases">ncipollo/release-action's releases</a>.</em></p>
<blockquote>
<h2>v1.14.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Bump semver from 6.3.0 to 6.3.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#350</a></li>
<li>Bump actions/checkout from 3 to 4 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#364</a></li>
<li>Bump glob from 10.3.1 to 10.3.4 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#361</a></li>
<li>Bump jest-circus from 29.5.0 to 29.6.4 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#359</a></li>
<li>Bump typescript from 5.1.6 to 5.2.2 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#362</a></li>
<li>Bump <code>@​types/node</code> from 20.3.3 to 20.6.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#366</a></li>
<li>Bump jest and <code>@​types/jest</code> by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#367</a></li>
<li>Bump <code>@​babel/traverse</code> from 7.17.3 to 7.23.2 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#378</a></li>
<li>Bump jest and <code>@​types/jest</code> by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#377</a></li>
<li>Bump jest-circus from 29.6.4 to 29.7.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#376</a></li>
<li>Bump <code>@​types/node</code> from 20.6.0 to 20.8.6 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#379</a></li>
<li>Bump <code>@​actions/core</code> from 1.10.0 to 1.10.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#375</a></li>
<li>Bump <code>@​types/jest</code> from 29.5.5 to 29.5.7 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#386</a></li>
<li>Bump actions/setup-node from 3 to 4 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#381</a></li>
<li>Bump <code>@​types/node</code> from 20.8.6 to 20.9.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#390</a></li>
<li>Bump typescript from 5.2.2 to 5.3.2 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#396</a></li>
<li>Bump <code>@​types/node</code> from 20.9.0 to 20.10.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#395</a></li>
<li>Bump <code>@​types/jest</code> from 29.5.7 to 29.5.11 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#399</a></li>
<li>Bump <code>@​actions/github</code> from 5.1.1 to 6.0.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#385</a></li>
<li>Bump typescript from 5.3.2 to 5.3.3 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#403</a></li>
<li>Bump <code>@​types/node</code> from 20.10.1 to 20.10.6 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#402</a></li>
<li>Upgrade to Node 20 by <a href="https://github.com/aovens-quantifi"><code>@​aovens-quantifi</code></a> in <a href="">ncipollo/release-action#411</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/aovens-quantifi"><code>@​aovens-quantifi</code></a> made their first contribution in <a href="">ncipollo/release-action#411</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/ncipollo/release-action/compare/v1...v1.14.0">https://github.com/ncipollo/release-action/compare/v1...v1.14.0</a></p>
<h2>v1.13.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Fixed <a href="">#357</a> - we now use a <code>ReadStream</code> for artifacts which will hopefully prevent them from being loaded entirely into memory before being uploaded.</li>
<li>Bump json5 from 2.2.1 to 2.2.3 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#296</a></li>
<li>Bump typescript from 4.9.3 to 4.9.4 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#293</a></li>
<li>Bump <code>@​types/node</code> from 18.11.10 to 18.11.18 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#292</a></li>
<li>Bump glob and <code>@​types/glob</code> by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#304</a></li>
<li>Bump typescript from 4.9.4 to 4.9.5 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#305</a></li>
<li>Bump jest-circus from 29.3.1 to 29.4.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#306</a></li>
<li>Bump jest-circus from 29.4.1 to 29.5.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#318</a></li>
<li>Bump <code>@​types/node</code> from 18.11.18 to 18.15.11 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#319</a></li>
<li>Readme: update checkout to v3 by <a href="https://github.com/SpencerIsGiddy"><code>@​SpencerIsGiddy</code></a> in <a href="">ncipollo/release-action#303</a></li>
<li>Bump typescript from 4.9.5 to 5.0.3 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#320</a></li>
<li>Bump glob from 8.1.0 to 9.3.2 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#321</a></li>
<li>Bump <code>@​types/jest</code> from 29.5.0 to 29.5.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#326</a></li>
<li>Bump glob from 9.3.2 to 10.2.2 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#330</a></li>
<li>Bump ts-jest from 29.0.5 to 29.1.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#329</a></li>
<li>Bump typescript from 5.0.3 to 5.0.4 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#327</a></li>
<li>Bump <code>@​types/jest</code> from 29.5.1 to 29.5.2 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#337</a></li>
<li>Bump glob from 10.2.2 to 10.2.6 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">ncipollo/release-action#339</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>2c591bc</code></a> Prepare 1.14.0</li>
<li><a href=""><code>1e3e9c6</code></a> Fix production build error</li>
<li><a href=""><code>c03240c</code></a> apply debug build</li>
<li><a href=""><code>66b1844</code></a> Upgrade to Node 20 (<a href="">#411</a>)</li>
<li><a href=""><code>a8aa04e</code></a> Bump <code>@​types/node</code> from 20.10.1 to 20.10.6 (<a href="">#402</a>)</li>
<li><a href=""><code>39c57fe</code></a> Bump typescript from 5.3.2 to 5.3.3 (<a href="">#403</a>)</li>
<li><a href=""><code>02a91b5</code></a> Fix build errors from github api update</li>
<li><a href=""><code>0300282</code></a> Bump <code>@​actions/github</code> from 5.1.1 to 6.0.0 (<a href="">#385</a>)</li>
<li><a href=""><code>c4a7702</code></a> Add more info about announcements category</li>
<li><a href=""><code>4f53bc4</code></a> Add discussionCategory caveat to readme</li>
<li>Additional commits viewable in <a href="https://github.com/ncipollo/release-action/compare/v1.12.0...v1.14.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ncipollo/release-action&package-manager=github_actions&previous-version=1.12.0&new-version=1.14.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot merge` will merge this PR after your CI passes on it
- `@dependabot squash and merge` will squash and merge this PR after your CI passes on it
- `@dependabot cancel merge` will cancel a previously requested merge and block automerging
- `@dependabot reopen` will reopen this PR if it is closed
- `@dependabot close` will close this PR and stop Dependabot recreating it. You can achieve the same result by closing it manually
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c868ad78859`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.