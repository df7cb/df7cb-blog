---
title: "Cool Unix Features: stat"
date: 2010-02-17T13:21:52+01:00
tags:
- debian
- unix
---

"stat" is "date +format" for files:

    $ stat -c %s ~/me.jpg  # size
    520073
    $ stat -c %U ~/me.jpg  # owner
    cbe

No more parsing of "ls" output or similar hacks.

It also shows detailed information about files.

    $ stat ~/me.jpg
      File: „/home/cbe/me.jpg“
      Size: 520073          Blocks: 1024       IO Block: 4096   reguläre Datei
    Device: fe03h/65027d    Inode: 12427268    Links: 1
    Access: (0600/-rw-------)  Uid: ( 2062/     cbe)   Gid: ( 2062/     cbe)
    Access: 2010-06-06 12:58:07.000000000 +0200
    Modify: 2010-04-09 22:38:46.000000000 +0200
    Change: 2010-04-26 14:18:00.000000000 +0200

It supports similar features for stat'ing filesystems.
