---
title: "vcswatch and git --filter"
date: 2024-03-18T15:22:23+01:00
tags:
- debian
---

Debian is running a "<a href="https://qa.debian.org/cgi-bin/vcswatch">vcswatch</a>"
service that keeps track of the status of all packaging repositories that have a
<a href="https://www.debian.org/doc/manuals/developers-reference/best-pkging-practices.de.html#vcs"><tt>Vcs-Git</tt></a>
(and other VCSes) header set and shows which repos might need a package upload to push pending changes out.

Naturally, this is a lot of data and the scratch partition on qa.debian.org
had to be expanded several times, up to 300 GB in the last iteration.
Attempts to reduce that size using shallow clones (<tt>git clone --depth=50</tt>)
did not result more than a few percent of space saved. Running <tt>git gc</tt> on
all repos helps a bit, but is tedious and as Debian is growing, the repos are
still growing both in size and number. I ended up blocking all repos with
checkouts larger than a gigabyte, and still the only cure was expanding the
disk, or to lower the blocking threshold.

Since we only need a tiny bit of info from the repositories, namely the content
of <tt>debian/changelog</tt> and a few other files from <tt>debian/</tt>, plus
the number of commits since the last tag on the packaging branch, it made sense
to try to get the info without fetching a full repo clone. The question if we
could grab that solely using the GitLab API at salsa.debian.org was never
really answered. But then, in <a href="https://bugs.debian.org/1032623">#1032623</a>,
Gábor Németh suggested the use of
<a href="https://git-scm.com/docs/git-clone#Documentation/git-clone.txt---filterltfilter-specgt"><tt>git clone --filter blob:none</tt></a>.
As things go, this sat unattended in the bug report for almost a year until the
next "disk full" event made me give it a try.

The <tt>blob:none</tt> filter makes git clone omit all files, fetching only commit and
tree information. Any blob (file content) needed at git run time is
transparently fetched from the upstream repository, and stored locally. It
turned out to be a game-changer. The (largish) repositories I tried it on
shrank to 1/100 of the original size.

Poking around I figured we could even do better by using <tt>tree:0</tt> as
filter. This additionally omits all trees from the git clone, again only
fetching the information at run time when needed. Some of the larger repos I
tried it on shrank to <em>1/1000</em> of their original size.

I deployed the new option on qa.debian.org and scheduled all repositories to
fetch a new clone on the next scan:

<img src="https://www.df7cb.de/blog/2024/df-month.png">

The initial dip from 100% to 95% is my first "what happens if we block repos
&gt; 500 MB" attempt. Over the week after that, the git filter clones reduce the
overall disk consumption from almost 300 GB to 15 GB, a <em>1/20</em>. Some
repos shrank from GBs to below a MB.

Perhaps I should make all my git clones use one of the filters.
