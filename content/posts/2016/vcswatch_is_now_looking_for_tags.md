---
title: "vcswatch is now looking for tags"
date: 2016-05-29T19:49:28+02:00
tags:
- debian
---

About a week ago, I extended
*<a href="https://qa.debian.org/cgi-bin/vcswatch">vcswatch</a>*
to also look at tags in git repositories.

Previously, it was solely paying attention to the version number in the top
paragraph in debian/changelog, and would alert if that version didn't match the
package version in Debian unstable or experimental. The idea is that *"UNRELEASED"*
versions will keep nagging the maintainer
(via <a href="https://qa.debian.org/developer.php">DDPO</a>)
not to forget that some day this package needs an upload. This works for git,
svn, bzr, hg, cvs, mtn, and darcs repositories (in decreasing order of actual
usage numbers in Debian. I had actually tried to add arch support as well, but
that VCS is so weird that it wasn't worth the trouble).

There are several shortcomings in that simple approach:

 * Some packages update debian/changelog only at release time, e.g. auto-generated from the git changelog using *git-dch*
 * Missing or misplaced release tags are not detected

The new mechanism fixes this for git repositories by also looking at the output
of *git describe --tags*. If there are any commits since the last tag, and the
vcswatch status according to debian/changelog would otherwise be *"OK"*, a new
status *"COMMITS"* is set. DDPO will report e.g. "1.4-1+2", to be read as "2
commits since the tag [debian/]1.4-1".

Of the 16644 packages using git in Debian, currently 7327 are "OK", 2649 are in
the new "COMMITS" state, and 4227 are "NEW". 723 are "OLD" and 79 are "UNREL"
which indicates that the package in Debian is ahead of the git repository. 1639
are in an ERROR state.

So far the new mechanism works for git only, but other VCSes could be added as
well.
