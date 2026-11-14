# Issue

**Title:** Bump org.json:json from 20231013 to 20260719 in /components/formats-bsd

## Description

Bumps [org.json:json](https://github.com/douglascrockford/JSON-java) from 20231013 to 20260719.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/douglascrockford/JSON-java/releases">org.json:json's releases</a>.</em></p>
<blockquote>
<h2>20260719</h2>
<table>
<thead>
<tr>
<th>Pull Request</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="">#1069</a></td>
<td>pre-release-20260719 prep for next release</td>
</tr>
<tr>
<td><a href="">#1068</a></td>
<td>Max number length config for BigInteger and BigDecimal</td>
</tr>
<tr>
<td><a href="">#1067</a></td>
<td>bound BigDecimal→BigInteger expansion in objectToBigInteger (completes CVE-2026-59171 fix)</td>
</tr>
<tr>
<td><a href="">#1065</a></td>
<td>Fixes CVE-2026-59171</td>
</tr>
<tr>
<td><a href="">#1062</a></td>
<td>Refactor CDL row serialization for readability</td>
</tr>
<tr>
<td><a href="">#1061</a></td>
<td>Restore lenient jsonarray allow consecutive commas and insert null</td>
</tr>
<tr>
<td><a href="">#1058</a></td>
<td>Docs and warnings cleanup</td>
</tr>
</tbody>
</table>
<h2>20260522</h2>
<table>
<thead>
<tr>
<th>Pull Request</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="">#1054</a></td>
<td>pre-release-20260522 prep for next release</td>
</tr>
<tr>
<td><a href="">#1053</a></td>
<td>update security.md with key data</td>
</tr>
<tr>
<td><a href="">#1046</a></td>
<td>Validate XML numeric character references before string construction</td>
</tr>
<tr>
<td><a href="">#1044</a></td>
<td>Ignore static fields in JSONObject.fromJson()</td>
</tr>
<tr>
<td><a href="">#1041</a></td>
<td>Enhance README with license clarification</td>
</tr>
<tr>
<td><a href="">#1039</a></td>
<td>Fix XML forceList parsing issue</td>
</tr>
<tr>
<td><a href="">#1038</a></td>
<td>Fix input validation in XMLTokener.unescapeEntity()</td>
</tr>
<tr>
<td><a href="">#1037</a></td>
<td>Fix ClassCastException in JSONML.toJSONArray and toJSONObject</td>
</tr>
<tr>
<td><a href="">#1029</a></td>
<td>add badge to external hosted javadoc</td>
</tr>
<tr>
<td><a href="">#1028</a></td>
<td>Refactoring: Fix sonarqube reliability issues</td>
</tr>
<tr>
<td><a href="">#1027</a></td>
<td>Save/restore default locale in test</td>
</tr>
</tbody>
</table>
<h2>20251224</h2>
<table>
<thead>
<tr>
<th>Pull Request</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="">#1021</a></td>
<td>Add LTS JDK 25 build to github actions</td>
</tr>
<tr>
<td><a href="">#1020</a></td>
<td>Record type support</td>
</tr>
<tr>
<td><a href="">#1017</a></td>
<td>Refactoring: Fix some SonarQube issues</td>
</tr>
<tr>
<td><a href="">#1014</a></td>
<td>Refactoring: String check logic in CDL</td>
</tr>
<tr>
<td><a href="">#1013</a></td>
<td>Refactoring: FIx Sonarqube issues in JSONArray</td>
</tr>
<tr>
<td><a href="">#1011</a></td>
<td>Refactoring: Fix SonarQube issues in JSONObject</td>
</tr>
<tr>
<td><a href="">#1009</a></td>
<td>Fix strict mode check for period after number</td>
</tr>
<tr>
<td><a href="">#1008</a></td>
<td>Fixed JSONArray strict mode check for leading comma</td>
</tr>
<tr>
<td><a href="">#1006</a></td>
<td>JSONObject.fromJson() with unit tests</td>
</tr>
<tr>
<td><a href="">#1005</a></td>
<td>Refactoring: Fix sonarQube issues in JSONObject</td>
</tr>
<tr>
<td><a href="">#1004</a></td>
<td>Refactoring: Fix sonarcube issues in JSONObject</td>
</tr>
<tr>
<td><a href="">#1001</a></td>
<td>Refactoring: sonarqube issues in JSONObject</td>
</tr>
<tr>
<td><a href="">#1000</a></td>
<td>Refactoring: Fix some sonarcube issues from recent commits</td>
</tr>
<tr>
<td><a href="">#999</a></td>
<td>fixed some strict mode issues</td>
</tr>
<tr>
<td><a href="">#995</a></td>
<td>Fix regression XML parsing null with keepStrings</td>
</tr>
<tr>
<td><a href="">#994</a></td>
<td>Add Jacoco option to build, restore method check in populateMap()</td>
</tr>
<tr>
<td><a href="">#993</a></td>
<td>Added JUnit tests for XMLTokenerTest</td>
</tr>
<tr>
<td><a href="">#992</a></td>
<td>Added JUnit test cases for HTTPTokener</td>
</tr>
<tr>
<td><a href="">#991</a></td>
<td>update CodeQL to v3</td>
</tr>
<tr>
<td><a href="">#990</a></td>
<td>Refactoring: fix SonarQube issues in populateMap()</td>
</tr>
</tbody>
</table>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/stleary/JSON-java/blob/master/docs/RELEASES.md">org.json:json's changelog</a>.</em></p>
<blockquote>
<p>20260719    Fixes CVE-2026-59171 very large BigInteger, BigDecimal</p>
<p>20260522    Publish key data, recent commits for minor fixes</p>
<p>20251224    Records, fromJson(), and recent commits</p>
<p>20250517    Strict mode hardening and recent commits</p>
<p>20250107    Restore moditect in pom.xml</p>
<p>20241224    Strict mode opt-in feature, and recent commits. This release does not contain module-info.class.
It is not recommended if you need this feature.</p>
<p>20240303    Revert optLong/getLong changes, and recent commits.</p>
<p>20240205    Recent commits.</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>1795e8c</code></a> Merge pull request <a href="">#1069</a> from stleary/pre-release-20260719</li>
<li><a href=""><code>da757c6</code></a> pre-release-20260719 oops forgot to update new unit tests for strict mode</li>
<li><a href=""><code>d24bc9e</code></a> pre-release-20260719 initial commit</li>
<li><a href=""><code>80efb52</code></a> Merge pull request <a href="">#1068</a> from stleary/max-number-length-config</li>
<li><a href=""><code>9953b76</code></a> max-number-length-config sonarqube fixes</li>
<li><a href=""><code>a28328c</code></a> Merge pull request <a href="">#1067</a> from mechko/1063-biginteger-exponent-dos</li>
<li><a href=""><code>703ac34</code></a> <a href="">#1063</a>: add JSONParserConfiguration overloads for getBigInteger/optBigInteger</li>
<li><a href=""><code>e40d933</code></a> <a href="">#1063</a>: add comment to expected-exception catch block (SonarCloud java:S108)</li>
<li><a href=""><code>fce83c9</code></a> <a href="">#1063</a>: bound BigDecimal-&gt;BigInteger expansion in objectToBigInteger</li>
<li><a href=""><code>90563eb</code></a> 1063-option-3 parserConfig set max len</li>
<li>Additional commits viewable in <a href="https://github.com/douglascrockford/JSON-java/compare/20231013...20260719">compare view</a></li>
</ul>
</details>
<br />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `77833925c46f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.