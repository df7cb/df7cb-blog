---
title: "Cool Unix Features: /usr/bin/time"
date: 2012-03-21T09:45:42+01:00
tags:
- debian
- unix
---

Ever wondered how much memory a program needed? Install the "time" package:

<pre>
$ /usr/bin/time ls
[...]
0.00user 0.00system 0:00.00elapsed 0%CPU (0avgtext+0avgdata 4000maxresident)k
0inputs+0outputs (0major+311minor)pagefaults 0swaps
</pre>

Unfortunately the "time" bash built-in makes it necessary to use the full path.

Thanks to youam for the tip.

*Update:* aba notes that calling \time works as well. Thanks!
