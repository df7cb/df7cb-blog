---
title: "cfengine"
date: 2007-02-17T13:21:52+01:00
tags:
- debian
---

I've given the idea of centrally configuring my hosts another go. Previously I
had some meta packages that would pull in packages, but that's not very
interesting. Furthermore the archive I set up didn't scale, dpkg-scanpackages
plus makefiles aren't really fun to use.

Now, I have a set of cfengine scripts that gets distributed as .deb. That
sounds messy, but connecting reprepro with the right .dput.cf makes updating a
breeze.

cfengine itself is a beast not easily tamed. It has some weird ideas about
timeouts and when (not) to execute scripts. So far I'm only using "editfiles"
in this setup to do tweaks like comment HashKnownHosts in ssh_config, add some
sources.list entries, add %adm to sudoers, etc. Next step will be to also
automatically push config into chroots, and to pull passwd.db and friends for
use with libnss-db.
