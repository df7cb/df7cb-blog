---
title: "Spamassassin, RBLs, and Dialup"
date: 2006-02-17T13:21:52+01:00
tags:
- debian
---


I'm using SMTP over dialup to my smarthost. Unfortunately that doesn't stop spamassassin
to think I am a spammer:

<pre>
Received: from tesla.df7cb.de ([88.198.227.218] ident=postfix)
        by merkel.debian.org with esmtp (Exim 4.50) id 1Gm6h1-0001Fw-26
        for ???@qa.debian.org; Mon, 20 Nov 2006 03:48:03 -0700
Received: from volta.df7cb.de (dslb-084-058-218-241.pools.arcor-ip.net [84.58.218.241])
        by tesla.df7cb.de (Postfix) with ESMTP id 2F5364475D
        for &lt;???@qa.debian.org&gt;; Mon, 20 Nov 2006 11:48:24 +0100 (CET)
Received: by volta.df7cb.de (Postfix, from userid 1000)
        id BBABE18E95; Mon, 20 Nov 2006 11:49:32 +0100 (CET)

 0.1 FORGED_RCVD_HELO       Received: contains a forged HELO
 0.1 RCVD_IN_SORBS_DUL      RBL: SORBS: sent directly from dynamic IP address
                            [84.58.218.241 listed in dnsbl.sorbs.net]
 1.8 RCVD_IN_BL_SPAMCOP_NET RBL: Received via a relay in bl.spamcop.net
               [Blocked - see &lt;http://www.spamcop.net/bl.shtml?70.103.162.29&gt;]
 2.5 RCVD_IN_XBL            RBL: Received via a relay in Spamhaus XBL
                            [84.58.218.241 listed in sbl-xbl.spamhaus.org]
 1.7 RCVD_IN_NJABL_DUL      RBL: NJABL: dialup sender did non-local SMTP
                            [84.58.218.241 listed in combined.njabl.org]
</pre>

My previous solution was to use an openvpn tunnel to the smarthost, but my
current one (provided by <a href="http://www.flexserv.de/blog">codebreaker</a>)
is a vserver, so that doesn't work. <a href="http://ganneff.de/blog">Ganneff</a>
provided the workaround: make postfix drop the Received: header.

<pre>
[0] cb@tesla:~ $grep header /etc/postfix/main.cf
header_checks = pcre:/etc/postfix/header_checks

[0] cb@tesla:~ $cat /etc/postfix/header_checks
/^Received: from [a-z]*\.df7cb\.de \(dslb-[0-9.-]*\.pools\.arcor-ip\.net/ IGNORE

Received: from tesla.df7cb.de ([88.198.227.218] ident=postfix)
        by merkel.debian.org with esmtp (Exim 4.50) id 1GmX3t-0000Pw-4I
        for ???@qa.debian.org; Tue, 21 Nov 2006 07:57:27 -0700
Received: by volta.df7cb.de (Postfix, from userid 1000)
        id 69AB218EAC; Tue, 21 Nov 2006 15:58:57 +0100 (CET)
</pre>

Of course this is a gross hack, but I'm happy with it :)
