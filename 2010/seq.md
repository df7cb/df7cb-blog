[[!meta title="seq is nice, but ..."]]

    $ for i in `seq 1 40` ; do ./something $i ; done
    $ for i in $(seq 1 40) ; do ./something $i ; done

*seq* is nice for that, but the syntax feels a bit hard to type. If you don't
need sh compatibility (read: in bash/zsh), try:

    $ for i in {1..40} ; do ./something $i ; done

*PS: no spaces allowed*

*PS 2: another useful feature is prefixes/suffixes as in "touch {1..40}.txt"*

[[!tag debian unix]]
