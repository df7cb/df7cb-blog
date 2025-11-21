---
title: "PostgreSQL Popularity Contest"
date: 2023-08-26T23:49:40+02:00
tags:
- postgresql
- debian
---

Back in 2015, when PostgreSQL 9.5 alpha 1 was released, I had posted the
<a href="https://www.df7cb.de/blog/2015/PostgreSQL_9.5_in_Debian.html">PostgreSQL data from Debian's popularity contest</a>.

8 years and 8 PostgreSQL releases later, the graph now looks like this:

<a href="https://qa.debian.org/popcon-graph.php?packages=postgresql+postgresql-7.4+postgresql-8.0+postgresql-8.1+postgresql-8.2+postgresql-8.3+postgresql-8.4+postgresql-9.0+postgresql-9.1+postgresql-9.2+postgresql-9.3+postgresql-9.4+postgresql-9.5+postgresql-9.6+postgresql-10+postgresql-11+postgresql-12+postgresql-13+postgresql-14+postgresql-15+postgresql-16&show_installed=on&want_legend=on&want_ticks=on&from_date=&to_date=&hlght_date=&date_fmt=%25Y-%25m&beenhere=1"><img src="https://www.df7cb.de/blog/2023/popcon-postgresql.png"></a>

Currently, the most popular PostgreSQL on Debian systems is still PostgreSQL 13 (shipped in Bullseye), followed by PostgreSQL 11 (Buster). At the time of writing,
PostgreSQL 9.6 (Stretch) and PostgreSQL 15 (Bookworm) share the third place, with 15 rising quickly.
