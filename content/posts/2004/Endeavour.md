---
title: "Endeavour upload"
date: 2004-02-17T13:21:52+01:00
tags:
- debian
---

Alexander Wirt sponsored the 2.4.6-1 version of endeavour. The Makefile
previously defined CPP=g++, which works fine as long as you don't touch it. If
you do, you get weird breakages because suddenly the source is printed on
stdout. Then you notice that using CXX instead would be saner. Ouch. Thanks
Alex for uploading, and happy birthday!
