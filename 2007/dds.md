[[!meta title="DDS: enter an open source double dummy solver"]]


In January I discovered Bo Haglund's double dummy solver, called
<a href="http://web.telia.com/~u88910365/">DDS</a>. I had been looking for an
open source solver running on Linux ever since I started playing Bridge, so
this was a very nice finding. It is very fast and the API is nicely documented.

<p> Of course, there are
<a href="http://packages.qa.debian.org/d/dds.html">Debian packages</a>, one for
the (static) library (libdds-dev), for the ddd driver frontend (renamed to dds
as there's already some other package called ddd), and for the python extension
(python-pydds).

<p> I am working on a GTK2 frontend called
<a href="http://www.df7cb.de/bridge/tenace/">tenace</a>. So far it features a
basic hand editor, can play cards, and compute double dummy/par scores. The
.lin import/export is not yet complete, but basically works.

[[!tag bridge]]
