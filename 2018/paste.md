[[!meta title="Cool Unix Features: paste"]]

*paste* is one of those tools nobody uses [1]. It puts two file side by side,
line by line.

One application for this came up today where some tool was called for several
files at once and would spit out one line by file, but unfortunately not
including the filename.

    $ paste <(ls *.rpm) <(ls *.rpm | xargs -r rpm -q --queryformat '%{name} \n' -p)

[1] See "J" in <a href="http://ifaq.wap.org/computers/abcsofunix.html">The ABCs of Unix</a>

[*PS: I meant to blog this in 2011, but apparently never committed the file...*]

[[!tag debian unix]]
