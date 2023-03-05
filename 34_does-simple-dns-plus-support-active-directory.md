﻿---
title: Does Simple DNS Plus support Active Directory?
category: 5
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---

<div style="border: 1px solid black; background-color: #ffffc0;">
NOTE: Windows Server 2008 R2 has a bug which causes a "Bad DNS Packet" error when trying to setup Active Directory with Simple DNS Plus - for details and fix <a href="https://simpledns.plus/news/10">click here</a>.
</div>

<p>Yes, Simple DNS Plus supports both the "SRV" record type (required for AD) and "dynamic updates" (makes configuration with AD much easier).</p>
<p>The Windows Server will attempt to create the necessary DNS records through DNS dynamic updates - so by enabling this for the zone in which your network belongs, everything should be automatic.</p>
<p>To enable dynamic updates, in the Simple DNS Plus main window, click the "Records" button:</p>
<p><img src="img/34/1.png" width="318" height="141" /></p>
<p>Right-click a zone and select "Properties" from the pop-up menu:</p>
<p><img src="img/34/2.png" width="500" height="394" /></p>
<p>Select the "Dynamic Updates" tab, check "Accept Standard Dynamic Update requests", and make sure the Windows server IP address is included:</p>
<p><img src="img/34/3.png" width="426" height="467" /></p>
<p  style="text-align: left;">
Or you can add the required DNS records manually - but this can difficult, and we highly recommend the automatic setup through dynamic updates.<br />
<br />
For more details on the DNS records etc., please see the Microsoft document <a href="https://simpledns.plus/mskb/msad.pdf">"Configuring Non-Windows 2000 DNS Servers to Support Active Directory"</a>.</p>
<p>Note: Simple DNS Plus does not store its own data in Active Directory.</p>