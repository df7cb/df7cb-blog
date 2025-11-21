---
title: "Datamining"
date: 2007-02-17T13:21:52+01:00
tags:
- irc
- debian
---

I'm just digging through OFTC's nickserv database to do some cleaning. We have
a bit over 20k nicknames in the database on 18k accounts which means about 10%
of registered nicks are linked to other master nicks.

By the power of sql, here's some statistics on the domain names of the
email addresses our users:

<pre>
com  9144
net  2241
org  1778
de   1016
uk    392
nl    288
fr    223
edu   217
au    203
it    193
br    190
ru    174
ca    165
se     88
dk     74
at     70
fi     62
cx     59
info   58
</pre>

<pre>
gmail.com             3997
hotmail.com           1405
yahoo.com              843
gmx.de                 221
gmx.net                201
web.de                 156
debian.org             148
free.fr                 94
aol.com                 90
msn.com                 73
comcast.net             72
gentoo.org              71
mail.ru                 65
xs4all.nl               59
linuxmail.org           58
verizon.net             57
yahoo.co.uk             54
yahoo.com.br            45
googlemail.com          45
student.uq.edu.au       44
sbcglobal.net           36
earthlink.net           33
users.sourceforge.net   32
</pre>

The numbers could use some aggregation as some providers use zillions of TLDs
(yahoo, gmx).

My personal favorite in there is <b>root@localhorst</b> :-)
