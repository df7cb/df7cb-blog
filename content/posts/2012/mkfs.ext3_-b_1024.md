---
title: "mkfs.ext3 -b 1024"
date: 2012-10-01T15:21:08+02:00
tags:
- debian
---

If you think you are smart and create an ext filesystem with 1024 bytes
blocksize because there will be zillions of very small files, and then run into
ENOSPC errors while there's both space and inodes left, you will probably see
<a href="http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-05/msg08251.html">ext3\_dx\_add\_entry: Directory index full!</a>
in the kernel log.

Turns out that there's a limit of approximately 300,000 files per directory
with 1k blocks, after which some hash tables are full. Recreate the filesystem
with 2k blocks and the limit will be MUCH higher.
