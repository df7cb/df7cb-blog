---
title: "Generating symbols files from a series of .deb files"
date: 2011-12-27T18:40:05+01:00
tags:
- debian
---

PostgreSQL's libpq5 package got its symbols file somewhere around version 8.4,
so the symbols in there were all marked with version "8.4~" or greater. As I'm
working on <a href="http://pgapt.debian.net">pgapt.debian.net</a> aiming at
providing packages for all upstream-supported PG versions (currently 8.3 and
up), this made packages incompatible with 8.3's libpq5.

There didn't seem to be a ready program to feed a series of .deb files which
would then run dpkg-gensymbols and build a symbols file, so I wrote this shell
script:

<pre>
#!/bin/sh

set -eu

[ -d tmp ] || mkdir tmp

i=1

for pkg in "$@" ; do
	echo "$pkg"
	test -e "$pkg"
	name=$(dpkg-deb -I "$pkg" | perl -lne 'print $1 if /^ Package: (.+)/')
	version=$(dpkg-deb -I "$pkg" | perl -lne 'print $1 if /^ Version: (.+)/')
	out=$(printf "tmp/%03d_%s" $i "$version")
	dpkg-deb -x "$pkg" "$out"
	dpkg-gensymbols -P"$out" -p"$name" -v"$version" \
		${oldsymbols:+-I"$oldsymbols"} -O"$out.symbols" | \
		tee "$out.symbols.diff"
	test -s "$out.symbols.diff" || rm "$out.symbols.diff"
	oldsymbols="$out.symbols"
	rm -rf "$out"
	i=$(expr $i + 1)
done
</pre>

To use it, do the following:
<ul>
<li>debsnap -a i386 libpq5
<li>ls binary-libpq5/*.deb > files
<li>edit "files" to have proper ordering (~rc versions before releases, remove bpo versions, etc.)
<li>./walk-symbols $(cat files)
</ul>

The highest-numbered *.symbols file in tmp/ will then have symbol information
for all packages. I then did some manual post-processing like s/~rc1-1/~/ to
get nice (and backportable) version numbers.

Another nice trick (pointed out by jcristau) is to replace the lowest version
number of that package (8.2~ here, where libpq changed SONAME) by 0 which will
make dpkg-shlibdeps omit the &gt;= version part. (Most packages depending on
libpq5 will profit from that.)

I'm still pondering whether this script is non-trivial enough add to
devscripts. (The people I asked so far only made comments about the mkdir
call...)
