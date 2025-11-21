Five years after the release of patch 2.5.9, patch 2.6 was released two weeks
ago. The most interesting feature is that it will now produce reject files in
unified format when the input is in that format. Lucky for those of us whose
brain hurts when trying to read context diffs.

Of course there are more changes, and one of them is affecting Gentoo in particular:
<a href="http://blog.flameeyes.eu/2009/12/01/gentoo-service-announcement-keep-clear-of-gnu-patch-2-6">
Gentoo service announcement: keep clear of GNU patch-2.6</a>. The linked
<a href="http://bugs.gentoo.org/show_bug.cgi?id=293570">Gentoo bug #293570</a>
has attachments to reproduce the bug:

<pre>
benz:~/tmp/tripwire-2.3.1-2 $ patch -p0 -F3 < ../tripwire-friend-classes.patch
patching file tripwire-2.3.1-2-p1/src/fco/fconame.h
Hunk #1 succeeded at 48 with fuzz 3 (offset -1 lines).
patching file tripwire-2.3.1-2-p1/src/fco/fcosetimpl.h
Hunk #1 succeeded at 45 with fuzz 3 (offset -1 lines).
patching file tripwire-2.3.1-2-p1/src/tw/fcoreport.h
Hunk #1 succeeded at 84 with fuzz 3 (offset -1 lines).

benz:~/tmp/tripwire-2.3.1-2 $ ls -l
drwxr-xr-x 4 cbe credativ 4096 18. Nov 05:03 src/
drwxr-xr-x 3 cbe credativ 4096  2. Dez 12:23 tripwire-2.3.1-2-p1/
</pre>

Note that it created a new tripwire-2.3.1-2-p1 directory inside the existing
one, which is consistent with -p0. The newly created file contain just the "+"
lines from the patch. (There are no "-" lines.) patch 2.5.9 would have refused
the patch because it couldn't find the file to patch.

This is arguably a surprising behavior, but what really happens here is that
-F3 (fuzz 3) will explicitly tell patch to ignore 3 context lines if it cannot
apply the patch otherwise. diff's default behavior is to create patches with 3
lines of context. patch's default fuzz factor is one less than that, 2. Now, 3
- 3 is zero, which doesn't leave <i>any</i> context left.

Apparently lots of Gentoo ebuilds use -F3, and try to guess the correct number
of directories to strip, starting with -p0, -p1, ... No wonder that things
break badly for them now, as patches will suddenly succeed with -p0.

I'm not sure I like the new patch behavior, but in Gentoo's case I'd say they
are using way too much magic in their build system, and now get bitten by
options they shouldn't have put there in the first place.

[[!tag debian]]
