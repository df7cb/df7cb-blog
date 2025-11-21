---
title: "Cool Unix Features: /dev/full"
date: 2010-02-17T13:21:52+01:00
tags:
- debian
- unix
---

I've always thought about collecting random bits of useful/interesting/cool
Unix features and the like. Before I let that rot indefinitely in a text file
in my $HOME, I'll post it in a series of blog posts. So here's bit #1:

Everyone knows /dev/null, and most will know /dev/zero. But /dev/full was
unknown to me until some time ago. This device will respond to any write
request with ENOSPC, No space left on device. Handy if you want to test if your
program catches "disk full" - just let it write there:

    $ echo foo > /dev/full
    bash: echo: write error: No space left on device
