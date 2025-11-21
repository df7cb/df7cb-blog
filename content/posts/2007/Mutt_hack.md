---
title: "Mutt hack"
date: 2007-02-17T13:21:52+01:00
tags:
- debian
---

When using a &lt;limit&gt; in mutt's message index, I always try to hit 'q' to
get back to the index view, but of course there's nothing to quit. The macro
below changes 'l' such that 'q' will unlimit, and a subsequent 'q' will then
quit mutt:

<pre>
macro index l '&lt;enter-command&gt;macro index q "&lt;limit\&gt;.&lt;enter\&gt;&lt;enter-command\&gt;bind index q quit&lt;enter\&gt;"&lt;enter&gt;&lt;limit&gt;' 'limit with quit enabled'
</pre>

(The weird \&gt; quotes trick the parser into not parsing &lt;fct&gt; in the
outer &lt;enter-command&gt; layer.)
