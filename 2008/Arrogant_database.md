Imagine every Unix command would...

<pre>
$ mysqladmin foo 2>&1 | hd
00000000  07 6d 79 73 71 6c 61 64  6d 69 6e 3a 20 63 6f 6e  |.mysqladmin: con|
</pre>

... prepend ^G to its error messages.

[[!tag debian]]
