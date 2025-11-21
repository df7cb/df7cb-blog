---
title: "Looking for a Window Manager"
date: 2007-02-17T13:21:52+01:00
tags:
- debian
---

I had been using fvwm2 for some 10 years when around the beginning of this
year, I thought it might be time for a change. My config was originally copied
from some SuSE templates and then heavily tweaked over the years, but recently
broke more and more in subtle way with new fvwm upstream versions, e.g. moving
windows suddenly required a different mouse button. Probably the config was
just slightly out of spec and fvwm got "fixed", but it was annoying.

The "tiled" window managers I had seen on others' desktops made me curious, so
I gave ion3 a try some months ago. The overall appearance was all cool, but it
tried a bit too hard to squeeze all windows into tiled windows - of course
there's the floating workspace, but creating one was weird, and moving windows
even weirder. And if only the (default) key bindings were more vi-like... I
admit I never really bothered to read the documentation - probably everything
would have been much nicer otherwise.

Then there was the big license "wtf" with ion, at which point I started looking
around further. dwm looks clearly too l33t to be serious, so wmii was the next
choice, 3.1 to be exact. vi key bindings, a nicely configurable status bar, easy
workspace switching and window moving. wmii doesn't have horizontally split
windows (windows are always in columns), and no "tabbed" windows, though. It
didn't warp the pointer to the currently active window (something I got used to
with fvwm), but some config tweaks mostly fixed that. This time, I read the
documentation, but there's only a 10 page pdf beginners document, but there's
not much to configure anyway.

Then came lenny. Testing and unstable currently feature version 3.6 which is a
big disappointment. It is broken (the default config is unusable), and even
after fixing that, it looks like they removed all the little details that I
liked. The status bar is still there (though with a new location in the virtual
filesystem), the color cannot be changed anymore (unless changing some other
color as well). The windows used to have slim 1-pixel (configurable) borders.
Now they still have, but the border will be expanded if the window chooses a
different size - xterm always rounds down to the next character size, so all my
terminals have fat surroundings now. The last-active window in a inactive
column still had some markup so I knew which window Alt-Left/Right wound return
to, now I have to guess. I wouldn't mind fixing my 3.1 config for 3.6, but I
don't think I will, given these issues look unfixable. The 3.1 wmiirc file
looked like a sh script, the 3.6 uses eval and a bunch of functions that
frighten me. On a positive note, it is now possible to create new workspaces by
just selecting them, which is much handier than start-program, wait,
move-window-over, move-workspace.

I guess I will give ion (2, 3?) another try...
