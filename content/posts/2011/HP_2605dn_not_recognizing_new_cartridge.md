---
title: "HP 2605dn not regcognizing new cartridge"
date: 2011-02-17T13:21:52+01:00
tags:
- debian
---

When my wife bought her HP 2605dn color laser, she had also ordered a set of
replacement cartridges because the originals would supposedly not last very
long. It turned out that they would last over two years, though.

Now, the black cartridge was empty. The replacements are original HP
components, but recycled/refilled second hand from a different source. I put in
the black one, and the trouble started with the new drum having a big scratch
that would appear in every print. After two years, returning the cartridge was
not an option. As the old drum was still good, the idea was
to put the new toner into the old cartridge. A bit of googling (and visual
inspection) quickly revealed that you are not supposed to do this, the device
doesn't have any facilities to access anything.

Some post did indicate though that the cartridge actually consists of two parts
that are only held together by two pivot pins and two small springs. If you
pull the two parts apart a bit, you can feel the axis the parts are moving
around. So, I would try to use the old drum part with the new toner container
part.

Removing the springs is easy (also removing the flap covering the drum, along
with a tiny third spring). The two pivot pins are pretty inaccessible, but I
managed to pull out both using a pointy tong. One pin is made of metal, if you
need more space you can drill a small hole right next to it. The other pin is
made of plastic with a small hole in it, in one case I succeeded by screwing in
a little screw and pulling at it.

Reassembling the parts is not so hard. I put the "new" cartridge into the
printer, waited for the initialization to finish, only to find out the printer
would still think the cartridge was empty and should be replaced. Duh.

I then discovered a small chip attached to one corner of the drum unit,
probably carrying product ID and some serial number. Luckily, it was easy to
be removed and exchanged with the other drum unit. Still, the printer thought
the cartridge was empty. Some (windows) driver re-installations later it was
clear that there is no "ignore fill level and print anyway" option. (Cups
didn't print either.)

The HP Support Forum has a long
<a href="http://h30434.www3.hp.com/t5/Other-printing-questions/Ink-cartridge-empty-but-it-s-not/td-p/4101">Ink cartridge empty but it's not</a>
thread with lots of complaints but few answers. (Their problem is mostly with
new HP cartridges becoming "empty" after a few days.) Someone suggests trying
to cold reset the printer. For the 2605dn, that's holding the left and right
buttons while powering on. I removed the cartridges for doing so. When I had
put them back in, the printer asked me to confirm that non-HP material was
installed, and subsequently didn't display any fill level for the black
cartridge anymore, just "|?|" in the display.

Printing works now. Yay.

(Lesson learned: I still hate dealing with printers.)
