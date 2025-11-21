0-$ bash  1$ bash  2*$ bash

If screen's default ^A w status line isn't really useful, put this in your bash prompt:

PS1='\\[\033k\u@\h\033\\\\\\] ...'

In other words, ESCk ESC\ sets the screen window title. This is independent
from the xterm title. Thanks to formorer for the pointer.

*Update:* fixed quoting in PS1

[[!tag debian]]
