At work, I'm dealing with lots of different database setups, luckily mostly
PostgreSQL running on Debian. At the same time, a fair amount of the tools in
the PostgreSQL ecosystem (not the PostgreSQL server packages itself) are not in
the best shape in the Debian archive.

I'm trying to change that by adopting some of the packages. So far, I have
fixed a few RC bugs where packages where suddenly trying to build against
PostgreSQL 9.0 while expecting 8.4. To my surprise, there are no packages yet
in the archive that support multiple PostgreSQL versions in parallel. There is
even a package ready to help doing this -
<a href="http://packages.debian.org/sid/postgresql-server-dev-all">postgresql-server-dev-all</a>,
but apparently nobody has used it yet. It turned out that after working around
a few trivial problems and adding just a few lines of sh code, it was pretty
straightforward
to port <a href="http://packages.qa.debian.org/s/skytools.html">skytools</a> and
<a href="http://packages.qa.debian.org/p/postgresql-pllua.html">postgresql-pllua</a>
to 9.0 while keeping 8.4 support. The latter has no version-specific code left
in debian/ except for a list of supported versions in debian/pgversions, so a
future port to 9.1 will be trivial. (Fun fact: the old postgresql-pllua version
0.8.1 was actually a typoed 0.3.1 version.)

Most PostgreSQL tools use a common
<a href="http://svn.debian.org/wsvn/pkg-postgresql/trunk/">subversion repository on Alioth</a>,
but there is no common mailing list address that is put into the Uploaders
fields, so it is hard to get an overview over the state of all packages. I've
compiled a list of all packages in svn, git, bzr (the server packages), and a
few others
<a href="http://qa.debian.org/developer.php?login=pkg-postgresql-public@lists.alioth.debian.org">in DDPO</a>
to fix that for now.

Other packages I've updated so far are
<a href="http://packages.qa.debian.org/p/pgtune.html">pgtune</a>,
<a href="http://packages.qa.debian.org/p/pgbouncer.html">pgbouncer</a>, and
<a href="http://packages.qa.debian.org/p/pgpool2.html">pgpool2</a>.

[[!tag debian postgresql]]
