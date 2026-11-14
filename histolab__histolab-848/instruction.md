# Issue

**Title:** build(deps): bump openslide-bin from 4.0.0.13 to 4.0.1.1

## Description

> [!WARNING]
> Dependabot will stop supporting `python v3.9`!
>
> Please upgrade to one of the following versions: `v3.9`, `v3.10`, `v3.11`, `v3.12`, `v3.13`, or `v3.14`.
>

Bumps [openslide-bin](https://github.com/openslide/openslide-bin) from 4.0.0.13 to 4.0.1.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/openslide/openslide-bin/releases">openslide-bin's releases</a>.</em></p>
<blockquote>
<h2>openslide-bin 4.0.1.1</h2>
<h2>Changes</h2>
<ul>
<li>Update OpenSlide to 4.0.1</li>
</ul>
<h2>Versions</h2>
<table>
<thead>
<tr>
<th>Software</th>
<th>Version</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>OpenSlide</strong></td>
<td><strong>4.0.1</strong></td>
</tr>
<tr>
<td>cairo</td>
<td>1.18.4-2</td>
</tr>
<tr>
<td>glib</td>
<td>2.88.1-1</td>
</tr>
<tr>
<td>libdicom</td>
<td>1.3.0-1</td>
</tr>
<tr>
<td>libffi</td>
<td>3.5.2-2</td>
</tr>
<tr>
<td>libjpeg-turbo</td>
<td>3.1.4.1-2</td>
</tr>
<tr>
<td>libpng</td>
<td>1.6.58-1</td>
</tr>
<tr>
<td>libtiff</td>
<td>4.7.1-4</td>
</tr>
<tr>
<td>libxml2</td>
<td>2.15.3-1</td>
</tr>
<tr>
<td>OpenJPEG</td>
<td>2.5.4-1</td>
</tr>
<tr>
<td>PCRE2</td>
<td>10.47-3</td>
</tr>
<tr>
<td>pixman</td>
<td>0.46.4-1</td>
</tr>
<tr>
<td>proxy-libintl</td>
<td>0.5-1</td>
</tr>
<tr>
<td>SQLite</td>
<td>3.53.2-1</td>
</tr>
<tr>
<td>uthash</td>
<td>2.3.0-2</td>
</tr>
<tr>
<td>zlib-ng</td>
<td>2.3.3-1</td>
</tr>
<tr>
<td>Zstandard</td>
<td>1.5.7-3</td>
</tr>
<tr>
<td><em>[Linux] Binutils</em></td>
<td><em>GNU ld version 2.30-128.el8_10</em></td>
</tr>
<tr>
<td><em>[Linux] GCC</em></td>
<td><em>(GCC) 8.5.0 20210514 (Red Hat 8.5.0-28)</em></td>
</tr>
<tr>
<td><em>[macOS] Clang</em></td>
<td><em>17.0.0 (clang-1700.0.13.5)</em></td>
</tr>
<tr>
<td><em>[Windows] Binutils</em></td>
<td><em>GNU ld (Gentoo 2.46.0 p1) 2.46.0</em></td>
</tr>
<tr>
<td><em>[Windows] GCC</em></td>
<td><em>(Gentoo 16.1.0 p1) 16.1.0</em></td>
</tr>
<tr>
<td><em>[Windows] MinGW-w64</em></td>
<td><em>14.0.0</em></td>
</tr>
</tbody>
</table>
<h2>openslide-bin 4.0.0.14</h2>
<h2>Changes</h2>
<ul>
<li>Fix arbitrary memory write with crafted Ventana BIF file (<a href="https://github.com/openslide/openslide/security/advisories/GHSA-mxg2-48g7-fmwc">CVE-2026-48977</a>)</li>
<li>Update various dependencies</li>
</ul>
<h2>Versions</h2>
<table>
<thead>
<tr>
<th>Software</th>
<th>Version</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>OpenSlide</strong></td>
<td><strong>4.0.0</strong></td>
</tr>
<tr>
<td>cairo</td>
<td>1.18.4-2</td>
</tr>
<tr>
<td>gdk-pixbuf</td>
<td>2.44.6-1</td>
</tr>
<tr>
<td>glib</td>
<td>2.88.1-1</td>
</tr>
<tr>
<td>libdicom</td>
<td>1.3.0-1</td>
</tr>
</tbody>
</table>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/openslide/openslide-bin/blob/main/CHANGELOG.md">openslide-bin's changelog</a>.</em></p>
<blockquote>
<h2>Version 4.0.1.1, 2026-06-07</h2>
<ul>
<li>Update OpenSlide to 4.0.1</li>
</ul>
<h2>Version 4.0.0.14, 2026-06-07</h2>
<ul>
<li>Fix arbitrary memory write with crafted Ventana BIF file (CVE-2026-48977)</li>
<li>Update various dependencies</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>879a732</code></a> Merge pull request <a href="">#471</a> from bgilbert/release</li>
<li><a href=""><code>f2a3e32</code></a> OpenSlide 4.0.1</li>
<li><a href=""><code>220b4d6</code></a> Drop gdk-pixbuf</li>
<li><a href=""><code>de8fcf8</code></a> Include zstd in stable builds</li>
<li><a href=""><code>40ffb08</code></a> Merge pull request <a href="">#469</a> from bgilbert/ventana</li>
<li><a href=""><code>3505a78</code></a> openslide-bin 4.0.0.14</li>
<li><a href=""><code>ec27e7c</code></a> Merge pull request <a href="">#467</a> from bgilbert/libdicom</li>
<li><a href=""><code>d410629</code></a> Revert &quot;workflows: disable werror on PR CI to break dependency cycle&quot;</li>
<li><a href=""><code>7101772</code></a> Merge pull request <a href="">#466</a> from bgilbert/libdicom</li>
<li><a href=""><code>689b773</code></a> workflows: disable werror on PR CI to break dependency cycle</li>
<li>Additional commits viewable in <a href="https://github.com/openslide/openslide-bin/compare/v4.0.0.13...v4.0.1.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=openslide-bin&package-manager=pip&previous-version=4.0.0.13&new-version=4.0.1.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `518029bc3649`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.