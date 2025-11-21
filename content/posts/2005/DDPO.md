---
title: "Hacking DDPO"
date: 2005-02-17T13:21:52+01:00
tags:
- debian
---

Over the last few weeks, I've implemented some new features in
<a href="http://qa.debian.org/developer.php">DDPO</a>. The system, originally
written by Igor Genibel, is a mix of Python, Perl, and PHP generated from WML,
so it's quite interesting to see how these languages interact.

<p>
The main new features are the ability to add arbitrary packages to the list
displayed, and an automatic listing of all NMUs and sponsored uploads in the
new "uploads" section. (Thanks to Ryan Murray, Joerg Jaspert, and Joey Schulze
for helping fix the projectb for that!) I won't repeat the details here, read
the <a href="http://lists.debian.org/debian-devel-announce/2005/11/msg00015.html">d-d-a
posting</a> for that. Another nice thing is the link to
<a href="http://people.debian.org/~igloo/popcon-graphs/index.php">Ian Lynagh's
popcon graphs</a> which I had mostly ignored so far.

<p>
Have a look at my <a href="http://qa.debian.org/developer.php?login=myon">DDPO
page</a> to see the new features - feedback welcome!
