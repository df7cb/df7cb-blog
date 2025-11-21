---
title: "Kudos to dh_python2"
date: 2011-07-12T12:33:43+02:00
tags:
- debian
---

Transitioning Python modules to dh_python2 is
<a href="http://wiki.debian.org/Python/TransitionToDHPython2">straightforward</a>.
I removed LOADS of magic from python-radix. I especially like the complexity reduction in
<a href="http://anonscm.debian.org/viewvc/python-modules/packages/py-radix/trunk/debian/rules?r1=17808&r2=17807&pathrev=17808">debian/rules</a>,
but debian/control also got some fields removed.
