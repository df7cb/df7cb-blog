Over the past few weeks, new distributions have been added on
<a href="http://apt.postgresql.org/">apt.postgresql.org</a>:
Ubuntu 13.10 codenamed "saucy" and the upcoming Ubuntu LTS release 14.04
codenamed "trusty".

Adding non-LTS releases for the benefit of developers using PostgreSQL on their
notebooks and desktop machines has been a frequently requested item since we
created the repository. I had some qualms about targeting a new Ubuntu release
every 6 months, but with having automated more and more parts of the repository
infrastructure, and the bootstrapping process now being painless, the
distributions are now available for use. Technically, trusty started as empty,
so it hasn't all packages yet, but of course all the PostgreSQL server packages
are there, along with pgAdmin. Saucy started as a copy of precise (12.04) so it
has all packages. Not all packages have been rebuilt for saucy, but the precise
packages included (you can tell by the version number ending in .pgdg12.4+12 or
.pgdg13.10+1) will work, unless apt complains about dependency problems. I have
rebuilt the packages needing it I was aware about (most notably the
postgresql-plperl packages) - if you spot problems, please let us know on the
mailing list.

Needless to say, last week's PostgreSQL server updates are already included in
the repository.

[[!tag postgresql debian]]
