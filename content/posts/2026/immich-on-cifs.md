---
title: "Running Immich on CIFS"
date: 2026-05-06T19:11:21+02:00
tags:
- notes
---

Some weeks ago I discovered [Immich](https://immich.app/) and was immediately
hooked and started feeding the family photo collection into it.

# Immich on CIFS

It's running on a VM at Hetzner, and I immediately filled up the disk with too
much data. Looking around, I discovered that Hetzner offers "storage boxes" at
the fraction of the cost of a VM with the same disk space, so I launched a 1 TB
instance there.

The Immich instance is rooted at /cb/immich/library/. In that directory, Immich
confusingly creates another "library" directory, which holds the actual
pictures, plus some more subdirectories.

There is now a cifs mount inside the outer library dir:

```
//u000000-sub1.your-storagebox.de/u000000-sub1 on /cb/immich/library/cifs type cifs
```

And a bunch of symlinks redirect some of the Immich directories to the remote server:

```
$ ls -l /cb/immich/library/
insgesamt 12
drwxr-xr-x 2 root root 4096 25. Mär 02:00 backups/
drwxr-xr-x 2 root root    0  2. Apr 18:18 cifs/
lrwxrwxrwx 1 root root   18 24. Mär 19:28 encoded-video -> cifs/encoded-video/
lrwxrwxrwx 1 root root   12 24. Mär 19:28 library -> cifs/library/
drwxr-xr-x 3 root root 4096 23. Mär 13:05 profile/
lrwxrwxrwx 1 root root   11  2. Apr 20:37 thumbs -> cifs/thumbs/
drwxr-xr-x 4 root root 4096 25. Mär 21:54 upload/
```

Initially I had planned to keep the "thumbs" directory on the local disk for
performance, but it outgrew the local disk pretty fast as well. (Perhaps I
should move the remaining two over as well...)

It's not the fastest setup, but it works and the storage space costs are very much ok.

# Immich on PostgreSQL

I already have a PostgreSQL instance running, so I didn't want Immich to create
another one. The official documentation mentions this is possible, but doesn't
detail out the instructions. Here's what I did:

1. In docker-compose.yml, removed the entire `database:` section.

2. In .env, use these database settings:

```
DB_PASSWORD=xxxxxxxxxxxx
DB_URL='postgresql://immich:xxxxxxxxxxxx@172.17.0.1/immich'
DB_DATABASE_NAME=immich
```

(Possibly DB_URL is enough, but the other two don't hurt.)

3. One complication was that the PostgreSQL running outside of Docker needs to
be reachable by Immich inside Docker, so I told it to use the Docker network
address `172.17.0.1`. PostgreSQL was already set to `listen_addresses='*'`, and
I just had to add a ufw firewall rule:

```
sudo ufw allow proto tcp from 172.17.0.0/16 to 0.0.0.0/0 port 5432
```

And a pg_hba.conf entry:

```
host    all             all             172.18.0.0/16           scram-sha-256
```
