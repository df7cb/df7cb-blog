---
title: "Tab completion in vim"
date: 2011-09-19T14:09:16+02:00
tags:
- debian
---

Vim's habit of completing the full filename of the first match on :e has always
annoyed me. Rhonda pointed me to *wildmode* - thanks!

<pre>
set wildmode=longest,list:longest,list:full
</pre>
