Sometimes remote accounts are only reachable with a series of ssh/su/sudo
commands. Using ProxyCommands in .ssh/config works for simple cases, but not
with several hops, or if passwords have to be entered.

The <a href="http://packages.debian.org/sid/belier">belier</a> tool takes as
input a series of user@hostname strings and will produce an
<a href="http://packages.debian.org/sid/expect">expect</a> script that does
the actual login work.

<pre>
$ cat input
user@host1 root pw1
user2@host2 pw2

$ bel -e input

$ cat host2.sh
#!/usr/bin/expect -f
set timeout 10

spawn ssh -o NoHostAuthenticationForLocalhost=yes -o StrictHostKeyChecking=no  user@host1
expect -re  "(%|#|\\$) $"
send -- "su - root\r"
expect ":"
send -- "pw1\r"
expect -re  "(%|#|\\$) $"
send -- "ssh -o NoHostAuthenticationForLocalhost=yes -o StrictHostKeyChecking=no  user2@host2\r"
expect -re {@[^\n]*:}
send -- "pw2\r"
expect -re  "(%|#|\\$) $"
interact +++ return
</pre>

The generated host2.sh script uses ugly ssh options, but is easily edited.

Now I need the same thing for scp...

<b>Update:</b> Carl Chenet, belier's author, kindly pointed me to the
<a href="http://www.ohmytux.com/belier/documentation.html">documentation</a>
which has examples how belier can set up ssh tunnels to copy files.

[[!tag debian]]
