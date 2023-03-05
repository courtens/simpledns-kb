﻿---
title: How to use domain names with international characters (IDN) in Simple DNS Plus and web-servers
category: 3
frontpage: false
comments: true
refs: 95,78
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>When you enter an IDN&nbsp;domain name&nbsp;in IE7 or Firefox, the browser will punycode-encode the domain&nbsp;name before sending it to the DNS server and web-server.<br />
The&nbsp;encoded form of the domain name contains only english letters (A-Z), numbers (0-9) and hyphens (-) ensuring that it is&nbsp;compatible with&nbsp;all DNS resolvers, DNS servers, web-servers, etc. without having to update those programs.<br />
So&nbsp;the DNS server and the web-server&nbsp;will only see the encoded form of the IDN domain name.<br />
For example a Japanese web address&nbsp;<img width="70" height="13" alt="www-tokyo-net.png" src="img/78/1.png" /> (the Japanese characters mean Tokyo) would be translated into www.xn--1lqs71d.net.<br />
(Note: only those segments of the name which contain international characters are actually encoded - leaving 'www' and 'net' in their original form in the previous example)</p>
<p>For example, if you enter <img width="70" height="13" alt="www-tokyo-net.png" src="img/78/2.png" />&nbsp;in the IE7:<br />
<img src="img/78/3.png" /></p>
<p>Simple DNS Plus will receive a DNS request for www.xn--1lqs71d.net, and&nbsp;resolve this:<br />
<img width="549" height="213" alt="1032a.png" src="img/78/4.png" /></p>
<p>If you click on the IDN button in IE, you will notice that it shows the same encoded address:<br />
<img width="419" height="373" alt="ie7-idn.png" src="img/78/5.png" /></p>
<p>If you are going to host DNS for this domain name in Simple DNS Plus:</p>
<p>In <strong><span style="text-decoration: underline;">Simple DNS Plus v. 5.0</span></strong>, you can enter the IDN directly, and it is automatically converted behind the scenes:</p>
<p><img width="425" height="160" alt="1032e.png" src="img/78/6.png" />		 </p>
<p>In <strong><span style="text-decoration: underline;">Simple DNS Plus v. 4.00 and earlier</span></strong> you must enter the encoded form:</p>
<p><img width="399" height="161" alt="1032b.png" src="img/78/7.png" />		 </p>
<p>And if you are hosting the web-site for the domain name, you must use the encoded form&nbsp;in the web-server configuration:<br />
<img width="482" height="374" alt="1032c.png" src="img/78/8.png" /></p>
<p><img width="517" height="278" alt="1032d.png" src="img/78/9.png" />		 </p>
<p>To convert your international domain name use our on-line <a href="https://simpledns.plus/idn-convert">IDN conversion Tool</a>.</p>
<p>IMPORTANT:&nbsp;IDN domain names&nbsp;are only supported by&nbsp;the most recent browser versions (Microsoft Internet Explorer&nbsp;7 /&nbsp;Firefox) and they are generally NOT yet supported by&nbsp;other&nbsp;applications such as e-mail clients.<br />
So keep in mind that if your website visitor uses an older browser&nbsp;version, he will not be able to access your web-site with the IDN domain name.</p>