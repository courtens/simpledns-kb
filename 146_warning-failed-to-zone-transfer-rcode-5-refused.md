﻿---
title: Warning: Failed to Zone Transfer ... (RCODE 5 Refused...)
category: 14
frontpage: false
comments: true
refs: 160
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>When you see this warning message (on the secondary DNS server), it is because the primary server is not allowing it to zone transfer (download) data for the zone.</p>
<p>The warning message will contain the name of the zone attempted transferred and the IP address of the primary DNS server. <br />
For example:<br />
*** Warning: Failed to Zone Transfer domain.com from 1.2.3.4 (RCODE 5 refused...)</p>
<p>First make sure that the zone name is spelled correctly and matches the name used on the primary server, and make sure that the IP address is the correct address of your primary DNS server.</p>
<p>Next make sure that the primary server allows the IP address of the secondary server to request zone transfers for the zone.</p>
<p>
<strong>IMPORTANT:</strong>
If the computer running your secondary DNS server has multiple IP addresses, then zone transfer requests may not originate from the same IP address as the secondary DNS server is configured to listen for inbound DNS requests on.<br />
You can configure which local IP address is used for outbound requests (including zone transfer requests) in the Options dialog / DNS / Outbound Requests section.<br />
You can check which IP address zone transfer requests originate from simply be looking in the Simple DNS Plus log on the primary server.</p>
<p>On a Simple DNS Plus primary server, there are 3 different settings which can affect zone transfer requests beeing allowed or not:</p>
<p>1) Options dialog / DNS / Zone Transfers:</p>
<p>
<img height="389" src="img/146/1.png" width="585" />
</p>
<p> IP addresses listed here are allowed to request zone transfers for all zones on this server.</p>
<p>2) If you are using the Super Master/Slave function:</p>
<p>
<img height="397" src="img/146/2.png" width="584" />
<br />
<br />
IP addresses in the &rdquo;Super Slaves&rdquo; list are allowed to request zone transfers for all primary zones on this server.</p>
<p>3) In the zone properties dialog for each individual zone:</p>
<p>
<img height="536" src="img/146/3.png" width="632" />
<br />
<br />
IP addresses specified here will be allowed to request zone transfers for this zone.</p>
<p>
<br />
The IP address of the secondary DNS server only needs to be included in one of these 3 settings to be allowed to request zone transfers for a zone.</p>