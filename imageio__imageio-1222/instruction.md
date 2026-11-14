# Issue

**Title:** Bump multidict from 6.7.1 to 6.9.1

## Description

Bumps [multidict](https://github.com/aio-libs/multidict) from 6.7.1 to 6.9.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/aio-libs/multidict/releases">multidict's releases</a>.</em></p>
<blockquote>
<h2>6.9.1</h2>
<h2>Bug fixes</h2>
<ul>
<li>
<p>Fixed the C extension reading freed memory on free-threaded builds when a
list handed to :py:meth:<code>~multidict.MultiDict.update</code>,
:py:meth:<code>~multidict.MultiDict.extend</code>, :py:meth:<code>~multidict.MultiDict.merge</code>
or the :py:class:<code>~multidict.MultiDict</code> and :py:class:<code>~multidict.CIMultiDict</code>
constructors, a <code>[key, value]</code> item inside any iterable handed to them, or a
list tested with <code>in</code> against :py:meth:<code>~multidict.MultiDict.items</code>, is
changed by another thread; a call that catches the list shrinking under it
now raises :py:exc:<code>RuntimeError</code> -- by :user:<code>rodrigobnogueira</code>.</p>
<p><em>Related issues and pull requests on GitHub:</em>
<a href="">#1437</a>.</p>
</li>
<li>
<p>Fixed a data race on the free-threaded build where a retired hash table's
reader count used relaxed atomics, letting a lock-free <code>get()</code>/<code>getone()</code>/
<code>__getitem__()</code> read race a concurrent free of that table. The reader-exit
decrement and the drain's free check now use release/acquire ordering
instead -- by :user:<code>asvetlov</code>.</p>
<p><em>Related issues and pull requests on GitHub:</em>
<a href="">#1481</a>.</p>
</li>
<li>
<p>Fixed a free-threaded build bug where two threads calling <code>update()</code>,
<code>merge()</code>, or <code>__setitem__()</code> on the same key at the same time could lose
the key entirely instead of just racing on which value wins. A decref of the
replaced value could transiently suspend the writer's critical section,
letting a second writer for the same key observe the first writer's
in-progress entry as absent and, once both settled, mistake it for a stale
duplicate and delete it. Every such decref is now deferred until the writer
has released its critical section, so the window can no longer open.
<code>setdefault()</code> had an unrelated instance of the same blind spot (it could
insert a duplicate rather than recognizing an in-flight key), fixed alongside
it -- by :user:<code>asvetlov</code>.</p>
<p><em>Related issues and pull requests on GitHub:</em>
<a href="">#1483</a>.</p>
</li>
<li>
<p>Fixed a free-threaded build bug where <code>getall()</code> and the <code>items()</code>/
<code>keys()</code>/<code>values()</code> equality path could raise <code>KeyError</code> or report a
present, never-deleted key as missing. A concurrent <code>update()</code>/<code>extend()</code>/
<code>__setitem__()</code> call can have its critical section transiently suspended
(a decref triggering a blocking allocator call) while an entry is marked as
part of its own bookkeeping; a reader landing in that window used to treat
the mark as &quot;not found&quot; instead of &quot;still there, in flight&quot; -- by
:user:<code>asvetlov</code>.</p>
<p><em>Related issues and pull requests on GitHub:</em></p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/aio-libs/multidict/blob/master/CHANGES.rst">multidict's changelog</a>.</em></p>
<blockquote>
<h1>6.9.1</h1>
<p><em>(2026-09-21)</em></p>
<h2>Bug fixes</h2>
<ul>
<li>
<p>Fixed the C extension reading freed memory on free-threaded builds when a
list handed to :py:meth:<code>~multidict.MultiDict.update</code>,
:py:meth:<code>~multidict.MultiDict.extend</code>, :py:meth:<code>~multidict.MultiDict.merge</code>
or the :py:class:<code>~multidict.MultiDict</code> and :py:class:<code>~multidict.CIMultiDict</code>
constructors, a <code>[key, value]</code> item inside any iterable handed to them, or a
list tested with <code>in</code> against :py:meth:<code>~multidict.MultiDict.items</code>, is
changed by another thread; a call that catches the list shrinking under it
now raises :py:exc:<code>RuntimeError</code> -- by :user:<code>rodrigobnogueira</code>.</p>
<p><em>Related issues and pull requests on GitHub:</em>
:issue:<code>1437</code>.</p>
</li>
<li>
<p>Fixed a data race on the free-threaded build where a retired hash table's
reader count used relaxed atomics, letting a lock-free <code>get()</code>/<code>getone()</code>/
<code>__getitem__()</code> read race a concurrent free of that table. The reader-exit
decrement and the drain's free check now use release/acquire ordering
instead -- by :user:<code>asvetlov</code>.</p>
<p><em>Related issues and pull requests on GitHub:</em>
:issue:<code>1481</code>.</p>
</li>
<li>
<p>Fixed a free-threaded build bug where two threads calling <code>update()</code>,
<code>merge()</code>, or <code>__setitem__()</code> on the same key at the same time could lose
the key entirely instead of just racing on which value wins. A decref of the
replaced value could transiently suspend the writer's critical section,
letting a second writer for the same key observe the first writer's
in-progress entry as absent and, once both settled, mistake it for a stale
duplicate and delete it. Every such decref is now deferred until the writer
has released its critical section, so the window can no longer open.
<code>setdefault()</code> had an unrelated instance of the same blind spot (it could
insert a duplicate rather than recognizing an in-flight key), fixed alongside
it -- by :user:<code>asvetlov</code>.</p>
<p><em>Related issues and pull requests on GitHub:</em>
:issue:<code>1483</code>.</p>
</li>
<li>
<p>Fixed a free-threaded build bug where <code>getall()</code> and the <code>items()</code>/
<code>keys()</code>/<code>values()</code> equality path could raise <code>KeyError</code> or report a
present, never-deleted key as missing. A concurrent <code>update()</code>/<code>extend()</code>/
<code>__setitem__()</code> call can have its critical section transiently suspended
(a decref triggering a blocking allocator call) while an entry is marked as</p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>0a1770c</code></a> Release 6.9.1 (<a href="">#1504</a>)</li>
<li><a href=""><code>d220522</code></a> Upload release assets one at a time to avoid the secondary rate limit (<a href="">#1503</a>)</li>
<li><a href=""><code>30cd596</code></a> Stop a GIL-releasing <strong>del</strong> from segfaulting the standard C extension build ...</li>
<li><a href=""><code>d1c331a</code></a> Recheck the reader gate after taking the retired list (<a href="">#1502</a>)</li>
<li><a href=""><code>b37f07c</code></a> Allocate deferred decrefs in fixed-size blocks (<a href="">#1501</a>)</li>
<li><a href=""><code>563f667</code></a> Run CodSpeed benchmarks on Python 3.14 and loop the smallest ones (<a href="">#1498</a>)</li>
<li><a href=""><code>157c87c</code></a> Cancel superseded CI runs on pull requests (<a href="">#1500</a>)</li>
<li><a href=""><code>d43adfe</code></a> Drop -I from the ASan test command so PYTHONMALLOC takes effect (<a href="">#1499</a>)</li>
<li><a href=""><code>2a68472</code></a> Stop items() iteration from reading a freed entry in CIMultiDict (<a href="">#1496</a>)</li>
<li><a href=""><code>cd528d6</code></a> Rename GHSA-54p9-h82j-f925 changelog fragment to the merged commit (<a href="">#1495</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/aio-libs/multidict/compare/v6.7.1...v6.9.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=multidict&package-manager=uv&previous-version=6.7.1&new-version=6.9.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/imageio/imageio/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1c83326f1648`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.