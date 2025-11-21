---
title: "pgbouncer running on the same hardware"
date: 2012-11-30T08:52:40+01:00
tags:
- debian
- postgresql
---

We have a PostgreSQL server with 16 cores that was apparently running well
below its capacity: load something between 3.0 and 4.0, around 200 active
database connections, almost all always being &lt;IDLE&gt;. However, when the
tps count reached 7k transactions per second, things started to throttle, and
pgbouncer (running on the database server) started listing up to half of the
client connections to be in cl_waiting state. Load was still low, but
application performance was bad.

<img src="http://www.df7cb.de/blog/2012/renice_pgbouncer.png">

The culprit turned out to be the kernel scheduler, fairly distributing CPU time
among all running processes. There's one single pgbouncer process, but hundreds
of postgres processes.

A simple *renice* of the pgbouncer process did the trick and gave us another
extra 2k tps.
