---
title: "PostgreSQL 9.4 on Debian"
date: 2014-05-16T07:54:27+02:00
tags:
- postgresql
- debian
---

Yesterday saw the first beta release of the new PostgreSQL version 9.4. Along
with the sources, we uploaded binary packages to Debian experimental and
apt.postgresql.org, so there's now packages ready to be tested on Debian
wheezy, squeeze, testing/unstable, and Ubuntu trusty, saucy, precise, and
lucid.

If you are using one of the release distributions of Debian or Ubuntu, add this
to your /etc/apt/sources.list.d/pgdg.list to have 9.4 available:

deb http://apt.postgresql.org/pub/repos/apt/ codename-pgdg main 9.4

On Debian jessie and sid, install the packages from experimental.

Happy testing!
