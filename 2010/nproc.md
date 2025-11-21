[[!meta title="Cool Unix Features: nproc"]]

Since coreutils 8.1 (in Squeeze, not Lenny), there is a command that simply
prints out how many processors (cores, processing units) are available:

    $ nproc
    2

The use case is obvious:

    $ make -j $(nproc)

On a side note, this is gnulib's nproc module wrapped into a C program. If you
didn't know gnulib before (it had slipped my attention until recently), it is a
library of portability functions and other useful things. Adding it to a
project is simply done by calling gnulib-tool and tweaking a few lines in the
automake/whatever build scripts.

<i>PS: do not use nproc unconditionally in debian/rules. Parse
DEB\_BUILD\_OPTIONS for "parallel" instead.</i>

[[!tag debian unix]]
