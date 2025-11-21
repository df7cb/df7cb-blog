Soon after <a href="http://bzed.de/">Bernd Zeimetz</a> joined our company, he
infected me with the <a href="http://www.geocaching.com/">geocaching</a> virus.
In the meantime, I bought a GPS receiver, and am now endeavoring around the
town and the nearby woods, searching for caches.

There's not that much free GPS and/or geocaching software around. gpsd works
quite well, but I don't take my computer to the woods ;) Viking is very nice
for visualizing waypoints and sorting them in categories, but is still
somewhere between alpha and beta state. gpsbabel reads and writes a zillion
different file format and talks to a vast array of receivers, but often needs
several attempts to upload data to mine. Things are moving fast though and
the GPS community looks active.

Last week I started looking into
<a href="http://openstreetmap.org/">OpenStreetMap</a> and already added a few
roads in my neighborhood. Compared to commercial maps, there's still much to
do, especially for smaller tracks and features like foot bridges or woods
outside bigger cities. I'll keep collecting GPS data :) For the free software
side, neither OSM's online editor worked here (flash), nor the recommended tool
for local use (java), so I tried
<a href="http://www.irule.be/bvh/c++/merkaartor/">merkaartor</a> (qt4) which
works nicely. It also has some bugs, but feels very usable (though sometimes
slow). Starting from upstream's debian/ dir, building packages was
straightforward, and after some more editing, packages are now in unstable.
(The svn repository is in collab-maint, contributors welcome.)

[[!tag debian geocaching]]
