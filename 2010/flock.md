[[!meta title="Cool Unix Features: flock"]]

Lockfiles are usually hard to get right, especially in sh scripts. The best bet
so far was "lockfile" included with procmail, but its semantics are pretty
weird. (Try to understand what exit code you want, with or without "-!".) Not
to mention that failing to clean up the lockfile will stop the next cron run,
etc.

Since Lenny, util-linux ships "flock". Now you simply say

    $ flock /path/to/lockfile /path/to/command

and are done. If you want it non-blocking, add "-n":

    $ flock -n /path/to/lockfile /path/to/command

I should probably migrate all my cronjobs to use this.

[[!tag debian unix]]
