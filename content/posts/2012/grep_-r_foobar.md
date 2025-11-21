---
title: "grep -r foobar"
date: 2012-11-22T16:25:49+01:00
tags:
- debian
- unix
---

In Wheezy's grep version [1], you can omit the "." in

<pre>
$ grep -r foobar .
</pre>

and just write

<pre>
$ grep -r foobar
</pre>

[1] actually since 2.11
