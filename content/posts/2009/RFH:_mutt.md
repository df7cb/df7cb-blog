---
title: "RFH: mutt"
date: 2009-02-17T13:21:52+01:00
tags:
- debian
---

<pre>
From: Christoph Berg &lt;myon@debian.org&gt;
To: Debian Bugs Submit &lt;submit@bugs.debian.org&gt;
Subject: Bug#512072: RFH: mutt -- text-based mailreader supporting MIME, GPG, PGP and threading

Package: wnpp
</pre>

Hi,

the Debian Mutt package needs more maintainers.

There are almost 200 open bugs. Some of these are already forwarded
upstream and might just need some triaging/poking. Some need
forwarding. Some might be fixed with a trivial patch. Others are
Debian specific, mostly for the extra patches we include. There's
duplicates and sub-wishlist items. We are using bts-link to link to
dev.mutt.org's trac, but that also needs more tweaking.

There's a new upstream version 1.5.19 pending, we need people to check
which bugs still apply.

The (in?)famous mutt-patched package needs love to get the sidebar
patch updated to the new version, and to get some of mutt-ng's extra
gimmicks and add-ons integrated.

I've moved packaging to git since that seems to be the least scary
choice nowadays:

<a href="http://git.debian.org/?p=pkg-mutt/mutt.git">http://git.debian.org/?p=pkg-mutt/mutt.git</a>

The repository has been updated to 1.5.19. The mutt-patched build is
disabled for now, as the patch doesn't apply. Testers welcome :)

If you are interested in helping out, please get in contact with me.
To get started, subscribe to mutt's PTS feed. There's no extra
maintainer mailinglist, mailing mutt@packages.debian.org will work for
PTS subscribers. If you prefer IRC, join #mutt on irc.freenode.net.

Thanks, <br />
Christoph
