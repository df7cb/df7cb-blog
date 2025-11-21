---
title: "PostgreSQL in Debian Hackathon"
date: 2012-08-27T14:21:08+02:00
tags:
- debian
- postgresql
---

Almost a year has passed since my talk at pgconf.eu 2011 in Amsterdam on
<a href="http://www.postgresql.eu/events/schedule/pgconfeu2011/session/166-connecting-the-debian-and-postgresql-worlds/">Connecting the Debian and PostgreSQL worlds</a>,
and unfortunately little has happened on that front, mostly due to my limited
spare time between family and job.
<a href="http://pgapt.debian.net/">pgapt.debian.net</a> is up and running, but
got few updates and is lagging behind on PostgreSQL releases.

Luckily, we got the project moving. <a href="http://tapoueh.org/blog/index.html">Dimitri Fontaine</a>
and <a href="http://blog.hagander.net/">Magnus Hagander</a> suggested to do a
face-to-face meeting, so we got together at my house for two days last week and
discussed ideas, repository layouts, build scripts, and whatnot to get all of
us aligned for pushing the project ahead. My
<a href="http://www.credativ.de/">employer</a> sponsored my time off work for
that. We almost finished moving the repository to postgresql.org
infrastructure, barring some questions of how to hook the repository into the
existing mirror infrastructure; this should get resolved this week.

The build server running Jenkins is still located on my laptop, but moving this
to a proper host will also happen really soon now. We are using
<a href="http://michael-prokop.at/blog/">Mika Prokop</a>'s
<a href="http://jenkins-debian-glue.org/">jenkins-debian-glue</a> scripts for
driving the package build from Jenkins. The big plus point about Jenkins is
that it makes executing jobs on different distributions and architectures in
parallel much easier than a bunch of homemade shell scripts could get us with
reasonable effort.

Here's a list of random points we discussed:

 * We decided to go for "pgdg" in version numbers and distribution names, i.e.
   packages will have version numbers like 9.1.5-1.pgdg+1, with distributions
   wheezy-pgdg, squeeze-pgdg, and so on.
 * There will be Debian-testing-style distributions called like
   wheezy-pgdg-testing that packages go into for some time before they get
   promoted to the "live" distributions.
 * PostgreSQL versions out of support (8.2 and below) will not be removed from
   the repository, but will be moved to distributions called like
   wheezy-pgdg-deprecated. People will still be able to use them, but the
   naming should make it clear that they should really be upgrading.
 * We have a slightly modified (compared to Debian unstable) postgresql-common
   package that sets the "supported-versions" to all versions supported by the
   PostgreSQL project. That will make the postgresql-server-dev-all package
   pull in build-dependencies for all server versions, and make extension
   module packages compile for all of them automatically. (Provided they are
   using pg_buildext.)
 * There's no Ubuntu support in there yet, but that's mostly only a matter of
   adding more cowbuilder chroots to the build jobs. TBD soon.

We really aim at using unmodified packages from Debian as much as possible, and
in fact this project doesn't mean to replace Debian's PostgreSQL packaging
work, but to extend it beyond the number of server versions (and Debian and
Ubuntu versions covered) supported. The people behind the Debian and Ubuntu
packages, and this repository are mostly the same, so we will claim that "our"
packages will be the same quality as the "original" ones. Big thanks go to
<a href="http://www.piware.de/">Martin Pitt</a> for maintaining the
postgresql-common testsuite that really covers every aspect of running
PostgreSQL servers on Debian/Ubuntu systems.

Stay tuned for updates! :)
