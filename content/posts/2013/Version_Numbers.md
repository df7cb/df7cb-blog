---
title: "Version Numbers"
date: 2013-07-31T10:04:01+02:00
tags:
- debian
---

Following an idea by Ansgar Burchardt, I've done some digging on version numbers in Debian:

<p>
Most common version numbers:
<pre>
projectb=> select version::text, count(*) from source group by 1 order by 2 desc;
  version   | count 
------------+-------
 4:4.10.5-1 |   131
 1.0-1      |   120
 1.0.0-1    |    95
 1.1-1      |    95
 1.0.1-1    |    93
 1.2-1      |    88
 1.0-2      |    82
 0.2-1      |    80
 0.3-1      |    79
 0.5-1      |    77
 0.04-1     |    76
 1.1.1-1    |    76
 0.10-1     |    74
 1.4-1      |    72
 1.1-2      |    71
 0.1-1      |    70
 0.11-1     |    70
</pre>
</p>

<p>
Version number with the most spellings: (considered equal by the dpkg
definition, implemented in the "debversion" type)
<pre>
projectb=> select version::text, count(*) from source where version = '1.02-1' group by 1 order by 2 desc;
  version   | count 
------------+-------
 1.2-1      |    88
 1.02-1     |    46
 1.002-1    |     4
 1.000002-1 |     1
 001.002-1  |     1
 1.00002-1  |     1
</pre>
</p>

<p>
If we look at equivalent version numbers, the first table above looks entirely different:
<pre>
projectb=> select version, count(*) from source group by 1 order by 2 desc limit 30;
  version   | count 
------------+-------
 0.3-1      |   162
 1.0-1      |   160
 0.05-1     |   156
 0.04-1     |   154
 0.02-1     |   151
 1.02-1     |   141
 0.006-1    |   133
 1.001-1    |   131
 4:4.10.5-1 |   131
 0.7-1      |   127
</pre>
</p>

(I'm also participating in the "longest version number" contest, I've just uploaded bind9 version
<b>1:9.8.4.dfsg.P1-6+nmu2+deb7u1~bpo60+1</b> to backports.)
