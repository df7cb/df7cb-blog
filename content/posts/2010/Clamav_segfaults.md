---
title: "Clamav segfaults"
date: 2010-02-17T13:21:52+01:00
tags:
- debian
---

If you are still using clamav on etch, you might want to upgrade now:

<pre>
# /etc/init.d/clamav-daemon start  
Starting ClamAV daemon: clamd LibClamAV Warning: ***********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.     ***
LibClamAV Warning: *** DON'T PANIC! Read http://www.clamav.net/support/faq ***
LibClamAV Warning: ***********************************************************
/etc/init.d/clamav-daemon: line 240:  5221 Segmentation fault      start-stop-daemon --start -o -c $User --exec $DAEMON
 failed!
</pre>

Rolling back to yesterday's daily.cld fixes the issue, at least for the segfault.
