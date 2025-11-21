---
title: "gpg --send"
date: 2007-02-17T13:21:52+01:00
tags:
- debian
---

Although I missed the deadline for the DC7 KSP, I just imported the keyring.
First I ran gpgsigs -r ksp-dc7.txt, and then gpg --import ksp-dc7.asc.
The result is scary:

<pre>
gpg: Total number processed: 182
gpg:               imported: 44  (RSA: 3)
gpg:              unchanged: 117
gpg:           new user IDs: 18
gpg:            new subkeys: 1
gpg:         new signatures: 64
</pre>

In other words, there are about 18 people who have added a a UID, but not sent
it to a keyserver. One key wasn't even there. This includes a fair number of
people whom I usually trust to handle such things more carefully. Please
consider running gpg --send :)

*Update:* On a closer look, at least one of the "new user IDs" was already
present on subkeys.pgp.net. Maybe my gpg was just to stupid to handle its own
keyrings. (The missing key was really not there, I've uploaded it in the
meantime.)
