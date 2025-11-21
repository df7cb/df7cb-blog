There have been several long-term wishlist bugs on Mutt to include the
(in?)famous "sidebar" patch. It adds a panel on the left side of the screen to
list mailboxes with message counts.

<img src="http://www.df7cb.de/projects/mutt/sidebar/mutt-sidebar.png">

We do ship several patches with Debian's Mutt package that are not considered
for inclusion by the upstream authors, but this one is different. It touches
the core of the UI renderer and adds extensive counting of messages. There's
been quite a hype about the patch, it was even included in the (now
discontinued [1]) mutt-ng fork. Unfortunately, the patch was technically questionable, it
was written for the Mutt tarballs and didn't easily apply to CVS, and most
versions floating around contained lots of cruft like backup files and
temporary editor files. Furthermore, it is far from bug-free and even segfaults
occasionally.

Some months ago we decided we would build a second binary package to put the
patch in so we don't destabilize the standard package. Thanks Dann Frazier, we
got a clean patch, Adeodato had the right idea on how to build two binaries
from the same, differently-patched source (make install would run havoc, the
trick was to build the patched version *before* the regular one), and I
resolved some more involved conflicts with the maildir-mtime patch.

So, finally, there it is:
<a href="http://packages.debian.org/sid/mutt-patched">mutt-patched</a>.

*Disclaimer:* As said, there _are_ bugs. YMMV.

On related news, there's now also a -dbg package now for the victims of the
IMAP and header cache segfaults that we still see sometimes.

**Update:** The sidebar patch was not the reason for the creation of mutt-ng,
but many mutt-ng users were using it because of this patch.

**Update 2008-01-08:** [1] mutt-ng used to be a Mutt fork. It is now maintained
as a patch collection for Mutt.

[[!tag debian]]
