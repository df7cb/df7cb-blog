[[!meta title="Jessie, the HP 6715b, and Wifi"]]

If you are upgrading your HP/Compaq 6715b to Debian Jessie, and suddenly Wifi
stops working because the PCI device is gone, install the "rfkill" package:

<pre>
# lspci | tail -2
02:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 02)
10:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

# rfkill list 1
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

# rfkill unblock wifi

# rfkill list 1
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

# lspci | tail -2
10:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
30:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 02)
</pre>

Reports on the internet say that the same could be done by going into the BIOS
and selecting "Reset to default" - this makes the Wifi LED active until about
udev is started on the next boot.

To be done: figure out how to automate this.

[[!tag debian]]
