When there a security update, just logging in to every host and issuing
"apt-get install $pkg" doesn't work as the package might not be installed
there. The fact that apt-get doesn't understand "apt-get upgrade $pkg" has
bugged me for a long time. Recent aptitude versions support that, but that's
not part of Lenny.

Here's a shell function that does the trick:

<pre>
upgrade () {
        if [ "$*" ] ; then
                set -- $(dpkg -l "$@" | grep ^ii | awk '{ print $2 }')
                if [ "$*" ] ; then
                        echo "apt-get install $@"
                        sudo apt-get install "$@"
                else
                        echo "Nothing to upgrade"
                fi
        else
                sudo apt-get upgrade
        fi
}
</pre>

One application is upgrading a lot of hosts when logged in with
<a href="http://packages.debian.org/sid/clusterssh">clusterssh</a>.

[[!tag debian]]
