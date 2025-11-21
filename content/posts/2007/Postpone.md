---
title: "Postpone"
date: 2007-02-17T13:21:52+01:00
tags:
- debian
---

I just finished implementing
<a href="http://www.df7cb.de/projects/postpone/">postpone</a>, a wrapper that
is intended to take an arbitrary command, fork into the background, wait until
some lockfile is freed, and then run the command. Of course the idea is that
the lockfile is /var/lib/dpkg/lock, and that postpone is used in maintainer
scripts. (Update-menus already does that, and I've basically grabbed that code
and generalized it as a separate program.)

As a test implementation, I <a href="http://www.df7cb.de/projects/postpone/texlive/">modified
the post{inst,rm} templates in the tex-common package</a> and rebuilt
texlive-lang-* using that. dpkg -i texlive-lang-*.deb takes over 4 minutes in
the old version, but only a total of 60s with postpone used (35s for dpkg -i
plus 25s for the background jobs).

A Debian package is currently sitting in NEW, let's hope it will actually get
used in maintainer scripts.
