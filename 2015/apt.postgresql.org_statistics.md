At this year's FOSDEM I gave a talk in the PostgreSQL devroom
about <a href="http://www.df7cb.de/projects/talks/2015-FOSDEM/">
Large Scale Quality Assurance in the PostgreSQL Ecosystem</a>.
The talk included a graph about the growth of the
<a href="https://apt.postgresql.org/">apt.postgresql.org</a>
repository that I want to share here as well:

<img src="https://www.df7cb.de/blog/2015/apt-stats.png">

The yellow line at the very bottom is the number of different source package
names, currently 71. From that, a somewhat larger number of actual source
packages that include the "pgdgXX" version suffixes targeting the various
distributions we have is built (blue). The number of different binary package
names (green) is in about the same range. The dimension explosion then happens
for the actual number of binary packages (black, almost 8000) targeting all
distributions and architectures.

The red line is the total size of the pool/ directory, currently a bit less
than 6GB.

(The graphs sometimes decrease when packages in the -testing distributions are
promoted to the live distributions and the old live packages get removed.)

[[!tag postgresql debian]]
