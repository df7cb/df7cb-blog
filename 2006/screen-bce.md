[[!meta title="Today's screen hack: bce"]]


When you have trouble cut-and-pasting in screen because it copies full terminal
lines filled up with spaces, put the following into your .screenrc:

<pre>
defbce on
term screen-bce
</pre>

Ganneff reports that the first line is enough, and even works at the : prompt
of a running screen. Happy pasting :)

[[!tag debian]]
