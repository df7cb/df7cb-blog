---
title: "NM finished"
date: 2005-02-17T13:21:52+01:00
tags:
- debian
---

The remaining parts of my NM process went through surprisingly well. Marc had
only a few points that I needed to clarify. He (HE) found some minor bugs in my
debian/rules files and a missing copyright attribution that I fixed this
evening. My application is now waiting for front desk approval. Thanks Marc for
being such a responsive AM!

<p>Afterwards, I went over the NM templates from alioth's CVS and corrected some
stuff that I had spotted while I was answering the questions. The patch is mostly
reformatting and grammar fixes, but got quite big:
<pre>
[0] cb@planck:~/debian/newmaint/templates $LC_ALL=C wc nm_* dak.txt | tail -1
  921  6452 39307 total
[0] cb@planck:~/debian/newmaint/templates $wc nm-templates.patch 
  918  6947 42773 nm-templates.patch
</pre>
Let's hope it helps future applicants.
