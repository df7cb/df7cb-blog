---
title: "How not to edit files"
date: 2012-01-30T11:17:44+01:00
tags:
- debian
---

When packaging new backport versions, I diff the old Debian package with the
old backport package to extract the changes I did there, and then apply this
patch to the new version. There is always a reject in debian/changelog because
the topmost bpo entry won't apply cleanly to the new changelog. To fix this, I
invoke "vi debian/changelog*" and manually copy the rejected hunk.

Unfortunately, I regularly end up copying it from debian/changelog.rej
(buffer 3) into debian/changelog.orig (buffer 2) instead of debian/changelog
(buffer 1). Here's the fix in my .vimrc:

<pre>
" Prevent accidental editing of patch .orig files
autocmd BufRead *.orig set readonly
</pre>
