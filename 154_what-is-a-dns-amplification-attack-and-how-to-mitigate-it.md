﻿---
title: What is a DNS amplification attack and how to mitigate it
category: 7
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<div>In a DNS amplification attack,&nbsp;a large number of DNS request are sent with a spoofed from-IP-address to one or more DNS servers.<br />
Depending on configuration, these DNS servers will send a response back to the IP address that the request appeared to originate from.</div>

<div>&nbsp;</div>

<div>Typically the DNS request packets are designed to trigger a response packet which is larger than the original request packet - thus the &quot;amplification&quot;.</div>

<div>&nbsp;</div>

<div>The goal of the attack is to flood the victim (whoever owns the spoofed IP address) with large DNS response packets - ultimately overloading the victim's network / systems.<br />
&nbsp;</div>

<div>The DNS servers involved are simply used as relays, and because a large number of DNS servers are often used, the individual DNS servers owners may not notice any significant spike in traffic - perhaps as little as a few extra requests per second - even when involved in a massive attack.</div>

<div>&nbsp;</div>

<div>The victim of the attack is not be able tell where the attack originates from - to him it appears that the attackers are the DNS servers.</div>

<div>To the owners of the DNS servers (who may not even notice it) - it appears that the attacker is the victim - since the requests appear to originate from his IP address.</div>

<div>&nbsp;</div>

<div>When/if the owners of the abused DNS server notice this, they will typically see&nbsp;incoming DNS requests that are:<br />
a) Lame requests (recursive request for non local domain names from an IP address that the DNS servers does not recurse for)<br />
b) Requests for &lt;root&gt;</div>

<div>c) Requests for the record type &quot;ANY&quot; (logged as *).</div>

<div>
<div>d) Repeated requests from a single or a few IP addresses.&nbsp;</div>
</div>

<div>&nbsp;</div>

<div>We do <strong><span style="TEXT-DECORATION: underline">NOT</span></strong> recommend blocking the apparent sender's IP address on your firewall, with IPSec, or anything else at the IP address level - that is exactly what the attacker wants you to do! By blocking the apparent sender IP addresses, you are really blocking the victim rather than the attacker - because the sender IP address is spoofed as the victim's.&nbsp;</div>

<p>The aim of the attack is twofold: (1) overload the victim's Internet connection with large DNS responses, and (2) make everybody firewall the victim, so he can't use his connection even after the attack.<br />
<br />
As a DNS server owner, the best way to counter this type of attack is to make your DNS server unattractive as a &quot;way-point&quot;.</p>

<p>&nbsp;</p>

<p>There are 4 things you can do:&nbsp;</p>

<div>1) Make sure that you don't offer recursion to non local IP addresses (<a href="/kb/155/what-is-an-open-dns-server-and-how-do-i-fix-it">don't be an &quot;open DNS server&quot;</a>).</div>

<div>&nbsp;</div>

<div>In the Options dialog / DNS / Resolver / Recursion section, either turn off recursion completely if you don't need it, or limit it to your own IP address range(s):</div>

<p>&nbsp;</p>

<p><img src="img/154/1.png" /></p>

<p><br />
2)&nbsp;Configure Simple DNS Plus to either ignore or refuse lame requests.</p>

<p>&nbsp;</p>

<div>In the Lame Requests section, select either &quot;Respond with a Refused error message&quot; or &quot;Do not respond&quot;:</div>

<p>&nbsp;</p>

<p><br />
<img src="img/154/2.png" /></p>

<p>Generally we recommend using the &quot;Refused&quot; option as this makes it easier to troubleshoot other DNS issues. However if this attack is continuously hitting your server, you will do the victim a favor using the &quot;Do not respond&quot; option. When no longer under attack, you can switch to the &quot;Refused&quot; option which still ensures that your server is not attractive as a way-point for this type of attack - since it won't amplify traffic.<br />
<br />
<br />
3) If the requests are mostly for &lt;root&gt;, another way to deal with this traffic, and keep it out of the log at the same time, is setting the &quot;UDP requests for &lt;root&gt;&quot; option to &quot;Ignore (no response)&quot;&nbsp;-&nbsp;found in the Miscellaneous section:</p>

<p><img height="426" src="img/154/3.png" width="647" /></p>

<p><br />
4) If the requests are mostly for record type ANY (logged as *), you can set the &quot;UDP 'ANY' requests&quot; option to &quot;Ignore (no response)&quot; - also in the&nbsp;Miscellaneous section:</p>

<p><img height="426" src="img/154/4.png" width="647" /></p>