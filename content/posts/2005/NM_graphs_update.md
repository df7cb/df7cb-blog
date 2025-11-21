---
title: "NM graphs update"
date: 2005-02-17T13:21:52+01:00
tags:
- debian
---

I've updated my <a href="http://www.df7cb.de/debian/nm-graph/">NM graphs</a>.
There were some cases where the advocate and AM entries in the NM database
didn't match the Debian user name, so some people appeared with two different
names. There are still lots of unconnected components in the advocate graph,
which is because the "advocate" field in the NM database was added only later,
and the older entries all have "sunset" as advocate which I skip when
generating the graphs. If you want your advocate listed, or have advocated
someone back then, please tell me so I can add that to my scripts.

<p>
<a href="http://www.grep.be/blog/2005/03/07#christoph_berg_nm_graphs">Wouter</a>
mentioned that besides <a href="http://packages.debian.org/unstable/graphics/graphviz">neato</a>
there was <a href="http://packages.debian.org/unstable/graphics/springgraph">springgraph</a>
to create this type of graph. Coincidentally, I happened to adopt that package
last week and as upstream hasn't updated it for some years, I'm probably also
its new upstream. However, I haven't managed yet to produce any useful output
on the NM graphs with it yet (it's still chewing on advocate.dot while I'm
writing this), so I'll stick to neato for the time being. (Since graphviz is
now free, I don't have any qualms against doing so.)

<p>
On a sidenote, I'm wondering how many software patents I'm touching with these
scripts in our fine <a href="http://ue.eu.int/">banana republic</a>.
