Today saw the release of PostgreSQL 9.5 Alpha 1. Packages for all supported
Debian and Ubuntu releases are available on <a href="http://apt.postgresql.org/">apt.postgresql.org</a>:

<tt>
deb http://apt.postgresql.org/pub/repos/apt/ <i>YOUR_RELEASE_HERE</i>-pgdg main 9.5
</tt>

The package is also waiting in NEW to be accepted for Debian experimental.

Being curious which PostgreSQL releases have been in use over time, I pulled some graphics
from <a href="https://qa.debian.org/popcon-graph.php?packages=postgresql+postgresql-7.4+postgresql-8.0+postgresql-8.1+postgresql-8.2+postgresql-8.3+postgresql-8.4+postgresql-9.0+postgresql-9.1+postgresql-9.2+postgresql-9.3+postgresql-9.4+postgresql-9.5&show_installed=on&want_legend=on&want_ticks=on&from_date=&to_date=&hlght_date=&date_fmt=%25Y-%25m&beenhere=1">Debian's popularity contest data</a>:

<a href="https://qa.debian.org/popcon-graph.php?packages=postgresql+postgresql-7.4+postgresql-8.0+postgresql-8.1+postgresql-8.2+postgresql-8.3+postgresql-8.4+postgresql-9.0+postgresql-9.1+postgresql-9.2+postgresql-9.3+postgresql-9.4+postgresql-9.5&show_installed=on&want_legend=on&want_ticks=on&from_date=&to_date=&hlght_date=&date_fmt=%25Y-%25m&beenhere=1"><img src="https://www.df7cb.de/blog/2015/popcon-postgresql.png"></a>

Before we included the PostgreSQL major version in the package name,
"postgresql" contained the server, so that line represents the installation
count of the pre-7.4 releases at the left end of the graph.

Interestingly, 7.4 reached its installation peak well past 8.1's. Does anyone have an
idea why that happened?

[[!tag postgresql debian]]
