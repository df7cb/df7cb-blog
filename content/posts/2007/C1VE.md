---
title: "C1VE"
date: 2007-02-17T13:21:52+01:00
tags:
- notes
---

Setting up X.org on a Sony PCG C1VE on Debian/etch:

 * dpkg-reconfigure xserver-xorg
 * ati
 * rest default
 * edit xorg.conf:
 * Section "Monitor": ModeLine "1024x480" 65.00 1024 1032 1176 1344 480 488 494 560 -hsync -vsync
 * Section "Screen", SubSection "Display": Modes "1024x480" ...
