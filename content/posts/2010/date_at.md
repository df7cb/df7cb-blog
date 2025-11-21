---
title: "Cool Unix Features: date -d @"
date: 2010-02-17T13:21:52+01:00
tags:
- debian
- unix
---

I've always been annoyed about how hard it is to convert seconds-since-epoch to
strings. I've always been using "date -d '1970-01-01 + 1234 sec'", but as it
turned out, that's wrong because it uses the wrong timezone. Luckily, there's a
slick replacement:

    $ date -d '@1234'
    Do 1. Jan 01:20:34 CET 1970

The right version of the "long" version is:

    $ date -d '1970-01-01 UTC + 1234 sec'
    Do 1. Jan 01:20:34 CET 1970
