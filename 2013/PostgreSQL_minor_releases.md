We've just put the new PostgreSQL minor releases live on apt.postgresql.org.
Building 5 major versions for 10 distributions produces quite a lot of stuff:

<ul>
<li>25 .dsc files (source packages)
<li>745 .deb files (360 *_amd64.deb + 360 *_i386.deb + 25 *_all.deb)
<li>497 MB in *_amd64.deb files
<li>488 MB in *_i386.deb files
<li>58 MB in *_all.deb files
<li>73 MB in *.orig.tar.bz2 files
<li>in total 1118 MB
</ul>

Compiling took a bit more than 10 hours on a 2-cpu VM. Of course that includes
running regression tests and the postgresql-common testsuite.

<b>Note:</b> This will be the last update published on pgapt.debian.net. Please
update your sources.list entries to point to apt.postgresql.org!

[[!tag debian postgresql]]
