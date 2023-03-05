﻿---
title: New in Simple DNS Plus (v. 5.2)
category: 17
frontpage: false
comments: true
vgroup: 7
vname: v. 5.2
vsort: 52
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>New features in v. 5.2:<br />
<a href="#remote">Remote Management</a><br />
<a href="#core">Runs on Windows &quot;Server Core&quot;</a><br />
<a href="#dnssec">DNSSEC</a><br />
<a href="#seczt">Secure Zone Transfers (TSIG signed)</a><br />
<a href="#chkdel">Check Internet Delegations wizard</a><br />
<a href="#perfctr">Windows Performance Counters</a><br />
<a href="#mtpi">High performance, multi-threaded plug-in processing</a><br />
<a href="#rules">DNS request &quot;rules&quot; for plug-ins</a><br />
<a href="#lookup">Enhanced DNS Look Up tool</a><br />
<a href="#stdpi">New standard plug-ins</a><br />
<a href="#misc">Miscellaneous updates / changes</a><br />
<a href="#rfc">New RFC and draft support</a></p>

<hr class="JHHR" />
<h3 id="remote">Remote Management</h3>

<p>You can now use the normal Simple DNS Plus user interface on a remote computer.<br />
For details see <a href="https://simpledns.plus/news/5">this news article</a>.</p>

<p><img alt="rc27.png" height="234" src="img/90/1.png" width="392" /></p>

<hr class="JHHR" />
<h3 id="core">Runs on Windows &quot;Server Core&quot;</h3>

<p>You can now run Simple DNS Plus on Windows Server Core.<br />
For details see <a href="/kb/119/simple-dns-plus-on-windows-server-core">this article</a>.</p>

<p><img alt="core.png" height="101" src="img/90/2.png" width="215" /></p>

<hr class="JHHR" />
<h3 id="dnssec">DNSSEC</h3>

<p>Simple DNS Plus can now host DNSSEC signed zones and includes GUI tools for DNSSEC key management and zone signing. For details see <a href="https://simpledns.plus/news/2">this news article</a>, <a href="/kb/65/how-to-dnssec-sign-a-zone-with-simple-dns-plus">this article</a>, and this article [RETIRED].</p>

<p><img height="381" src="img/90/3.png" width="484" /><br />
&nbsp;</p>

<hr class="JHHR" />
<h3 id="seczt">Secure Zone Transfers (TSIG signed)</h3>

<p>Simple DNS Plus&nbsp;now supports secure zone transfer (TSIG authenticated).<br />
Both zone transfer requests and responses are authenticated, so this provides protection in two ways;&nbsp;it prevents unauthorized transfers (only&nbsp;people / servers with the correct key can transfer), and&nbsp;it ensures data integrity on secondary servers (not possible to spoof / inject false data during transfers).<br />
For details see <a href="https://simpledns.plus/news/6">this news article</a>.</p>

<p><img alt="tsigzt.png" height="228" src="img/90/4.png" width="426" /></p>

<hr class="JHHR" />
<h3 id="chkdel">Check Internet Delegations wizard</h3>

<p>This new wizard lets you automatically test if the NS and SOA records in your local zone data match the actual current delegations on the Internet. This can be very useful both to check for errors and to make sure that you still own the domain names that you think you do. It could also be used for example by ISPs to see if any customers have left them (changed their DNS to another provider).</p>

<p><img alt="chkdel.png" height="416" src="img/90/5.png" width="505" /></p>

<hr class="JHHR" />
<h3 id="perfctr">Windows Performance Counters</h3>

<p>Simple DNS Plus now supplies 9 different performance counters which can be graphed with the Windows Performance Monitor and polled by other programs such as SNMP tools:</p>

<p><img height="545" src="img/90/6.png" width="628" /></p>

<hr class="JHHR" />
<h3 id="mtpi">High performance, multi-threaded plug-in processing</h3>

<p>All plug-in processing is now performed asynchronously (in separate threads) so that other DNS requests that are not processed by the plug-in can proceed without delay.<br />
We have also added the option for plug-ins to process multiple DNS requests in parallel. This can improve plug-in performance significantly - especially for resources on multi-core computers.</p>

<p><img height="441" src="img/90/7.png" width="546" /></p>

<p>Multi threading is currently available in the <a href="https://simpledns.plus/plugin-mssql">MS SQL Server</a>, <a href="https://simpledns.plus/plugin-mssqlplus">MS SQL Server Plus</a>, and the <a href="https://simpledns.plus/plugin-mysql">MySQL Server</a> plug-ins, and is of course also available for implementation by 3rd party plug-in developers.</p>

<hr class="JHHR" />
<h3 id="rules">DNS request &quot;rules&quot; for plug-ins</h3>

<p>New &quot;rule engine&quot; and GUI editor for setting up &quot;rules&quot; controlling which DNS requests are processed by each plug-in. This is configured in new &quot;DNS Requests&quot; tab - which replaces the &quot;DNS Ask About&quot; and &quot;DNS Access&quot; tabs.<br />
Plug-ins can provide custom &quot;rules&quot; for other plug-ins. For example; you can setup a rule that a plug-in may only be queried from IP addresses listed by another plug-in. Such rules may be based on databases or practically anything else you can think of.</p>

<p><img height="364" src="img/90/8.png" width="422" /></p>

<p>More details are available in <a href="/kb/110/plug-ins-in-simple-dns-plus">this article</a>.</p>

<hr class="JHHR" />
<h3 id="lookup">Enhanced DNS Look Up tool</h3>

<p>New options pane docked in main window for quick and easy access, separate DNS and WHOIS server fields, new server port fields, and new DNSSEC options / output:</p>

<p><img height="462" src="img/90/9.png" width="631" /><br />
&nbsp;</p>

<hr class="JHHR" />
<h3 id="stdpi">New standard plug-ins</h3>

<ul>
	<li>New &quot;Skip&quot; plug-in.<br />
	Replaces &quot;Scheduler&quot; and &quot;Domain Whitelist&quot; plug-ins. <a href="https://simpledns.plus/plugin-skip">More details...</a></li>
	<li>New &quot;Fixed IP Address&quot; plug-in.<br />
	Returns a fixed IP address to all A/AAAA requests. <a href="https://simpledns.plus/plugin-fixedip">More details...</a></li>
	<li>New &quot;Fixed Host Name&quot; plug-in.<br />
	Returns a fixed host name - either as a CNAME record for all requests, or as MX/NS/PTR records. <a href="https://simpledns.plus/plugin-fixedhostname">More details...</a></li>
	<li>New &quot;Ignore DNS Request&quot; plug-in.<br />
	Instructs Simple DNS Plus to ignore (not answer) specified DNS requests. <a href="https://simpledns.plus/plugin-ignorereq">More details...</a><br />
	&nbsp;</li>
</ul>

<hr class="JHHR" />
<h3 id="misc">Miscellaneous updates / changes</h3>

<ul>
	<li>Runs on Windows 7&nbsp;and Windows 2008 R2.</li>
	<li>Support for DHCID records (RFC4701).</li>
	<li>Support for RFC4635 &quot;HMAC SHA TSIG Algorithm Identifiers&quot; - both for TSIG signed dynamic updates and for zone transfers.</li>
	<li>Active Log View can be paused (from main View menu / log right-click menu / F9 key).</li>
	<li>Options / DNS / Resolver / Caching: New separate setting for maximum cache time for negative responses.</li>
	<li>Options / DNS / Local Zones / Data Files: New &quot;Maximum TTL&quot; option.</li>
	<li>Options / DNS / Lame Requests: Default changed to &quot;Respond with a Refused error message&quot; (moved to top of list).</li>
	<li>New plug-in option: &quot;Perform DNS recursion for IP addresses listed by this plug-in&quot;.</li>
	<li>New plug-in option: &quot;Whitelist IP addresses listed by this plug-in from all DNSBLs&quot;.</li>
	<li>sdnsplus.exe is now dedicated to command line functions (no longer used to start Simple DNS Plus)&nbsp;and now also returns exit code 1 if a command line operation fails, which enables more advanced command line / PowerShell scripting scenarios.</li>
	<li>The New Zone wizard can now also create /8 and /16 reverse zones, and such existing zones are now recognized as reverse zones.</li>
	<li>DHCP plug-in: List of DHCP leases can now be exported to .csv and HTML (right-click menu in view).</li>
	<li>New Event ID 105 Error &quot;Failed to start remote management on &lt;ip-address&gt; port &lt;port&gt; (&lt;error&gt;)&quot;.</li>
	<li>New Event ID 140 Warning &quot;Open DNS Server. Limiting recursion to trusted IP addresses is recommended (Options dialog / DNS / Resolver / Recursion)&quot;.</li>
	<li>New Event ID 259 Warning &quot;Thread queue error for plug-in&quot;.</li>
	<li>New exception option for Non-Existing Domains feature: &quot;Do not redirect domain names that begin with an IPv4 address (reverse and RBL/DNSBL record names)&quot; (build 108).</li>
	<li>Added support for new &quot;Clone Answer&quot; plug-in interface. See&nbsp;<a href="https://simpledns.plus/plugin-cloneresponse">this article</a>&nbsp;(build 111).</li>
	<li>
	<div>Added option to either ignore or &quot;force TCP&quot; for UDP 'ANY' requests (Options dialog / DNS / Miscellaneous section), and to log / not log these requests - to deal with DNS reflection/amplification attacks (build 123).</div>
	</li>
	<li>
	<div>
	<div>Added new free educational license type.&nbsp;<a href="/kb/48/free-educational-licenses">Details</a>&nbsp;(build 132).</div>
	</div>
	</li>
</ul>

<hr class="JHHR" />
<h3 id="RFC">New RFC and draft support</h3>

<ul>
	<li><a href="http://www.rfc-editor.org/rfc/rfc3225.txt" target="_blank">RFC3225</a> - Indicating Resolver Support of DNSSEC (authoritative server)</li>
	<li><a href="http://www.rfc-editor.org/rfc/rfc4033.txt" target="_blank">RFC4033</a> - DNS Security Introduction and Requirements (signing and authoritative server)</li>
	<li><a href="http://www.rfc-editor.org/rfc/rfc4034.txt" target="_blank">RFC4034</a> - Resource Records for the DNS Security Extensions (signing and authoritative server)</li>
	<li><a href="http://www.rfc-editor.org/rfc/rfc4035.txt" target="_blank">RFC4035</a> - Protocol Modifications for the DNS Security Extensions (signing and authoritative server)</li>
	<li><a href="http://www.rfc-editor.org/rfc/rfc4635.txt" target="_blank">RFC4635</a> - HMAC SHA TSIG Algorithm Identifiers</li>
	<li><a href="http://www.rfc-editor.org/rfc/rfc4641.txt" target="_blank">RFC4641</a> - DNSSEC Operational Practices (signing and authoritative server)</li>
	<li><a href="http://www.rfc-editor.org/rfc/rfc4701.txt" target="_blank">RFC4701</a> - A DNS Resource Record (RR) for Encoding Dynamic Host Configuration Protocol (DHCP) Information (DHCID RR)</li>
	<li><a href="http://www.rfc-editor.org/rfc/rfc5155.txt" target="_blank">RFC5155</a> - DNS Security (DNSSEC) Hashed Authenticated Denial of Existence (signing and authoritative server)</li>
</ul>
