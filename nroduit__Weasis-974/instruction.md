# Issue

**Title:** build: bump the maven group with 31 updates

## Description

> [!WARNING]
> Cooldown could not be applied because no publication date was available from the registry.
>

Bumps the maven group with 31 updates:

| Package | From | To |
| --- | --- | --- |
| [org.slf4j:slf4j-bom](https://github.com/qos-ch/slf4j) | `2.0.18` | `2.0.20` |
| org.slf4j:slf4j-api | `2.0.18` | `2.0.20` |
| org.apache.felix:org.apache.felix.gogo.runtime | `1.1.6` | `1.2.0` |
| org.weasis.thirdparty:docking-frames | `1.1.7` | `1.1.8` |
| org.apache.felix:org.apache.felix.scr | `2.2.18` | `2.3.0` |
| org.apache.felix:org.apache.felix.configadmin | `1.9.26` | `1.10.0` |
| org.weasis.thirdparty:jaxb-osgi | `4.0.3` | `4.0.9` |
| [org.eclipse.parsson:parsson](https://github.com/eclipse-ee4j/parsson) | `1.1.7` | `1.1.9` |
| [com.github.oshi:oshi-core-ffm](https://github.com/oshi/oshi) | `7.6.0` | `7.7.3` |
| [org.junit:junit-bom](https://github.com/junit-team/junit-framework) | `6.1.2` | `6.1.3` |
| [org.mockito:mockito-bom](https://github.com/mockito/mockito) | `5.23.0` | `5.24.0` |
| [ch.qos.logback:logback-classic](https://github.com/qos-ch/logback) | `1.6.1` | `1.6.6` |
| [ch.qos.logback:logback-core](https://github.com/qos-ch/logback) | `1.6.1` | `1.6.6` |
| [com.formdev:flatlaf](https://github.com/JFormDesigner/FlatLaf) | `3.7.2` | `3.8` |
| [com.formdev:flatlaf-intellij-themes](https://github.com/JFormDesigner/FlatLaf) | `3.7.2` | `3.8` |
| [com.formdev:flatlaf-extras](https://github.com/JFormDesigner/FlatLaf) | `3.7.2` | `3.8` |
| [com.miglayout:miglayout-swing](https://github.com/mikaelgrev/miglayout) | `11.4.3` | `11.5.2` |
| [com.miglayout:miglayout-core](https://github.com/mikaelgrev/miglayout) | `11.4.3` | `11.5.2` |
| [org.apache.maven.plugins:maven-compiler-plugin](https://github.com/apache/maven-compiler-plugin) | `3.15.0` | `3.16.0` |
| [biz.aQute.bnd:bnd-maven-plugin](https://github.com/bndtools/bnd) | `7.3.0` | `7.4.0` |
| [org.apache.maven.plugins:maven-install-plugin](https://github.com/apache/maven-install-plugin) | `3.1.4` | `3.2.0` |
| [org.apache.maven.plugins:maven-deploy-plugin](https://github.com/apache/maven-deploy-plugin) | `3.1.4` | `3.2.0` |
| [org.codehaus.mojo:flatten-maven-plugin](https://github.com/mojohaus/flatten-maven-plugin) | `1.8.0` | `1.9.0` |
| [org.apache.maven.plugins:maven-surefire-plugin](https://github.com/apache/maven-surefire) | `3.5.6` | `3.6.1` |
| [org.apache.maven.plugins:maven-enforcer-plugin](https://github.com/apache/maven-enforcer) | `3.6.3` | `3.7.0` |
| [org.codehaus.mojo:build-helper-maven-plugin](https://github.com/mojohaus/build-helper-maven-plugin) | `3.6.1` | `3.7.0` |
| [com.diffplug.spotless:spotless-maven-plugin](https://github.com/diffplug/spotless) | `3.9.0` | `3.11.0` |
| [org.codehaus.mojo:exec-maven-plugin](https://github.com/mojohaus/exec-maven-plugin) | `3.6.3` | `3.6.4` |
| [org.jacoco:jacoco-maven-plugin](https://github.com/jacoco/jacoco) | `0.8.15` | `0.8.16` |
| [org.sonarsource.scanner.maven:sonar-maven-plugin](https://github.com/SonarSource/sonar-scanner-maven) | `5.7.0.6970` | `5.8.0.7211` |
| org.apache.felix:org.apache.felix.framework | `7.0.5` | `8.0.0` |

Updates `org.slf4j:slf4j-bom` from 2.0.18 to 2.0.20
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/qos-ch/slf4j/releases">org.slf4j:slf4j-bom's releases</a>.</em></p>
<blockquote>
<h2>SLF4J 2.0.20</h2>
<p><strong>2026-09-22 - Release of SLF4J 2.0.20</strong></p>
<p>• <code>Marker</code> instances are slated to become immutable in future releases. As such, methods in the <code>Marker</code> interface adding/removing children are now marked as deprecated.</p>
<p>• A bit-wise identical binary of this version can be reproduced by building from source code at commit 58d80a4fe8f2e811707fcfba4d292b5d62fc2fe9 associated with the tag v_2.0.20. Release built using Java &quot;21&quot; 2023-10-17 LTS build 21.0.1.+12-LTS-29 under Linux Debian 11.6.</p>
<p><strong>Full Changelog</strong>: <a href="https://github.com/qos-ch/slf4j/compare/v_2.0.19...v_2.0.20">https://github.com/qos-ch/slf4j/compare/v_2.0.19...v_2.0.20</a></p>
<h2>SLF4J 2.0.19</h2>
<h3>2026-09-04 - Release of SLF4J 2.0.19</h3>
<ul>
<li>
<p>When the fluent API was used with <code>XLogger</code>/<code>LoggerWrapper</code> in the <em>slf4j-ext</em> module, caller location was incorrectly reported. To correct this, <code>LoggerWrapper</code> now delegates <code>makeLoggingEventBuilder()</code> to the wrapped logger so that the application caller can be correctly extracted. This issue was reported in <a href="">issues/464</a>.</p>
</li>
<li>
<p>In <code>slf4j-api/DefaultLoggingEventBuilder</code>, a failing <code>toString()</code> invocation on a key-value value, including <code>StackOverflowError</code>, no longer aborts logging. The builder now substitutes <code>[FAILED toString()]</code>, matching the existing behaviour of <code>MessageFormatter</code> for message arguments. This issue was reported in <a href="">issues/448</a>.</p>
</li>
<li>
<p>The <code>isLoggable()</code> method in <code>SLF4JPlatformLogger</code> now maps <code>System.Logger.Level.ALL</code> and <code>Level.OFF</code> the same way as <code>log()</code>, that is ALL as TRACE and OFF as ERROR, instead of treating both as always loggable. This is a follow-up to the changes introduced in 2.0.17. See <a href="">issues/430</a>.</p>
</li>
<li>
<p>Published JAR files now package each module's own <em>LICENSE.txt</em> under <em>META-INF/</em>. Previously the parent POM copied the repository-root MIT license into every module, so Apache-2.0 modules such as <em>jcl-over-slf4j</em> and <em>log4j-over-slf4j</em> shipped the wrong license text. This issue was reported in <a href="">issues/465</a>.</p>
</li>
<li>
<p>A bit-wise identical binary of this version can be reproduced by building from source code at commit f0fc3e52a16d5053039495f4f3b64d191508204f associated with the tag v_2.0.19. Release built using Java &quot;21&quot; 2023-10-17 LTS build 21.0.1.+12-LTS-29 under Linux Debian 11.6.</p>
</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>58d80a4</code></a> prepare release 2.0.20</li>
<li><a href=""><code>ef47ab9</code></a> deprecate methods for adding/remocing children to markers</li>
<li><a href=""><code>6b6c63e</code></a> fix failing test on Windows</li>
<li><a href=""><code>233d4d1</code></a> renamed LoggerTestSuite.java as SimpleLoggerAcceptanceTest</li>
<li><a href=""><code>bf3a7b9</code></a> start work on 2.0.20-SNAPSHOT</li>
<li><a href=""><code>f0fc3e5</code></a> prepare release 2.0.19</li>
<li><a href=""><code>2288d0c</code></a> fix issues/464. slf4j-ext/XLogger incorrect caller extraction when the fluent...</li>
<li><a href=""><code>6ff7f77</code></a> test: pin fluent API caller method name</li>
<li><a href=""><code>2b3f94b</code></a> SLF4JPlatformLogger.isLoggable should handle Logger.ALL and Logger.OFF in a c...</li>
<li><a href=""><code>9221f77</code></a> fix(api): guard addKeyValue value toString from fatal errors</li>
<li>Additional commits viewable in <a href="https://github.com/qos-ch/slf4j/compare/v_2.0.18...v_2.0.20">compare view</a></li>
</ul>
</details>
<br />

Updates `org.slf4j:slf4j-api` from 2.0.18 to 2.0.20

Updates `org.apache.felix:org.apache.felix.gogo.runtime` from 1.1.6 to 1.2.0

Updates `org.weasis.thirdparty:docking-frames` from 1.1.7 to 1.1.8

Updates `org.apache.felix:org.apache.felix.scr` from 2.2.18 to 2.3.0

Updates `org.apache.felix:org.apache.felix.configadmin` from 1.9.26 to 1.10.0

Updates `org.weasis.thirdparty:jaxb-osgi` from 4.0.3 to 4.0.9

Updates `org.eclipse.parsson:parsson` from 1.1.7 to 1.1.9
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/eclipse-ee4j/parsson/releases">org.eclipse.parsson:parsson's releases</a>.</em></p>
<blockquote>
<h2>1.1.9</h2>
<h2>What's Changed</h2>
<ul>
<li>Publish Central releases automatically by <a href="https://github.com/jbescos"><code>@​jbescos</code></a> in <a href="">eclipse-ee4j/parsson#171</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/eclipse-ee4j/parsson/compare/1.1.8...1.1.9">https://github.com/eclipse-ee4j/parsson/compare/1.1.8...1.1.9</a></p>
<h2>1.1.8</h2>
<h2>What's Changed</h2>
<ul>
<li>Update deprecated GH actions by <a href="https://github.com/jbescos"><code>@​jbescos</code></a> in <a href="">eclipse-ee4j/parsson#136</a></li>
<li>Make JsonArrayImpl implement RandomAccess by <a href="https://github.com/marschall"><code>@​marschall</code></a> in <a href="">eclipse-ee4j/parsson#135</a></li>
<li>Implement JsonStructureParser.currentEvent() by <a href="https://github.com/marschall"><code>@​marschall</code></a> in <a href="">eclipse-ee4j/parsson#134</a></li>
<li>Remove unused method by <a href="https://github.com/pzygielo"><code>@​pzygielo</code></a> in <a href="">eclipse-ee4j/parsson#137</a></li>
<li>Rename parameter to match field by <a href="https://github.com/pzygielo"><code>@​pzygielo</code></a> in <a href="">eclipse-ee4j/parsson#138</a></li>
<li>Implement JsonStructureParser#getValue methods by <a href="https://github.com/marschall"><code>@​marschall</code></a> in <a href="">eclipse-ee4j/parsson#140</a></li>
<li>Use assertThrows by <a href="https://github.com/marschall"><code>@​marschall</code></a> in <a href="">eclipse-ee4j/parsson#142</a></li>
<li>Fix compilation failes by <a href="https://github.com/marschall"><code>@​marschall</code></a> in <a href="">eclipse-ee4j/parsson#144</a></li>
<li>Adding Dependabot for dependency management by <a href="https://github.com/mswatosh"><code>@​mswatosh</code></a> in <a href="">eclipse-ee4j/parsson#148</a></li>
<li>json input size limit by <a href="https://github.com/jbescos"><code>@​jbescos</code></a> in <a href="">eclipse-ee4j/parsson#169</a></li>
<li>Add Maven Central publishing release profile by <a href="https://github.com/jbescos"><code>@​jbescos</code></a> in <a href="">eclipse-ee4j/parsson#170</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/marschall"><code>@​marschall</code></a> made their first contribution in <a href="">eclipse-ee4j/parsson#135</a></li>
<li><a href="https://github.com/mswatosh"><code>@​mswatosh</code></a> made their first contribution in <a href="">eclipse-ee4j/parsson#148</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/eclipse-ee4j/parsson/compare/1.1.7...1.1.8">https://github.com/eclipse-ee4j/parsson/compare/1.1.7...1.1.8</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>f7204e8</code></a> Prepare release org.eclipse.parsson:project:1.1.9</li>
<li><a href=""><code>2d01f00</code></a> Publish Central releases automatically (<a href="">#171</a>)</li>
<li><a href=""><code>10920a2</code></a> Add Maven Central publishing release profile (<a href="">#170</a>)</li>
<li><a href=""><code>134e8d1</code></a> json input size limit (<a href="">#169</a>)</li>
<li><a href=""><code>0789993</code></a> Adding Dependabot for dependency management (<a href="">#148</a>)</li>
<li><a href=""><code>216b15d</code></a> Fix compilation failes (<a href="">#144</a>)</li>
<li><a href=""><code>34177db</code></a> Use assertThrows (<a href="">#142</a>)</li>
<li><a href=""><code>9d67960</code></a> Implement JsonStructureParser#getValue methods (<a href="">#140</a>)</li>
<li><a href=""><code>7c8c244</code></a> Rename parameter to match field (<a href="">#138</a>)</li>
<li><a href=""><code>4dda2e0</code></a> Remove unused method (<a href="">#137</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/eclipse-ee4j/parsson/compare/1.1.7...1.1.9">compare view</a></li>
</ul>
</details>
<br />

Updates `com.github.oshi:oshi-core-ffm` from 7.6.0 to 7.7.3
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/oshi/oshi/releases">com.github.oshi:oshi-core-ffm's releases</a>.</em></p>
<blockquote>
<h2>Release 7.7.3</h2>
<h5>Bug Fixes and Improvements</h5>
<ul>
<li><a href="">#3837</a>: Reject IPv6 address text with a dotted IPv4 component before compressed zero groups - <a href="https://github.com/PHJ2000"><code>@​PHJ2000</code></a>.</li>
<li><a href="">#3843</a>: <code>HWDiskStore.getDiskType()</code> on Windows now reports <code>SSD</code>, <code>HDD</code>, <code>Removable</code> or <code>Virtual</code>, read from the storage driver and falling back to <code>MSFT_PhysicalDisk</code> - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3848</a>: Fixed listing processes on DragonFly BSD, which could panic the kernel since 7.7.2. <code>OSProcess.getPath()</code> there now reads the full path from the kernel for the current process only, and <code>argv[0]</code> or the command name for others - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3852</a>: Fixed IPv4 and IPv6 addresses reported byte-reversed on big-endian Linux, such as s390x, in <code>NetworkParams.getRoutes()</code> and <code>InternetProtocolStats.getConnections()</code> - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3853</a>: <code>NetworkParams.getIpv4DefaultGateway()</code> and <code>getIpv6DefaultGateway()</code> on Linux now read the kernel routing table, so they no longer return an empty string when the <code>route</code> command is missing or not on the <code>PATH</code> - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
</ul>
<p><a href="https://github.com/oshi/oshi/blob/master/CHANGELOG.md">Full change log</a></p>
<h2>Release 7.7.2</h2>
<h5>Bug Fixes and Improvements</h5>
<ul>
<li><a href="">#3785</a>: Fixed DragonFly BSD reporting 0 total swap, and the FFM implementation failing every <code>sysctl</code> read there - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3785</a>, <a href="">#3795</a>, <a href="">#3800</a>, <a href="">#3801</a>, <a href="">#3803</a>, <a href="">#3822</a>, <a href="">#3831</a>: Fixed the TCP and UDP statistics from <code>InternetProtocolStats</code> on Linux, macOS, AIX, FreeBSD, OpenBSD, NetBSD and DragonFly BSD, where many counters were read from the wrong field or at the wrong width. Counters a platform does not keep now report 0, including IPv6 UDP on FreeBSD and macOS, and connection failures and UDP receive errors on AIX - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3787</a>, <a href="">#3816</a>: <code>ComputerSystem</code>, <code>Firmware</code> and <code>Baseboard</code> now report SMBIOS values without root on FreeBSD and DragonFly BSD, and at all on NetBSD, where every value was unknown; NetBSD's serial numbers and UUID still need root. <code>Firmware.getReleaseDate()</code> is no longer garbled on any platform when the firmware does not write the date as MM/DD/YYYY - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3788</a>, <a href="">#3807</a>, <a href="">#3814</a>, <a href="">#3824</a>: Fixed <code>NetworkIF</code> on the BSDs: traffic statistics were 0 on OpenBSD and DragonFly BSD, and on NetBSD for interfaces without a link-level address, and <code>getSpeed()</code> was always 0 on FreeBSD, OpenBSD and NetBSD. <code>NetworkParams</code> now reports DragonFly BSD's default gateways and reads NetBSD's routing table from the kernel - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3789</a>, <a href="">#3792</a>, <a href="">#3799</a>, <a href="">#3812</a>, <a href="">#3818</a>: Fixed <code>CentralProcessor</code> on FreeBSD, NetBSD and DragonFly BSD, which miscounted cores, packages or logical processors and left identification and caches unknown, and on NetBSD ARM threw a <code>StackOverflowError</code>. AMD processors of family 16 and later now get the right family on OpenBSD and the right <code>ProcessorID</code> where OSHI builds one. FreeBSD context switch and interrupt counts no longer wrap at 2^32 - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3791</a>, <a href="">#3798</a>, <a href="">#3819</a>, <a href="">#3833</a>: Fixed <code>getDiskStores()</code> on the BSDs: DragonFly BSD returned no disks, FreeBSD listed each disk as a partition of the next, and NetBSD listed each wedge as a separate disk. Partitions now sit under their disk with their mount points, and on OpenBSD and NetBSD without root they no longer include another disk's or misread their size when <code>BLOCKSIZE</code> is set - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3793</a>, <a href="">#3810</a>, <a href="">#3817</a>, <a href="">#3821</a>, <a href="">#3827</a>, <a href="">#3829</a>, <a href="">#3832</a>: Fixed <code>OSProcess</code> on the BSDs. <code>getPath()</code> now returns the executable's full path from the kernel on FreeBSD, DragonFly BSD and NetBSD, as does <code>getCurrentWorkingDirectory()</code> on NetBSD. DragonFly BSD now reports bitness and affinity, FreeBSD other processes' open-file limits, and NetBSD every thread of a process and only real descriptors in <code>getOpenFiles()</code>. <code>getServices()</code> skips rcorder placeholders - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3797</a>, <a href="">#3805</a>, <a href="">#3826</a>: Fixed <code>getPowerSources()</code> on FreeBSD and DragonFly BSD, which reported a battery on machines with none and only one of several, with units and signs now matching other platforms; <code>getGraphicsCards()</code> on current FreeBSD, which reported the wrong vendor and no device ID; and <code>getUsbDevices()</code> on FreeBSD, which was empty - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3808</a>, <a href="">#3820</a>, <a href="">#3823</a>, <a href="">#3825</a>: Fixed <code>FileSystem</code> and <code>OSFileStore</code> on the BSDs. <code>getMaxFileDescriptorsPerProcess()</code> returns the per-process limit, NetBSD's <code>getOpenFileDescriptors()</code> is no longer 0, FreeBSD's <code>getUUID()</code> is found for every volume, and mount points with spaces and NetBSD and OpenBSD inode counts are read correctly - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
</ul>
<p><a href="https://github.com/oshi/oshi/blob/master/CHANGELOG.md">Full change log</a></p>
<h2>Release 7.7.1</h2>
<h5>Bug Fixes and Improvements</h5>
<ul>
<li><a href="">#3763</a>: Standardizes connection reporting from <code>InternetProtocolStats.getConnections()</code> on the UNIX platforms. It now includes listening and unconnected sockets, as on Linux, and returns connections on Solaris, where it returned none. A <code>tcp6</code> or <code>udp6</code> connection to an IPv4 peer now has a 16-byte IPv4-mapped address rather than a 4-byte one - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3771</a>: Fixed <code>Firmware.getManufacturer()</code> on Linux, which never read the BIOS vendor from sysfs - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3774</a>: <code>LogicalVolumeGroup.getPhysicalVolumes()</code> on Linux now runs <code>pvs</code> through the <code>oshi.os.linux.privileged.prefix</code> when <code>pvs</code> is in <code>oshi.os.linux.privileged.allowlist</code>, so physical volumes that hold no logical volume can be listed without running the application as root - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3777</a>: Fixed the heap corruption behind intermittent JVM crashes on Solaris and illumos - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3781</a>: <code>Sensors.getCpuTemperature()</code> now returns a 0.0 sentinel on all platforms when the temperature is unavailable. FreeBSD previously returned <code>NaN</code> - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3776</a>, <a href="">#3782</a>: Fixed intermittent JVM crashes on Solaris (illumos), OpenBSD and DragonFly BSD when <code>libcups</code> is not installed - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
</ul>
<p><a href="https://github.com/oshi/oshi/blob/master/CHANGELOG.md">Full change log</a></p>
<h2>Release 7.7.0</h2>
<h5>New Features</h5>
<ul>
<li><a href="">#3745</a>: The FFM implementation now reads NetBSD natively, through <code>sysctl</code>, <code>getloadavg</code>, <code>_lwp_self</code> and <code>getrlimit</code>, where it previously ran commands and parsed their output - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3709</a>, <a href="">#3757</a>: <code>Display.getCurrentMode()</code> returns the mode a display is driven in: its logical and pixel resolution, refresh rate, rotation, and position on the desktop. <code>Display.isBuiltIn()</code> reports whether it is a built-in panel, and <code>Display.isPrimary()</code> whether it is the primary display. All three are available on Windows, macOS, and on Linux and the other UNIX platforms through X11 - <a href="https://github.com/ayonization"><code>@​ayonization</code></a>, <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
</ul>
<h5>Bug Fixes and Improvements</h5>
<ul>
<li><a href="">#3723</a>: Windows <code>Sensors</code> now reads CPU temperature, fan speed and voltage from the <code>ROOT\LibreHardwareMonitor</code> WMI namespace when the LibreHardwareMonitor application is running, in addition to the <code>ROOT\OpenHardwareMonitor</code> namespace it already read. Users running the maintained LibreHardwareMonitor previously got its GPU metrics but no CPU sensor data - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3727</a>: The <code>oshi.os.windows.ohm.disabled</code> and <code>oshi.os.windows.lhm.disabled</code> configuration properties now skip the Open Hardware Monitor and Libre Hardware Monitor WMI namespaces, which OSHI otherwise queries on each sensor read until one returns data. The latter also covers GPU metrics - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3730</a>: Fixed <code>Sensors.getCpuVoltage()</code> on Windows when using the voltage published by Open Hardware Monitor or LibreHardwareMonitor - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3742</a>: <code>NetworkParams.getRoutes()</code> on NetBSD now reads the routing table from the kernel where the JNA native library is available - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/oshi/oshi/blob/master/CHANGELOG.md">com.github.oshi:oshi-core-ffm's changelog</a>.</em></p>
<blockquote>
<h1>7.7.0 (2026-09-29), 7.7.1 (2026-10-10), 7.7.2 (2026-10-20), 7.7.3 (2026-10-31)</h1>
<h5>New Features</h5>
<ul>
<li><a href="">#3745</a>: The FFM implementation now reads NetBSD natively, through <code>sysctl</code>, <code>getloadavg</code>, <code>_lwp_self</code> and <code>getrlimit</code>, where it previously ran commands and parsed their output - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3709</a>,
<a href="">#3757</a>: <code>Display.getCurrentMode()</code> returns the mode a display is driven in: its logical and pixel resolution, refresh rate, rotation, and position on the desktop. <code>Display.isBuiltIn()</code> reports whether it is a built-in panel, and <code>Display.isPrimary()</code> whether it is the primary display. All three are available on Windows, macOS, and on Linux and the other UNIX platforms through X11 - <a href="https://github.com/ayonization"><code>@​ayonization</code></a>, <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
</ul>
<h5>Bug Fixes and Improvements</h5>
<ul>
<li><a href="">#3723</a>: Windows <code>Sensors</code> now reads CPU temperature, fan speed and voltage from the <code>ROOT\LibreHardwareMonitor</code> WMI namespace when the LibreHardwareMonitor application is running, in addition to the <code>ROOT\OpenHardwareMonitor</code> namespace it already read. Users running the maintained LibreHardwareMonitor previously got its GPU metrics but no CPU sensor data - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3727</a>: The <code>oshi.os.windows.ohm.disabled</code> and <code>oshi.os.windows.lhm.disabled</code> configuration properties now skip the Open Hardware Monitor and Libre Hardware Monitor WMI namespaces, which OSHI otherwise queries on each sensor read until one returns data. The latter also covers GPU metrics - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3730</a>: Fixed <code>Sensors.getCpuVoltage()</code> on Windows when using the voltage published by Open Hardware Monitor or LibreHardwareMonitor - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3742</a>: <code>NetworkParams.getRoutes()</code> on NetBSD now reads the routing table from the kernel where the JNA native library is available - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3743</a>: Fixed three <code>HWDiskStore</code> faults on NetBSD: read and write byte totals that could decrease between readings, a doubled <code>getTransferTime()</code>, and a 1-byte disk or 512-byte partition size where the size is unknown, which also affected OpenBSD - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3744</a>: Fixed <code>OSProcess</code> naming on NetBSD: <code>getPath()</code> and <code>getName()</code> were truncated to seven characters, and where the kernel withholds a process's arguments, <code>getCommandLine()</code> returned <code>ps</code>'s <code>(command)</code> placeholder and <code>getName()</code> kept its parentheses - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3754</a>: <code>OperatingSystem.getProcessId()</code> and <code>getThreadId()</code> return 0 when the ID is unknown on every platform. On NetBSD without JNA, <code>getThreadId()</code> returned a Java thread ID, and on failure some implementations returned -1, which led <code>getCurrentProcess()</code> to return an arbitrary process on the BSDs, Solaris and AIX. <code>getProcess()</code> with a negative PID now returns null on Solaris and AIX - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3763</a>: Standardizes connection reporting from <code>InternetProtocolStats.getConnections()</code> on the UNIX platforms. It now includes listening and unconnected sockets, as on Linux, and returns connections on Solaris, where it returned none. A <code>tcp6</code> or <code>udp6</code> connection to an IPv4 peer now has a 16-byte IPv4-mapped address rather than a 4-byte one - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3771</a>: Fixed <code>Firmware.getManufacturer()</code> on Linux, which never read the BIOS vendor from sysfs - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3774</a>: <code>LogicalVolumeGroup.getPhysicalVolumes()</code> on Linux now runs <code>pvs</code> through the <code>oshi.os.linux.privileged.prefix</code> when <code>pvs</code> is in <code>oshi.os.linux.privileged.allowlist</code>, so physical volumes that hold no logical volume can be listed without running the application as root - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3777</a>: Fixed the heap corruption behind intermittent JVM crashes on Solaris and illumos - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3781</a>: <code>Sensors.getCpuTemperature()</code> now returns a 0.0 sentinel on all platforms when the temperature is unavailable. FreeBSD previously returned <code>NaN</code> - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3776</a>,
<a href="">#3782</a>: Fixed intermittent JVM crashes on Solaris (illumos), OpenBSD and DragonFly BSD when <code>libcups</code> is not installed - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3785</a>: Fixed DragonFly BSD reporting 0 total swap, and the FFM implementation failing every <code>sysctl</code> read there - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3785</a>,
<a href="">#3795</a>,
<a href="">#3800</a>,
<a href="">#3801</a>,
<a href="">#3803</a>,
<a href="">#3822</a>,
<a href="">#3831</a>: Fixed the TCP and UDP statistics from <code>InternetProtocolStats</code> on Linux, macOS, AIX, FreeBSD, OpenBSD, NetBSD and DragonFly BSD, where many counters were read from the wrong field or at the wrong width. Counters a platform does not keep now report 0, including IPv6 UDP on FreeBSD and macOS, and connection failures and UDP receive errors on AIX - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3787</a>,
<a href="">#3816</a>: <code>ComputerSystem</code>, <code>Firmware</code> and <code>Baseboard</code> now report SMBIOS values without root on FreeBSD and DragonFly BSD, and at all on NetBSD, where every value was unknown; NetBSD's serial numbers and UUID still need root. <code>Firmware.getReleaseDate()</code> is no longer garbled on any platform when the firmware does not write the date as MM/DD/YYYY - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3788</a>,
<a href="">#3807</a>,
<a href="">#3814</a>,
<a href="">#3824</a>: Fixed <code>NetworkIF</code> on the BSDs: traffic statistics were 0 on OpenBSD and DragonFly BSD, and on NetBSD for interfaces without a link-level address, and <code>getSpeed()</code> was always 0 on FreeBSD, OpenBSD and NetBSD. <code>NetworkParams</code> now reports DragonFly BSD's default gateways and reads NetBSD's routing table from the kernel - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3789</a>,
<a href="">#3792</a>,
<a href="">#3799</a>,
<a href="">#3812</a>,
<a href="">#3818</a>: Fixed <code>CentralProcessor</code> on FreeBSD, NetBSD and DragonFly BSD, which miscounted cores, packages or logical processors and left identification and caches unknown, and on NetBSD ARM threw a <code>StackOverflowError</code>. AMD processors of family 16 and later now get the right family on OpenBSD and the right <code>ProcessorID</code> where OSHI builds one. FreeBSD context switch and interrupt counts no longer wrap at 2^32 - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3791</a>,
<a href="">#3798</a>,
<a href="">#3819</a>,
<a href="">#3833</a>: Fixed <code>getDiskStores()</code> on the BSDs: DragonFly BSD returned no disks, FreeBSD listed each disk as a partition of the next, and NetBSD listed each wedge as a separate disk. Partitions now sit under their disk with their mount points, and on OpenBSD and NetBSD without root they no longer include another disk's or misread their size when <code>BLOCKSIZE</code> is set - <a href="https://github.com/dbwiddis"><code>@​dbwiddis</code></a>.</li>
<li><a href="">#3793</a>,
<a href="">#3810</a>,
<a href="">#3817</a>,</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>47d0e45</code></a> [maven-release-plugin] prepare release oshi-parent-7.7.3</li>
<li><a href=""><code>7efc531</code></a> 7.7.3 Release</li>
<li><a href=""><code>c46a6c0</code></a> Resolve the three open Sonar findings</li>
<li><a href=""><code>f5e572d</code></a> Allow for whole-minute sources in the AIX boot time test (<a href="">#3854</a>)</li>
<li><a href=""><code>c55f2d4</code></a> Read the Linux default gateways from the kernel routing table (<a href="">#3853</a>)</li>
<li><a href=""><code>5154264</code></a> Decode /proc/net addresses in the host's byte order on Linux (<a href="">#3852</a>)</li>
<li><a href=""><code>9480cbc</code></a> Update dependency org.apache.maven.plugins:maven-enforcer-plugin to v3.7.0 (#...</li>
<li><a href=""><code>7170e1f</code></a> Update eclipse-temurin Docker tag to v25.0.5_8-jdk-alpine (<a href="">#3850</a>)</li>
<li><a href=""><code>4e05429</code></a> Print JVM crash reports from every Unix CI job when its build fails</li>
<li><a href=""><code>0bb4198</code></a> Name the AppVeyor account in the on-demand build request</li>
<li>Additional commits viewable in <a href="https://github.com/oshi/oshi/compare/oshi-parent-7.6.0...oshi-parent-7.7.3">compare view</a></li>
</ul>
</details>
<br />

Updates `org.junit:junit-bom` from 6.1.2 to 6.1.3
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/junit-team/junit-framework/releases">org.junit:junit-bom's releases</a>.</em></p>
<blockquote>
<p>JUnit 6.1.3 = Platform 6.1.3 + Jupiter 6.1.3 + Vintage 6.1.3</p>
<p>See <a href="https://docs.junit.org/6.1.3/release-notes.html">Release Notes</a>.</p>
<p><strong>Full Changelog</strong>: <a href="https://github.com/junit-team/junit-framework/compare/r6.1.2...r6.1.3">https://github.com/junit-team/junit-framework/compare/r6.1.2...r6.1.3</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>f59f60d</code></a> Release 6.1.3</li>
<li><a href=""><code>cd8ec92</code></a> Finalize 6.1.3 release notes</li>
<li><a href=""><code>c8729f2</code></a> Restore compatibility with GraalVM 25 (<a href="">#5901</a>)</li>
<li><a href=""><code>ddc9e74</code></a> Update graalvm/setup-graalvm action to v1.6.4 (<a href="">#5959</a>)</li>
<li><a href=""><code>fe2c52a</code></a> Update plugin org.graalvm.buildtools.native to v1.1.7 (<a href="">#5923</a>)</li>
<li><a href=""><code>62afc02</code></a> Delay GraalVM plugin updates for 3 days</li>
<li><a href=""><code>0cc2902</code></a> Skip <code>graalVmTest</code> task if GraalVM env vars are not set</li>
<li><a href=""><code>f6bbfc5</code></a> Move GraalVM tests to separate test task (<a href="">#5903</a>)</li>
<li><a href=""><code>e87e052</code></a> Update plugin org.graalvm.buildtools.native to v1.1.6 (<a href="">#5899</a>)</li>
<li><a href=""><code>1cd56df</code></a> Update plugin org.graalvm.buildtools.native to v1.1.5 (<a href="">#5880</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/junit-team/junit-framework/compare/r6.1.2...r6.1.3">compare view</a></li>
</ul>
</details>
<br />

Updates `org.mockito:mockito-bom` from 5.23.0 to 5.24.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/mockito/mockito/releases">org.mockito:mockito-bom's releases</a>.</em></p>
<blockquote>
<h2>v5.24.0</h2>
<p><!-- raw HTML omitted --><!-- raw HTML omitted --><em>Changelog generated by <a href="https://github.com/shipkit/shipkit-changelog">Shipkit Changelog Gradle Plugin</a></em><!-- raw HTML omitted --><!-- raw HTML omitted --></p>
<h4>5.24.0</h4>
<ul>
<li>2026-09-23 - <a href="https://github.com/mockito/mockito/compare/v5.23.0...v5.24.0">27 commit(s)</a> by Andrei Solntsev, DragonFSKY, Hünkar Can Tunç, Joshua Selbo, M. Minot, Markus Gaisbauer, Mirko Alicastro, Vinod Kumar M ( codingkiddo ), dependabot[bot]</li>
<li>Fix Mockito docs for -javaagent flag with Gradle [(<a href="">#3866</a>)](<a href="">mockito/mockito#3866</a>)</li>
<li>Kotlin example for adding Mockito as an agent is incorrect [(<a href="">#3864</a>)](<a href="">mockito/mockito#3864</a>)</li>
<li>Bump graalvm/setup-graalvm from 1.6.3 to 1.6.6 [(<a href="">#3862</a>)](<a href="">mockito/mockito#3862</a>)</li>
<li>Bump gradle/actions from 6.2.0 to 6.3.0 [(<a href="">#3852</a>)](<a href="">mockito/mockito#3852</a>)</li>
<li>Bump gradle/actions from 5 to 6.2.0 [(<a href="">#3851</a>)](<a href="">mockito/mockito#3851</a>)</li>
<li>Preserve method parameters when clearing inline mocks [(<a href="">#3847</a>)](<a href="">mockito/mockito#3847</a>)</li>
<li>Bump graalvm/setup-graalvm from 1.6.0 to 1.6.3 [(<a href="">#3845</a>)](<a href="">mockito/mockito#3845</a>)</li>
<li>Print object fields via reflection when <code>toString()</code> is not implemented [(<a href="">#3844</a>)](<a href="">mockito/mockito#3844</a>)</li>
<li>Migrate extensions-tests to JUnit Jupiter [(<a href="">#3840</a>)](<a href="">mockito/mockito#3840</a>)</li>
<li>Bump graalvm/setup-graalvm from 1.5.6 to 1.6.0 [(<a href="">#3839</a>)](<a href="">mockito/mockito#3839</a>)</li>
<li>docs(when-verify): fixes to explanations about redundancy [(<a href="">#3838</a>)](<a href="">mockito/mockito#3838</a>)</li>
<li>Confusing inconsistency in example method calls in “stubbing and verifying is redundant” note of “when” and “verify” Javadoc [(<a href="">#3837</a>)](<a href="">mockito/mockito#3837</a>)</li>
<li>Bump actions/checkout from 6 to 7 [(<a href="">#3836</a>)](<a href="">mockito/mockito#3836</a>)</li>
<li>Fixes <a href="">#2740</a> : Add mockMaker option to <code>@Spy</code> annotation [(<a href="">#3835</a>)](<a href="">mockito/mockito#3835</a>)</li>
<li>Bump graalvm/setup-graalvm from 1.5.5 to 1.5.6 [(<a href="">#3834</a>)](<a href="">mockito/mockito#3834</a>)</li>
<li>Bump graalvm/setup-graalvm from 1.5.4 to 1.5.5 [(<a href="">#3833</a>)](<a href="">mockito/mockito#3833</a>)</li>
<li>Bump codecov/codecov-action from 6 to 7 [(<a href="">#3831</a>)](<a href="">mockito/mockito#3831</a>)</li>
<li>Bump graalvm/setup-graalvm from 1.4.5 to 1.5.4 [(<a href="">#3830</a>)](<a href="">mockito/mockito#3830</a>)</li>
<li>Fix clearInlineMocks not de-registering singleton mocks [(<a href="">#3829</a>)](<a href="">mockito/mockito#3829</a>)</li>
<li>Fix NotAMockException when using mockSingleton with MockitoJUnit [(<a href="">#3827</a>)](<a href="">mockito/mockito#3827</a>)</li>
<li>NotAMockException when using mockSingleton with MockitoSession or MockitoJUnit [(<a href="">#3826</a>)](<a href="">mockito/mockito#3826</a>)</li>
<li>Improve Gradle agent docs for configuration cache [(<a href="">#3823</a>)](<a href="">mockito/mockito#3823</a>)</li>
<li>Gradle documentation for setting up instrumentation with Gradle configuration cache [(<a href="">#3822</a>)](<a href="">mockito/mockito#3822</a>)</li>
<li>Fixes <a href="">#3818</a> : Fix data race in InvocationContainerImpl.invocationForStubbing [(<a href="">#3819</a>)](<a href="">mockito/mockito#3819</a>)</li>
<li>Data race on invocationForPotentialStubbing [(<a href="">#3818</a>)](<a href="">mockito/mockito#3818</a>)</li>
<li>Fixes <a href="">#3814</a> : implement package-level clinit suppression [(<a href="">#3815</a>)](<a href="">mockito/mockito#3815</a>)</li>
<li>Package-level clinit suppression [(<a href="">#3814</a>)](<a href="">mockito/mockito#3814</a>)</li>
<li>Upgrade Android Gradle Plugin to 8.13.2 [(<a href="">#3812</a>)](<a href="">mockito/mockito#3812</a>)</li>
<li>Replaces raw generic types with type parameters [(<a href="">#3806</a>)](<a href="">mockito/mockito#3806</a>)</li>
<li>Fixes <a href="">#2398</a> : Implement global suppress static initialization leveraging java agent [(<a href="">#3801</a>)](<a href="">mockito/mockito#3801</a>)</li>
<li>Bump codecov/codecov-action from 5 to 6 [(<a href="">#3800</a>)](<a href="">mockito/mockito#3800</a>)</li>
<li>Fix non-deterministic AssertionError when using MockMakers.SUBCLASS (<a href="">#3406</a>, <a href="">#2823</a>) [(<a href="">#3795</a>)](<a href="">mockito/mockito#3795</a>)</li>
<li>Fixes <a href="">#3536</a> : Implement SpyStatic API [(<a href="">#3794</a>)](<a href="">mockito/mockito#3794</a>)</li>
<li>The class's MethodParameters are removed after clearAllCaches is invoked [(<a href="">#3763</a>)](<a href="">mockito/mockito#3763</a>)</li>
<li>[FeatureRequest / Idea] Create Mockito.spyStatic [(<a href="">#3536</a>)](<a href="">mockito/mockito#3536</a>)</li>
<li>Add option to specify mockmaker for <code>@Spy</code> [(<a href="">#2740</a>)](<a href="">mockito/mockito#2740</a>)</li>
<li>How can I suppress static initializer? [(<a href="">#2398</a>)](<a href="">mockito/mockito#2398</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5a2f0f8</code></a> Fix Mockito docs for -javaagent flag with Gradle (<a href="">#3866</a>)</li>
<li><a href=""><code>9c5f36f</code></a> Bump graalvm/setup-graalvm from 1.6.3 to 1.6.6 (<a href="">#3862</a>)</li>
<li><a href=""><code>e7fd06d</code></a> Preserve method parameters when clearing inline mocks (<a href="">#3847</a>)</li>
<li><a href=""><code>5a676bc</code></a> Bump gradle/actions from 6.2.0 to 6.3.0 (<a href="">#3852</a>)</li>
<li><a href=""><code>508f8e7</code></a> Bump gradle/actions from 5 to 6.2.0 (<a href="">#3851</a>)</li>
<li><a href=""><code>ee8a330</code></a> Print object fields via reflection when <code>toString()</code> is not implemented (<a href="">#3844</a>)</li>
<li><a href=""><code>39b1aba</code></a> Bump graalvm/setup-graalvm from 1.6.0 to 1.6.3 (<a href="">#3845</a>)</li>
<li><a href=""><code>d8638e1</code></a> Migrate extensions-tests to JUnit Jupiter (<a href="">#3840</a>)</li>
<li><a href=""><code>0aab922</code></a> Bump graalvm/setup-graalvm from 1.5.6 to 1.6.0 (<a href="">#3839</a>)</li>
<li><a href=""><code>f3cf74c</code></a> docs(when-verify): fixes to explanations about redundancy (<a href="">#3838</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/mockito/mockito/compare/v5.23.0...v5.24.0">compare view</a></li>
</ul>
</details>
<br />

Updates `org.slf4j:slf4j-api` from 2.0.18 to 2.0.20

Updates `ch.qos.logback:logback-classic` from 1.6.1 to 1.6.6
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/qos-ch/logback/releases">ch.qos.logback:logback-classic's releases</a>.</em></p>
<blockquote>
<h2>Logback 1.6.6</h2>
<h3>2026-10-25 Release of logback version 1.6.6</h3>
<p>• <code>LoggingEventVO</code> now rejects, during deserialization, throwable proxies whose cause or suppressed entries point back into the graph of proxies, for example to their own parent. Such graphs cannot be produced by logback itself. However, a crafted stream sent to a socket receiver could use serialization back-references to build them, after which <code>DefaultThrowableRenderer</code> and <code>SyslogAppender</code> would loop forever and the recursive converters would overflow the stack. These streams are now rejected with an <code>InvalidObjectException</code>. Circular exceptions logged by the application are still transmitted correctly. This issue was reported and fixed in [PR <a href="">#1079</a>](<a href="">qos-ch/logback#1079</a>) by <a href="https://github.com/arfa-21">arfa-21</a>.</p>
<p>• <code>FileNamePattern</code> now escapes characters with a special meaning in regular expressions, such as <code>(</code>, <code>[</code> or <code>+</code>, when converting the literal parts of a file name pattern into a regex. Previously, <code>RollingFileAppender</code> failed to start when the path contained an unbalanced parenthesis, as in <code>C:/Users/Michael(Financ</code>. This issue was reported in <a href="">issues/914</a> by <a href="https://github.com/danamlund">danamlund</a>. Moreover, with <code>SizeAndTimeBasedRollingPolicy</code> and a pattern such as <code>app.%d.(%i).log</code>, existing archives were not recognized. After a restart within the same period, the next rollover could overwrite an existing archive, and <em>maxHistory</em> and <em>totalSizeCap</em> never removed such archives. This issue was reported in <a href="">issues/933</a> by <a href="https://github.com/GeoffreyBoulay">GeoffreyBoulay</a>. The fix was contributed in [PR <a href="">#1077</a>](<a href="">qos-ch/logback#1077</a>) by <a href="https://github.com/CCCLL">Jialin Chen</a>. Regex metacharacters in <code>%d{...}</code> date patterns are now escaped as well.</p>
<p>• The conversion of date patterns into regular expressions now follows the rules of <code>DateTimeFormatter</code>, which logback uses to format dates, instead of those of <code>SimpleDateFormat</code>. In particular, the <code>L</code> (stand-alone month) pattern letter is now supported.</p>
<p>• <code>SyslogOutputStream</code> now connects its <code>DatagramSocket</code> to the syslog host. Previously, the socket was bound to the wildcard address, so that hardened environments saw an unconnected UDP listener on all interfaces for as long as the application ran. This issue was reported in <a href="">issues/939</a> by <a href="https://github.com/joao-rebelo">joao-rebelo</a>. The fix was contributed in [PR <a href="">#1076</a>](<a href="">qos-ch/logback#1076</a>) by <a href="https://github.com/Lyin-OTTF">Lyin-OTTF</a>.</p>
<p>If the socket cannot be connected, for example because the network is not yet available, <code>SyslogOutputStream</code> falls back to an unconnected socket and <code>SyslogAppenderBase</code> emits a warning. When a datagram sent on a connected socket fails due to an ICMP &quot;port unreachable&quot; message caused by an earlier datagram, the datagram is sent once more so that no message is lost. If the retry also fails, a single warning is emitted instead of one error per event.</p>
<p>• <code>OutputStreamAppender</code> now stops its encoder when the appender is stopped. Previously, encoders holding resources until they were stopped, such as those of logstash-logback-encoder, were never released, causing heap growth at each reconfiguration. This issue was fixed in [PR <a href="">#1072</a>](<a href="">qos-ch/logback#1072</a>) by <a href="https://github.com/samyuh">Samuel Fernandes</a>.</p>
<p>• During variable substitution, an unmatched right curly brace now causes an error to be reported, with the original value left unchanged. Previously, the brace and all subsequent characters were silently dropped, so that <code>%m}some text</code> became <code>%m</code>. This issue was reported in <a href="">issues/836</a> by <a href="https://github.com/philsttr">philsttr</a>.</p>
<p>• <code>LogbackMDCAdapter</code> now stores MDC entries in a <code>LinkedHashMap</code>, so that the <code>%X</code> converter outputs them in insertion order. This issue was reported in <a href="https://jira.qos.ch/browse/LOGBACK-1337">LOGBACK-1337</a> and fixed by <a href="https://github.com/motlin">Craig P. Motlin</a>.</p>
<p>• A bit-wise identical binary of this version can be reproduced by building from <a href="https://github.com/qos-ch/logback">source code</a> at commit a9ee8019ee183e076ff5477957dbf90c4b04dd92 associated with the tag <code>v_1.6.6</code>. The release was built using Java &quot;21&quot; 2023-10-17 LTS build 21.0.1.+12-LTS-29 under Linux Debian 11.6.</p>
<h2>Logback 1.6.5</h2>
<p>2026-09-30 Release of logback version 1.6.5</p>
<p>• Fixed a vulnerability <a href="https://www.cve.org/CVERecord?id=CVE-2026-104721">CVE-2026-104721</a> closely related to <a href="https://www.cve.org/cverecord?id=CVE-2026-19880">CVE-2026-19880</a>. The fix in version 1.6.3, which strips forward and backward slashes from <code>MDC</code> values, was insufficient. An <code>MDC</code> value could still contain relative path components such as .., variable references such as /, or characters that are special in file name patterns and email addresses. This latest vulnerability was found and reported by François Martin (GitHub: <a href="https://github.com/martinfrancois"><code>@​martinfrancois</code></a>, <a href="https://github.com/martinfrancois">https://github.com/martinfrancois</a>).</p>
<p><code>MDCBasedDiscriminator</code>, used by <a href="https://logback.qos.ch/manual/appenders-async-sift.html#SiftingAppender"><code>SiftingAppender</code></a>, now rejects <code>MDC</code> values instead of stripping characters from them. An MDC value is rejected if it is empty, if it is longer than 64 characters, if it contains the sequence .., or if it contains any of the following characters: <code>/ \ $ { } [ ] ( ) | ? * + % , @</code>. When an <code>MDC</code> value is rejected, the discriminator returns the value of its <code>DefaultValue</code> property. A warning is emitted for each rejected value. These warnings are rate-limited.</p>
<p>• When compression is enabled, <code>TimeBasedRollingPolicy</code> and <code>SizeAndTimeBasedRollingPolicy</code> now also remove old log files that were never compressed, for example because the application was not running at rollover time. Previously, such files were ignored by <code>maxHistory</code> and accumulated indefinitely. This issue was discussed in <a href="https://github.com/qos-ch/logback/discussions/1032">discussions/1032</a>. See <a href="h...

_Description has been truncated_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7b0154a65126`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.