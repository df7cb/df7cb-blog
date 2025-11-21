---
title: "Unix Locking"
date: 2007-02-17T13:21:52+01:00
tags:
- debian
---

Note to myself: fcntl() locks vanish after a fork(). flock() works, but doesn't
work over NFS. Not that I care about the later, but sometimes I wonder why Unix
is so weird.
