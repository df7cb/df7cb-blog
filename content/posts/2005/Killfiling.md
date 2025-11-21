---
title: "Killfiling"
date: 2005-02-17T13:21:52+01:00
tags:
- debian
---

I don't like killfiles and /ignore mainly due to the fact that it's very
confusing to see only one side of a conversation afterwards. I'm using some
kind of "greylisting". For email, I have a procmail recipe that looks like:

<pre>
# killfile
:0fhw
* !^Status:
* ^From: .*<(noob@bla.com|luser@foo.org|troll@evil.net)>
| formail -i"Status: RO"
</pre>

This will mark the messages as read but leaves all threads intact. (I'm using
mbox folders.) That way, I'm not bothered to read the messages unless I really
want to.

<p>
In irssi, I have a /hide macro:

<pre>
hide    color set $0 15 ; color save
</pre>

Together with a
<a href="http://svn.df7cb.de/dotfiles/cb/.irssi/scripts/nickcolor.pl">patched
version of nickcolor.pl</a>, this will color the nick in light grey. Since that
is hardly readable on white background, I can only see which troll is talking
there if I have a close look.
