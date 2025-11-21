---
title: "apt.postgresql.org"
date: 2012-12-07T10:31:58+01:00
tags:
- debian
- postgresql
---

So we finally made it, and sent out an 
<a href="http://archives.postgresql.org/pgsql-announce/2012-12/msg00008.php">official announcement</a> for
<a href="https://wiki.postgresql.org/wiki/Apt">apt.postgresql.org</a>.

This new repository hosts packages for all PostgreSQL server versions (at the
moment 8.3, 8.4, 9.0, 9.1, 9.2) for several Debian/Ubuntu distributions
(squeeze, wheezy, sid, precise) on two architectures (amd64, i386). Now add
packages for extension modules on top of all these, and you get a really large
amount of binaries from a small number of sources. Right now there's 1670 .deb
files and 148 .dsc files, but the .dsc count includes variants that only differ
in the version number per distribution (we attach .pgdg60+1 for squeeze
packages, .pgdg70+1 for wheezy and so on), so the real number of different
sources is rather something like 81, with 38 distinct source package names.

<a href="http://tapoueh.org/">Dimitri Fontaine</a>,
<a href="http://www.hagander.net/">Magnus Hagander</a>, and I have been working
on this since I first presented the idea at PGconf.EU 2011 in Amsterdam. We now
have a Jenkins server building all the packages, an archive server with the
master repository, and a feed that syncs the repository to the postgresql.org
FTP (well, mostly http) server.

If you were previously using pgapt.debian.net, that's the same archive as on
apt.postgresql.org (one rsync away). Please update your sources.list to point
to apt.postgresql.org, I'll shut down the archive at that location at the end
of January.

Here's the <a href="https://wiki.postgresql.org/wiki/Apt#Quickstart">Quickstart
instructions from the Wiki page</a>:

Import the repository key from http://apt.postgresql.org/pub/repos/apt/ACCC4CF8.asc:

<pre>
wget -O - http://apt.postgresql.org/pub/repos/apt/ACCC4CF8.asc | sudo apt-key add -
</pre>

Edit /etc/apt/sources.list.d/pgdg.list. The distributions are called codename-pgdg. In the example, replace squeeze with the actual distribution you are using:

<pre>
deb http://apt.postgresql.org/pub/repos/apt/ squeeze-pgdg main
</pre>

Configure apt's package pinning to prefer the PGDG packages over the Debian ones in /etc/apt/preferences.d/pgdg.pref:

<pre>
Package: *
Pin: release o=apt.postgresql.org
Pin-Priority: 500
</pre>

Note: this will replace all your Debian/Ubuntu packages with available packages from the PGDG repository. If you do not want this, skip this step.

Update the package lists, and install the pgdg-keyring package to automatically get repository key updates:

<pre>
apt-get update
apt-get install pgdg-keyring
</pre>
