﻿---
title: Domain Blacklist plug-in
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2021-10-28
---
<p>This plug-in redirects requests for domain names on a blacklist.</p>

<p>This can be used to block banner ads, malicious web-sites, porn web-sites, etc.<br />
Doing this at a central DNS server makes it easy to enforce company/family policy for your entire network.<br />
You can direct browser requests for listed entries either to a dummy IP address, or to an IP address of your own web-server where you serve up some type of  &quot;not allowed&quot; message.</p>

<p>Hosts files (and the <a href="https://simpledns.plus/plugin-hostsfile">hosts file plug-in</a>) are often used for the same thing - but this plug-in is more powerful because it can also match partial host names (&quot;wildcard&quot;, &quot;ends-with-domain&quot; and &quot;regular expressions&quot; entries).</p>

<p>This plug-in is also similar to the <a href="https://simpledns.plus/plugin-blacklist">DNS Blacklist plug-in</a> - except this plug-in is used to block domain names whereas the DNS Blacklist plug-in is used to block IP addresses (typically to block spam and other unwanted e-mails).</p>

<p>In the plug-in instance dialog / Plug-In Settings tab you can specify the data file, and if the file should automatically be reloaded when updated:</p>

<p><img src="img/171/1.png" /></p>

<p>If you want to ensure that specific web-sites are not accidentally blocked (for example if you are using a blacklist data file created by someone else) you can setup a whitelist- see <a href="https://simpledns.plus/kb/79">KB1286</a>.</p>

<p>If you want to relax blacklist restrictions at certain times - for example allow social networking web-sites after normal working hours, you can schedule when the plug-in takes effect - see <a href="https://simpledns.plus/kb/72">KB1287</a>.</p>

<p>NOTE: Operating systems and Internet browsers cache DNS records, so if a user recently accessed or was blocked from accessing a web-site, this information might be cached locally on her computer for some time. You may need to restart all browser instances and type &quot;ipconfig /flushdns&quot; at a command prompt on the local computer before it will query the DNS server again for an updated result.<br />
When using the black/white-list plug-in and users may get different DNS results at different times (as lists are updated), we recommend that you configure Simple DNS Plus to limit client caching to 20 minutes or less. See Options dialog / DNS / Miscellaneous section (v. 5.1 build 118 and later):</p>

<p><img src="img/171/2.png" /></p>

<p><b><u>Data file format specifications</u></b></p>

<p>The data file for this plug-in is a simple text file that you can create using notepad or any text editor tool.<br />
Each line in the file starts with a capital letter I, T, X, M, E or R followed by a space and then some data:</p>

<p>I - the IP address to serve. This is optional and defaults to 127.0.0.1. One entry per file per IP version (4/6).<br />
T - the host record's TTL in seconds. This is optional and defaults to 300. Only one entry per file.<br />
X - Date (YYYYMMDD) file expires. This is optional. Lists do not expire by default. Only one entry per file.<br />
M - exact-match entry. Unlimited entries per file.<br />
E - ends-with-domain entry. Unlimited entries per file.<br />
R - regular expression (<a href="http://en.wikipedia.org/wiki/regular_expression" target="_blank">about</a>) entry. Unlimited entries per file (*).</p>

<p>The domain name of exact-match (M) entries can start with a wildcard character (*.example.com) meaning &quot;all sub-domains&quot;. The wildcard character can only be used as the first character and only when immediately followed by a period(.) and a host name. The difference between an ends-with-domain (E) entry and a wildcard exact-match entry (M *...) is that E entries match the domain name itself whereas M entries do not (only sub-domains).</p>

<p>M, E, and R entries can be prefixed with an exclamation character (!) to indicate an exception (do not block).<br />
Exception entries are always evaluated first and override all other entries.</p>

<p>Empty lines and lines starting with # are ignored.<br />
The # character indicates the start of a comment. Everything from a # character and the rest of the line is ignored.</p>

<p>Example data file content:</p>

<p><code>#Start of Domain Blacklist data file<br />
I 1.2.3.4 #IP address to serve<br />
T 600 #TTL (time to live) - 10 minutes<br />
X 20120725 #File expires on July 25th 2012<br />
M badhost.domain.com #Exact-match entry<br />
M *.badsubnames.com #Wildcard exact-match entry<br />
E baddomain.com #Ends-with-domain entry<br />
R badterm$ #Regular expression entry<br />
!M goodhost.domain.com #Exact-match entry (exception)<br />
!M *.goodsubnames.com #Wildcard exact-match entry (exception)<br />
!E gooddomain.com #Ends-with-domain entry (exception)<br />
!R goodterm$ #Regular expression entry (exception)<br />
#End of Domain Blacklist data file</code></p>

<p>(*) Note about performance:<br />
Exact-match (M) and ends-with-domain (E) entries are very fast, even with thousands of entries, because these are stored in hash tables, whereas regular expression (R) entries must be evaluated one by one for each lookup. Regular expressions are pre-compiled and run very efficiently but are still much slower than the other types. For high traffic sites we therefore recommend using M and E entires over R entries whenever possible.</p>
