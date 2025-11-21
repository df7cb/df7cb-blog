In contrast to chess, there is very little free software for bridge players.
Some <a href="http://packages.debian.org/sid/deal">deal</a>
<a href="http://packages.debian.org/sid/dealer">generators</a> have been around
for years, but basically, that was all.

Nowadays major online bridge site is
<a href="http://online.bridgebase.com/">bridgebase.com</a>. Their windows
client actually runs quite well in cedega (and wine), with the notable
exception that the built-in double dummy solver doesn't work there.
(A double dummy solver is a program that computes the optimal line of play
with all four hands open (both sides dummy), and hence can compute the
theoretically optimal score for a given board.)

Furthermore, viewing records of played boards is a bit tedious as launching the
viewer of course requires wine as well. Editing boards is not possible. This is
where I started writing some perl scripts that would at least dump the board
records as text files. At the same time I thought about doing something
interesting with Gnome's glade UI builder. Over the past two years, I have been
working on a GTK+ version of a bridge hand viewer and editor I called
<a href="http://www.df7cb.de/bridge/tenace/">*tenace*</a>.

When <a href="http://web.telia.com/~u07502278/">Bo Haglund</a> released his
double dummy solver library as GPL software, I
<a href="http://packages.debian.org/sid/libdds-dev">packaged</a> it for Debian
and worked on integration into tenace. It will compute "best" cards to play,
determine par scores.

Now tenace should be stable enough so I can risk announcing it to the world.

<img src="http://www.df7cb.de/bridge/tenace/img/tenace-0.6.png">

Coincidentally, the screenshot shows a board from last week's club
championships. East can beat 3NT by returning a Spade, but at my table they
didn't and so the board became my first squeeze hand :)

[[!tag bridge debian]]
