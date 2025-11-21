---
title: "Incrementing DNS Zone Serials"
date: 2006-02-17T13:21:52+01:00
tags:
- debian
---


<pre>
$cat .vim/after/ftplugin/dns.vim
nmap _a !!perl -pe '($y,$m,$d) = (localtime)[5,4,3]; $d = sprintf("\%04d\%02d\%02d", $y+1900, $m+1, $d); s/\b(?\!$d)(\d{8})(\d{2})/${d}00/'&lt;cr&gt;&lt;c-a&gt;
</pre>
