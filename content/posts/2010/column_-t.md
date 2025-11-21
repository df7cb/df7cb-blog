---
title: "Cool Unix Features: column -t"
date: 2010-02-17T13:21:52+01:00
tags:
- debian
- unix
---

*/etc/fstab* files tend to be an unreadable mess of unaligned fields.

    # /etc/fstab: static file system information.
    #
    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
    proc            /proc           proc    defaults        0       0
    /dev/mapper/benz-root /               ext3    errors=remount-ro 0       1
    /dev/sda1       /boot           ext3    defaults        0       2
    /dev/mapper/benz-home /home           ext3    defaults        0       2
    /dev/mapper/benz-swap_1 none            swap    sw              0       0
    newton:/home		/nfs		nfs	defaults,soft,intr,users	0 0
    /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Let's remove some whitespace in the third line:

    #<filesystem> <mountpoint>   <type>  <options>       <dump>  <pass>

And then pipe everything from line 3 to the end through *column -t*:

    # /etc/fstab: static file system information.
    #
    #<filesystem>            <mountpoint>   <type>       <options>                 <dump>  <pass>
    proc                     /proc          proc         defaults                  0       0
    /dev/mapper/benz-root    /              ext3         errors=remount-ro         0       1
    /dev/sda1                /boot          ext3         defaults                  0       2
    /dev/mapper/benz-home    /home          ext3         defaults                  0       2
    /dev/mapper/benz-swap_1  none           swap         sw                        0       0
    newton:/home             /nfs           nfs          defaults,soft,intr,users  0       0
    /dev/scd0                /media/cdrom0  udf,iso9660  user,noauto               0       0

Thanks to SP8472 for bringing this to my attention.
