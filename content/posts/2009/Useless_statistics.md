---
title: "Useless statistics"
date: 2009-02-17T13:21:52+01:00
tags:
- debian
---

<pre>
projectb =>
SELECT
        array_accum(SUBSTRING(source FROM 1 FOR 1)) AS first,
        SUBSTRING(source FROM 2) AS rest
FROM
        (SELECT DISTINCT source FROM source) AS source
GROUP BY rest
HAVING
        COUNT(SUBSTRING(source FROM 1 FOR 1)) >= 4
ORDER BY rest;

        first        |  rest
---------------------+---------
 {c,f,j,l,p,s}       | am
 {a,g,n,y}           | ap
 {c,d,p,r,t,x}       | ar
 {b,d,l,s}           | ash
 {h,i,l,n,r,v}       | at
 {b,m,r,s}           | c
 {g,j,p,x}           | cal
 {e,g,p,x}           | cb
 {d,j,k,n,t}         | cc
 {a,f,i,v}           | check
 {a,d,e,g,m,u}       | cl
 {e,j,n,q,u,x}       | d
 {e,g,l,t,x}         | db
 {c,d,r,s}           | dd
 {j,l,o,u}           | de
 {f,g,l,s,w,x}       | dm
 {a,l,p,u}           | dns
 {e,l,n,q,r}         | e
 {j,s,t,x}           | ed
 {g,l,m,n}           | edit
 {c,e,f,x}           | fingerd
 {b,d,l,p,x}         | fm
 {g,k,p,y}           | forth
 {c,g,j,l}           | ftp
 {b,g,m,o,p}         | identd
 {f,k,t,v,z}         | ile
 {s,u,v,z}           | im
 {b,d,m,s,w}         | ing
 {b,g,w,z}           | ip
 {j,l,s,t}           | irc
 {a,c,f,j,u}         | lex
 {e,p,s,z}           | lib
 {f,k,r,x}           | log
 {i,m,o,q,s,v}       | m
 {c,q,s,w,x}         | mail
 {c,d,h,m,o,p,s,t,x} | make
 {e,i,l,x}           | mms
 {b,g,x,z}           | oo
 {b,c,r,s}           | play
 {e,f,g,r}           | pm
 {g,p,t,w,x}         | pp
 {i,q,w,x}           | print
 {a,b,m,o}           | sc
 {b,c,d,k,p,z}       | sh
 {a,f,p,x}           | sp
 {a,h,s,x}           | t
 {g,u,x,y}           | talk
 {a,e,i,k,q,w,x}     | term
 {a,h,i,m,n,p}       | top
 {c,k,q,r}           | torrent
 {a,h,l,n,o}         | tp
 {g,i,j,o}           | ts
 {c,j,n,o,r}         | unit
 {f,g,l,p,w}         | v
 {c,k,p,r}           | vm
 {i,l,n,s,x}         | watch
 {9,b,d,j,l,p,t}     | wm
 {g,j,r,w,x}         | zip
(58 Zeilen)
</pre>

... and the winner is *make*!
