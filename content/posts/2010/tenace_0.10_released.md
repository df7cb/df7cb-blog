---
title: "tenace 0.10 released"
date: 2010-02-17T13:21:52+01:00
tags:
- bridge
- debian
---

It has been a while since the last update for <a href="http://www.df7cb.de/bridge/tenace/">tenace</a>,
my bridge hand viewer. The highlight in version 0.10 is version 2.0 of the double
dummy engine <a href="http://privat.bahnhof.se/wb758135/">dds</a> which has
been updated to support parallel computation in multiple threads. The parscore
computation in tenace now uses all available CPU cores. Even my notebook has
two CPUs :).

<img src="http://www.df7cb.de/bridge/tenace/img/tenace-0.10.png" border="0">

More on the technical side, the GUI has been switched to use GtkBuilder which
comes with Gtk so there is no external library needed anymore (previously
libglade). The looks are pretty much the same as before, though.

The previous version 0.9 had added windows support via mingw. I would still
appreciate if people could test it and tell me which bits I need to improve.
