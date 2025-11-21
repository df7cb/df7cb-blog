I have a small set of config files and cfengine scripts that I want to deploy
on every machine I own. Of course, the Debian way is to put them into a package,
and install that. So far so good.

Problems arise when trying to maintain this package on several different $HOME
directories - depending on where I am when I want a change. Using $vcs (svn in
this case) works, but I'd also like source packages. Only that I occasionally
forget where I put the repository. Or uploading new source packages is too
tedious.

The later problem was solved by a cute combination of dput and reprepro. My
.dput.cf has targets that rsync the package over to my server, and
automatically install the packages into the repository there.

For the repository problem, Stefano Zacchiroli's *debcheckout* comes to the
rescue. Vcs-Svn: in debian/control points to my svn+ssh:// repository. Instant
"DWIM" checkouts! (To actually make this work, the latest cfengine tweaks add
deb-src lines for my local repository that were previously missing.)

[[!tag debian]]
