# Issue

**Title:** ci: bump the actions group across 1 directory with 5 updates

## Description

Bumps the actions group with 5 updates in the / directory:

| Package | From | To |
| --- | --- | --- |
| [actions/setup-java](https://github.com/actions/setup-java) | `6.0.1` | `6.2.0` |
| [actions/upload-artifact](https://github.com/actions/upload-artifact) | `7.0.1` | `7.0.2` |
| [actions/download-artifact](https://github.com/actions/download-artifact) | `8.0.1` | `8.0.2` |
| [apple-actions/import-codesign-certs](https://github.com/apple-actions/import-codesign-certs) | `7.0.0` | `7.2.0` |
| [stefanzweifel/git-auto-commit-action](https://github.com/stefanzweifel/git-auto-commit-action) | `7.2.0` | `7.2.1` |

Updates `actions/setup-java` from 6.0.1 to 6.2.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/setup-java/releases">actions/setup-java's releases</a>.</em></p>
<blockquote>
<h2>v6.2.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Fix Liberica SDKMAN patch release resolution by <a href="https://github.com/brunoborges"><code>@​brunoborges</code></a> in <a href="">actions/setup-java#1291</a></li>
<li>Update Undici to 6.29.1 by <a href="https://github.com/brunoborges"><code>@​brunoborges</code></a> in <a href="">actions/setup-java#1308</a></li>
<li>chore(deps): bump the monthly-npm-updates group with 12 updates by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">actions/setup-java#1309</a></li>
<li>Fix Liberica Java 25 release resolution by <a href="https://github.com/brunoborges"><code>@​brunoborges</code></a> in <a href="">actions/setup-java#1313</a></li>
<li>Add repository-specific Copilot instructions by <a href="https://github.com/brunoborges"><code>@​brunoborges</code></a> in <a href="">actions/setup-java#1312</a></li>
<li>Support exact Corretto release versions by <a href="https://github.com/electrum"><code>@​electrum</code></a> in <a href="">actions/setup-java#1310</a></li>
<li>Support Maven mirrors in generated settings.xml by <a href="https://github.com/brunoborges"><code>@​brunoborges</code></a> in <a href="">actions/setup-java#1289</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/electrum"><code>@​electrum</code></a> made their first contribution in <a href="">actions/setup-java#1310</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/setup-java/compare/v6.1.0...v6.2.0">https://github.com/actions/setup-java/compare/v6.1.0...v6.2.0</a></p>
<h2>v6.1.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Preserve compound Liberica build versions from .sdkmanrc by <a href="https://github.com/brunoborges"><code>@​brunoborges</code></a> with <a href="https://github.com/Copilot"><code>@​Copilot</code></a> in <a href="">actions/setup-java#1268</a></li>
<li>Support Temurin on Linux RISC-V by <a href="https://github.com/yawkat"><code>@​yawkat</code></a> in <a href="">actions/setup-java#1269</a></li>
<li>Stop GPG agent before removing signature-verification home by <a href="https://github.com/brunoborges"><code>@​brunoborges</code></a> with <a href="https://github.com/Copilot"><code>@​Copilot</code></a> in <a href="">actions/setup-java#1273</a></li>
<li>Prefer Zulu 4-segment hotfix builds when resolving version ranges by <a href="https://github.com/brunoborges"><code>@​brunoborges</code></a> in <a href="">actions/setup-java#1278</a></li>
<li>Support Temurin JEP 322 patch versions like 26.0.2.1+1 by <a href="https://github.com/brunoborges"><code>@​brunoborges</code></a> in <a href="">actions/setup-java#1279</a></li>
<li>chore(deps): bump undici from 6.28.0 to 6.29.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">actions/setup-java#1274</a></li>
<li>chore(deps): bump the monthly-npm-updates group with 13 updates by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">actions/setup-java#1276</a></li>
<li>feat: support Maven server credential origins by <a href="https://github.com/YunaBraska"><code>@​YunaBraska</code></a> in <a href="">actions/setup-java#1282</a></li>
<li>Support Maven plugin repositories in generated settings.xml by <a href="https://github.com/brunoborges"><code>@​brunoborges</code></a> in <a href="">actions/setup-java#1286</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/yawkat"><code>@​yawkat</code></a> made their first contribution in <a href="">actions/setup-java#1269</a></li>
<li><a href="https://github.com/YunaBraska"><code>@​YunaBraska</code></a> made their first contribution in <a href="">actions/setup-java#1282</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/setup-java/compare/v6.0.1...v6.1.0">https://github.com/actions/setup-java/compare/v6.0.1...v6.1.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>77dd5b2</code></a> Support Maven mirrors in generated settings.xml (<a href="">#1289</a>)</li>
<li><a href=""><code>644a850</code></a> Support exact Corretto release versions (<a href="">#1310</a>)</li>
<li><a href=""><code>dade0c5</code></a> Save uncommitted changes (<a href="">#1312</a>)</li>
<li><a href=""><code>ef0b922</code></a> Fix Liberica Java 25 release resolution (<a href="">#1313</a>)</li>
<li><a href=""><code>e144521</code></a> chore(deps): bump the monthly-npm-updates group with 12 updates (<a href="">#1309</a>)</li>
<li><a href=""><code>8cd57eb</code></a> Update Undici to 6.29.1 (<a href="">#1308</a>)</li>
<li><a href=""><code>816722a</code></a> Fix Liberica SDKMAN patch release resolution (<a href="">#1291</a>)</li>
<li><a href=""><code>b843ebf</code></a> Support Maven plugin repositories in generated settings.xml (<a href="">#1286</a>)</li>
<li><a href=""><code>2a69be2</code></a> feat: support Maven server credential origins (<a href="">#1282</a>)</li>
<li><a href=""><code>d0e6e4d</code></a> chore(deps): bump the monthly-npm-updates group with 13 updates (<a href="">#1276</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/actions/setup-java/compare/de7274f081f381c8f8158605e0321c36c376e2e6...77dd5b2ce225ea11469928ac317850245a74ae78">compare view</a></li>
</ul>
</details>
<br />

Updates `actions/upload-artifact` from 7.0.1 to 7.0.2
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/upload-artifact/releases">actions/upload-artifact's releases</a>.</em></p>
<blockquote>
<h2>v7.0.2</h2>
<h2>What's Changed</h2>
<ul>
<li>Improves artifact download retries when the service returns HTTP 429 (rate limiting), including honoring valid Retry-After headers.</li>
<li>Updates <code>@​actions/artifact</code> to v6.3.1.</li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/tunc-d"><code>@​tunc-d</code></a> made their first contribution in <a href="">actions/upload-artifact#821</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/upload-artifact/compare/v7.0.1...v7.0.2">https://github.com/actions/upload-artifact/compare/v7.0.1...v7.0.2</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>cf430e0</code></a> Merge pull request <a href="">#822</a> from actions/tunc-d-prepare-upload-v7-0-2</li>
<li><a href=""><code>c2acded</code></a> chore: prepare v7.0.2 release</li>
<li><a href=""><code>4687c1b</code></a> Merge pull request <a href="">#821</a> from actions/tunc-d-upload-artifact-package-bump</li>
<li><a href=""><code>8cbe1be</code></a> Bump <code>@​actions/artifact</code> to 6.3.1</li>
<li>See full diff in <a href="https://github.com/actions/upload-artifact/compare/043fb46d1a93c77aae656e7c1c64a875d1fc6a0a...cf430e030ddbb5b0abf93d22962f4752f3646cd9">compare view</a></li>
</ul>
</details>
<br />

Updates `actions/download-artifact` from 8.0.1 to 8.0.2
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/download-artifact/releases">actions/download-artifact's releases</a>.</em></p>
<blockquote>
<h2>v8.0.2</h2>
<h2>What's Changed</h2>
<ul>
<li>Update the readme by <a href="https://github.com/danwkennedy"><code>@​danwkennedy</code></a> in <a href="">actions/download-artifact#473</a></li>
<li>Improves artifact download retries when the service returns HTTP 429 (rate limiting), including honoring valid Retry-After headers.</li>
<li>Update <code>@​actions/artifact</code> to 6.3.1 by <a href="https://github.com/tunc-d"><code>@​tunc-d</code></a> in <a href="">actions/download-artifact#492</a></li>
<li>Prepare download-artifact v8.0.2 by <a href="https://github.com/tunc-d"><code>@​tunc-d</code></a> in <a href="">actions/download-artifact#493</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/tunc-d"><code>@​tunc-d</code></a> made their first contribution in <a href="">actions/download-artifact#492</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/download-artifact/compare/v8.0.1...v8.0.2">https://github.com/actions/download-artifact/compare/v8.0.1...v8.0.2</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9000827</code></a> Merge pull request <a href="">#493</a> from actions/tunc-d-prepare-download-v8-0-2</li>
<li><a href=""><code>e455989</code></a> Prepare download-artifact v8.0.2</li>
<li><a href=""><code>a00b90c</code></a> Merge pull request <a href="">#492</a> from actions/tunc-d-download-artifact-package-bump</li>
<li><a href=""><code>29bb7ce</code></a> Update <code>@​actions/artifact</code> to 6.3.1</li>
<li><a href=""><code>484a0b5</code></a> Update the readme (<a href="">#473</a>)</li>
<li>See full diff in <a href="https://github.com/actions/download-artifact/compare/3e5f45b2cfb9172054b4087a40e8e0b5a5461e7c...9000827ccba6bdab643e8b6fd33ac0654aef8333">compare view</a></li>
</ul>
</details>
<br />

Updates `apple-actions/import-codesign-certs` from 7.0.0 to 7.2.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/apple-actions/import-codesign-certs/releases">apple-actions/import-codesign-certs's releases</a>.</em></p>
<blockquote>
<h2>v7.2.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Add actionlint and zizmor by <a href="https://github.com/daveisfera"><code>@​daveisfera</code></a> in <a href="">Apple-Actions/import-codesign-certs#219</a></li>
<li>Bump knip from 6.38.0 to 6.39.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#217</a></li>
<li>Bump eslint from 10.9.1 to 10.12.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#216</a></li>
<li>Bump <code>@​types/node</code> from 26.1.2 to 26.6.4 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#218</a></li>
<li>Add security argv unit tests by <a href="https://github.com/daveisfera"><code>@​daveisfera</code></a> in <a href="">Apple-Actions/import-codesign-certs#227</a></li>
<li>Bump actions/setup-node from 7.0.0 to 7.1.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#220</a></li>
<li>Bump actions/upload-artifact from 7.0.1 to 7.0.2 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#221</a></li>
<li>Bump zizmorcore/zizmor-action from 0.6.4 to 0.7.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#222</a></li>
<li>Bump eslint from 10.12.0 to 10.13.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#223</a></li>
<li>Bump prettier from 3.9.9 to 3.9.10 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#224</a></li>
<li>Bump vitest from 5.0.3 to 5.0.5 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#225</a></li>
<li>Bump knip from 6.39.0 to 6.42.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#226</a></li>
<li>Rebuild dist/ on Dependabot npm PRs by <a href="https://github.com/daveisfera"><code>@​daveisfera</code></a> in <a href="">Apple-Actions/import-codesign-certs#229</a></li>
<li>Bump undici from 6.29.0 to 6.29.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#228</a></li>
<li>Standardize dist generation on the shared esbuild setup by <a href="https://github.com/daveisfera"><code>@​daveisfera</code></a> in <a href="">Apple-Actions/import-codesign-certs#230</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/Apple-Actions/import-codesign-certs/compare/v7.1.0...v7.2.0">https://github.com/Apple-Actions/import-codesign-certs/compare/v7.1.0...v7.2.0</a></p>
<h2>v7.1.0</h2>
<h2>What's Changed</h2>
<ul>
<li>New <code>identities</code> output: a JSON array of <code>{&quot;hash&quot;, &quot;name&quot;}</code> for each valid code-signing identity, so you can sign by hash when a renewed certificate has the same name as the old one</li>
<li>Bump actions/upload-artifact from 7.0.0 to 7.0.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#174</a></li>
<li>Bump actions/setup-node from 6.3.0 to 6.4.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#175</a></li>
<li>Bump <code>@​types/node</code> from 24.9.2 to 25.5.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#170</a></li>
<li>Bump actions/checkout from 6.0.2 to 6.0.3 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#184</a></li>
<li>Bump <code>@​types/node</code> from 25.6.0 to 25.9.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#180</a></li>
<li>Bump knip from 6.5.0 to 6.15.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#183</a></li>
<li>Bump <code>@​actions/core</code> from 3.0.0 to 3.0.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#178</a></li>
<li>Bump esbuild from 0.28.0 to 0.28.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#186</a></li>
<li>Bump actions/checkout from 6.0.3 to 7.0.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#187</a></li>
<li>Bump prettier from 3.8.4 to 3.9.4 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#189</a></li>
<li>Bump knip from 6.15.0 to 6.23.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#191</a></li>
<li>Bump actions/setup-node from 6.4.0 to 7.0.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#193</a></li>
<li>Bump eslint-plugin-github from 6.0.0 to 6.1.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#199</a></li>
<li>Bump knip from 6.23.0 to 6.31.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#198</a></li>
<li>Bump actions/checkout from 7.0.0 to 7.0.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#194</a></li>
<li>Bump <code>@​types/node</code> from 25.9.5 to 26.1.2 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#195</a></li>
<li>Bump prettier from 3.9.5 to 3.9.6 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#196</a></li>
<li>Bump eslint from 9.39.5 to 10.8.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#197</a></li>
<li>Bump undici from 6.27.0 to 6.28.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#200</a></li>
<li>Bump js-yaml from 4.3.0 to 4.3.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#201</a></li>
<li>Bump eslint from 10.8.0 to 10.9.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#202</a></li>
<li>Bump browserslist from 4.28.6 to 4.28.8 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#207</a></li>
<li>Bump esbuild from 0.28.1 to 0.28.2 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#204</a></li>
<li>Bump knip from 6.31.0 to 6.33.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#205</a></li>
<li>Bump typescript from 6.0.3 to 7.0.2 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#206</a></li>
<li>Bump eslint-plugin-github from 6.1.1 to 6.1.2 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">Apple-Actions/import-codesign-certs#203</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>288b8ec</code></a> Merge pull request <a href="">#230</a> from Apple-Actions/ci/standardize-dist</li>
<li><a href=""><code>8f9f13d</code></a> [standardize-dist] Standardize dist generation on the shared esbuild setup.</li>
<li><a href=""><code>74ff53b</code></a> [main] Approve Dependabot PRs with GITHUB_TOKEN, merge with PAT.</li>
<li><a href=""><code>5d87793</code></a> [main] Merge Dependabot PRs with DEPENDABOT_DIST_TOKEN.</li>
<li><a href=""><code>192cf72</code></a> [main] Land green Actions Dependabot PRs via merge API.</li>
<li><a href=""><code>888a446</code></a> [main] Remove duplicates and fix dist</li>
<li><a href=""><code>ae14493</code></a> [main] Merge remote-tracking branch 'origin/dependabot/npm_and_yarn/undici-6....</li>
<li><a href=""><code>8e2e88b</code></a> Merge pull request <a href="">#229</a> from Apple-Actions/ci/rebuild-dependabot-dist</li>
<li><a href=""><code>3729d5b</code></a> [rebuild-dependabot-dist] Rebuild dist/ on Dependabot npm PRs with DEPENDABOT...</li>
<li><a href=""><code>1a2c6ba</code></a> [main] Merge origin/main into release workflow fix</li>
<li>Additional commits viewable in <a href="https://github.com/apple-actions/import-codesign-certs/compare/5142e029c445c10ffc7149d172e540235a065466...288b8ec97b82c66b6f2a6baaf7acc8dfbcbe331c">compare view</a></li>
</ul>
</details>
<br />

Updates `stefanzweifel/git-auto-commit-action` from 7.2.0 to 7.2.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/stefanzweifel/git-auto-commit-action/releases">stefanzweifel/git-auto-commit-action's releases</a>.</em></p>
<blockquote>
<h2>v7.2.1</h2>
<h2>Fixed</h2>
<ul>
<li>Accept repositories where .git is a file (<a href="">#417</a>) <a href="https://github.com/@stefanzweifel"><code>@​stefanzweifel</code></a></li>
<li>README: Update actions (<a href="">#413</a>) <a href="https://github.com/@jackbayliss"><code>@​jackbayliss</code></a></li>
<li>Remove unused gitStatusMessage variable in the entrypoint (<a href="">#415</a>) <a href="https://github.com/@ChihweiLHBird"><code>@​ChihweiLHBird</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/stefanzweifel/git-auto-commit-action/blob/master/CHANGELOG.md">stefanzweifel/git-auto-commit-action's changelog</a>.</em></p>
<blockquote>
<h1>Changelog</h1>
<p>All notable changes to this project will be documented in this file.</p>
<p>The format is based on <a href="http://keepachangelog.com/en/1.0.0/">Keep a Changelog</a>
and this project adheres to <a href="http://semver.org/spec/v2.0.0.html">Semantic Versioning</a>.</p>
<h2><a href="https://github.com/stefanzweifel/git-auto-commit-action/compare/v7.2.1...HEAD">Unreleased</a></h2>
<blockquote>
<p>TBD</p>
</blockquote>
<h2><a href="https://github.com/stefanzweifel/git-auto-commit-action/compare/v7.2.0...v7.2.1">v7.2.1</a> - 2026-10-22</h2>
<h3>Fixed</h3>
<ul>
<li>Accept repositories where .git is a file (<a href="">#417</a>) <a href="https://github.com/@stefanzweifel"><code>@​stefanzweifel</code></a></li>
<li>README: Update actions (<a href="">#413</a>) <a href="https://github.com/@jackbayliss"><code>@​jackbayliss</code></a></li>
<li>Remove unused gitStatusMessage variable in the entrypoint (<a href="">#415</a>) <a href="https://github.com/@ChihweiLHBird"><code>@​ChihweiLHBird</code></a></li>
</ul>
<h2><a href="https://github.com/stefanzweifel/git-auto-commit-action/compare/v7.1.0...v7.2.0">v7.2.0</a> - 2026-06-28</h2>
<h3>Added</h3>
<ul>
<li>Add hooks to run shell snippets around git operations (<a href="">#411</a>) <a href="https://github.com/@stefanzweifel"><code>@​stefanzweifel</code></a></li>
<li>Emit warning for pull_request_target trigger usage (<a href="">#410</a>) <a href="https://github.com/@stefanzweifel"><code>@​stefanzweifel</code></a></li>
</ul>
<h3>Fixed</h3>
<ul>
<li>docs(action): fix input and output descriptions in action.yml (<a href="">#406</a>) <a href="https://github.com/@kranthipoturaju"><code>@​kranthipoturaju</code></a></li>
<li>docs: fix typos, grammar, and formatting across markdown files (<a href="">#408</a>) <a href="https://github.com/@kranthipoturaju"><code>@​kranthipoturaju</code></a></li>
<li>docs: fix broken and redirecting URLs in README.md (<a href="">#407</a>) <a href="https://github.com/@kranthipoturaju"><code>@​kranthipoturaju</code></a></li>
<li>README: clearify meaning of the repository field (<a href="">#404</a>) <a href="https://github.com/@gucio321"><code>@​gucio321</code></a></li>
</ul>
<h3>Dependency Updates</h3>
<ul>
<li>Bump actions/checkout from 6 to 7 (<a href="">#409</a>) [@<a href="https://github.com/apps/dependabot">dependabot[bot]</a>](<a href="https://github.com/@%5Bdependabot%5Bbot%5D%5D(https://github.com/apps/dependabot)">https://github.com/@[dependabot[bot]](https://github.com/apps/dependabot)</a>)</li>
<li>Bump release-drafter/release-drafter from 6 to 7 (<a href="">#403</a>) [@<a href="https://github.com/apps/dependabot">dependabot[bot]</a>](<a href="https://github.com/@%5Bdependabot%5Bbot%5D%5D(https://github.com/apps/dependabot)">https://github.com/@[dependabot[bot]](https://github.com/apps/dependabot)</a>)</li>
</ul>
<h2><a href="https://github.com/stefanzweifel/git-auto-commit-action/compare/v7.0.0...v7.1.0">v7.1.0</a> - 2025-12-17</h2>
<h3>Added</h3>
<ul>
<li>Add skip_push input option (<a href="">#401</a>) <a href="https://github.com/@kvanzuijlen"><code>@​kvanzuijlen</code></a></li>
</ul>
<h3>Changes</h3>
<ul>
<li>docs: fix typo in README.md (<a href="">#400</a>) <a href="https://github.com/@GideonBear"><code>@​GideonBear</code></a></li>
</ul>
<h3>Dependency Updates</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>d0b0110</code></a> Accept repositories where .git is a file (<a href="">#417</a>)</li>
<li><a href=""><code>9264814</code></a> Remove unused gitStatusMessage variable in the entrypoint (<a href="">#415</a>)</li>
<li><a href=""><code>4b4693c</code></a> README: Update actions (<a href="">#413</a>)</li>
<li><a href=""><code>53ee9ba</code></a> Update CHANGELOG</li>
<li>See full diff in <a href="https://github.com/stefanzweifel/git-auto-commit-action/compare/4a55954c782fc1ea30b9056cd3e7a2b40ca8887d...d0b01107b5db882071f96de5dd4b54961ea93f4c">compare view</a></li>
</ul>
</details>
<br />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b6acbbc8dfce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.