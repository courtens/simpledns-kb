﻿---
title: Smart Reverse DNS plug-in
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2020-01-08
---
<p>With this plug-in, Simple DNS Plus can automatically synthesize reverse DNS records (PTR) for all the IP addresses (IPv4 or IPv6) in a subnet.</p>

<p>This can be used if you manage a large number of IP addresses, and you need to provide generic reverse DNS records for these.</p>

<p>The plug-in will respond with reverse DNS records pointing to a synthesized host name in the format &lt;prefix&gt;&lt;ip-address-&gt;&lt;suffix&gt;. Dots and colons in IP addresses are replaces with hyphens, and you can choose to either include the full IP address, or just the right part (as per subnet size).</p>

<p>For example with the prefix &quot;webserver-&quot;, the suffix &quot;.example.com&quot;, and a DNS request for reverse DNS records for IP address 1.2.3.4 (PTR for &quot;4.3.2.1.in-addr.arpa&quot;), a PTR record pointing to &quot;webserver-1-2-3-4.example.com&quot; would be synthesized.</p>

<p>In the plug-in instance dialog / Plug-In Settings tab you can specify the following settings (below image):</p>

<p><img src="img/187/1.png"  /></p>

<ul>
  <li><b>First IP address</b><br>
     The first IP address of the subnet that you want to provide reverse DNS records for.</li>
  <li><b>Subnet mask size</b><br>
     The mask size (in bits) of the subnet - larger the number = fewer IP addresses.</li>
  <li><b>Respond with PTR-record pointing to synthesized host name</b><br>
     - <b>Prefix (optional)</b><br>
         First part of the synthesized host name.<br/>
     - <b>IP address</b><br>
         How much of the IP address should be included in the synthesize host name. Choose "Full" or "Right part".<br/>
     - <b>Suffix</b><br>
         Last part of the synthesized host name.
     </li>
  <li><b>Response TTL</b><br>
    For how long other DNS servers may cache the provided PTR / A / AAAA records.</li>
  <li><b>Respond to requests for matching host records (A / AAAA)</b><br>
   Also respond to host record requests matching a host name that would be synthesized in PTR requests.</li>
</ul>