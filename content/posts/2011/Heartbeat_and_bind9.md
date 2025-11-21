---
title: "Heartbeat and bind9"
date: 2011-02-17T13:21:52+01:00
tags:
- debian
---

Using a virtual IP managed by heartbeat is a nice way to work around the slow
fallback behavior with multiple nameservers in /etc/hosts. But unlike ntpd,
bind9 doesn't automatically listen on new IPs on the system.

Here's a cute hack to fix that:

<pre>
# cat /etc/ha.d/haresources
server01 bind9release IPaddr::10.0.0.3 bind9takeover

# cat /etc/ha.d/resource.d/bind9release
#!/bin/sh
# when giving up resources, reload bind9
case $1 in
        stop) /etc/init.d/bind9 reload ;;
esac
exit 0

# cat /etc/ha.d/resource.d/bind9takeover
#!/bin/sh
# on takeover, reload bind9
case $1 in
        start) /etc/init.d/bind9 reload ;;
esac
exit 0
</pre>
