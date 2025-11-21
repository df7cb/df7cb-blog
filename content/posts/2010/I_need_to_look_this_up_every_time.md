---
title: "I need to look this up every time"
date: 2010-06-19T13:09:24+02:00
tags:
- debian
- unix
- notes
---

I need to look this up every time I need a backport (mostly PostgreSQL) at a
customer site with limited networking:

    $ lftp -c 'mget http://backports.debian.org/debian-backports/pool/main/p/postgresql-8.4/*_8.4.5-1~bpo50+1_amd64.deb'

Hopefully I can remember this in the future.
