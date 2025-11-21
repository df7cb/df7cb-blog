I need to look this up every time I need a backport (mostly PostgreSQL) at a
customer site with limited networking:

    $ lftp -c 'mget http://backports.debian.org/debian-backports/pool/main/p/postgresql-8.4/*_8.4.5-1~bpo50+1_amd64.deb'

Hopefully I can remember this in the future.

[[!tag debian unix notes]]
