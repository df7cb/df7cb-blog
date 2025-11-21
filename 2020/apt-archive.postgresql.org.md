[[!meta title="Announcing apt-archive.postgresql.org"]]

Users had often asked where they could find older versions of packages from
<a href="https://apt.postgresql.org/">apt.postgresql.org</a>. I had been
collecting these since about April 2013, and in July 2016, I made the packages
available via an ad-hoc URL on the repository master host, called "the morgue".
There was little repository structure, all files belonging to a source package
were stuffed into a single directory, no matter what distribution they belonged
to. Besides this not being particularly accessible for users, the main problem
was the ever-increasing need for more disk space on the repository host. We are
now at 175 GB for the archive, of which 152 GB is for the morgue.

Our friends from <a href="https://yum.postgresql.org/">yum.postgresql.org</a>
have had a proper archive host (yum-archive.postgresql.org) for some time
already, so it was about time to follow suit and implement a proper archive
for apt.postgresql.org as well, usable from apt.

So here it is:
<b><a href="https://apt-archive.postgresql.org/">apt-archive.postgresql.org</a></b>

The archive covers all past and current Debian and Ubuntu distributions. The
apt sources.lists entries are similar to the main repository, just with "-archive"
appended to the host name and the
<a href="https://apt-archive.postgresql.org/pub/repos/apt/dists/index.html">distribution</a>:

<pre>
deb https://apt-archive.postgresql.org/pub/repos/apt DIST-pgdg-archive main
deb-src https://apt-archive.postgresql.org/pub/repos/apt DIST-pgdg-archive main
</pre>

The oldest PostgreSQL server versions covered there are 8.2.23, 8.3.23, 8.4.17,
9.0.13, 9.1.9, 9.2.4, 9.3beta1, and everything newer.

Some example:
<pre>
$ apt-cache policy postgresql-12
postgresql-12:
  Installed: 12.2-2.pgdg+1+b1
  Candidate: 12.2-2.pgdg+1+b1
  Version table:
 *** 12.2-2.pgdg+1+b1 900
        500 http://apt.postgresql.org/pub/repos/apt sid-pgdg/main amd64 Packages
        500 https://apt-archive.postgresql.org/pub/repos/apt sid-pgdg-archive/main amd64 Packages
        100 /var/lib/dpkg/status
     12.2-2.pgdg+1 500
        500 https://apt-archive.postgresql.org/pub/repos/apt sid-pgdg-archive/main amd64 Packages
     12.2-1.pgdg+1 500
        500 https://apt-archive.postgresql.org/pub/repos/apt sid-pgdg-archive/main amd64 Packages
     12.1-2.pgdg+1 500
        500 https://apt-archive.postgresql.org/pub/repos/apt sid-pgdg-archive/main amd64 Packages
     12.1-1.pgdg+1 500
        500 https://apt-archive.postgresql.org/pub/repos/apt sid-pgdg-archive/main amd64 Packages
     12.0-2.pgdg+1 500
        500 https://apt-archive.postgresql.org/pub/repos/apt sid-pgdg-archive/main amd64 Packages
     12.0-1.pgdg+1 500
        500 https://apt-archive.postgresql.org/pub/repos/apt sid-pgdg-archive/main amd64 Packages
     12~rc1-1.pgdg+1 500
        500 https://apt-archive.postgresql.org/pub/repos/apt sid-pgdg-archive/main amd64 Packages
     12~beta4-1.pgdg+1 500
        500 https://apt-archive.postgresql.org/pub/repos/apt sid-pgdg-archive/main amd64 Packages
     12~beta3-1.pgdg+1 500
        500 https://apt-archive.postgresql.org/pub/repos/apt sid-pgdg-archive/main amd64 Packages
     12~beta2-1.pgdg+1 500
        500 https://apt-archive.postgresql.org/pub/repos/apt sid-pgdg-archive/main amd64 Packages
     12~beta1-1.pgdg+1 500
        500 https://apt-archive.postgresql.org/pub/repos/apt sid-pgdg-archive/main amd64 Packages
</pre>

Because this is hosted on S3, browsing directories is only supported indirectly by
static index.html files, so if you want to look at some specific URL, append
"/index.html" to see it.

The archive is powered by a
<a href="https://git.postgresql.org/gitweb/?p=pgapt.git;a=tree;f=pgapt-db/sql">PostgreSQL database</a> and a
<a href="https://git.postgresql.org/gitweb/?p=pgapt.git;a=tree;f=repo/bin">bunch of python/shell scripts</a>,
from which the apt index files are built.

<h2>Archiving old distributions</h2>

I'm also using the opportunity to remove some long-retired distributions from the main
repository host. The following distributions have been moved over:

<ul>
<li>Debian etch (4.0)</li>
<li>Debian lenny (5.0)</li>
<li>Debian squeeze (6.0)</li>
<li>Ubuntu lucid (10.04)</li>
<li>Ubuntu saucy (13.10)</li>
<li>Ubuntu utopic (14.10)</li>
<li>Ubuntu wily (15.10)</li>
<li>Ubuntu zesty (17.04)</li>
<li>Ubuntu cosmic (18.10)</li>
</ul>

They are available as "<em>DIST</em>-pgdg" from the archive, e.g. squeeze:

<pre>
deb https://apt-archive.postgresql.org/pub/repos/apt squeeze-pgdg main
deb-src https://apt-archive.postgresql.org/pub/repos/apt squeeze-pgdg main
</pre>

[[!tag debian postgresql]]
