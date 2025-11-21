On RedHat/CentOS/rpm systems, there's no <i>dpkg --compare-versions</i>
available - <i>sort -V</i> can help to compare version numbers:

    version_lt () {
        newest=$( ( echo "$1"; echo "$2" ) | sort -V | tail -n1)
        [ "$1" != "$newest" ]
    }

    $ version_lt 1.5 1.1 && echo yes
    $ version_lt 1.5 1.10 && echo yes
    yes

[[!tag debian]]
