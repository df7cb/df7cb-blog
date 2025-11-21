[[!meta title="UDP port forwarding with iptables and ferm"]]

To talk to my IC-7610 via wireguard, I set up UDP port forwarding for ports 50001 50002 50003 on a raspi:

```
domain (ip) {
  table filter {
    chain FORWARD {
      policy ACCEPT;
    }
  }

  table nat {
    chain PREROUTING {
      interface (wg0) {
        proto udp dport 50001 DNAT to 192.168.0.6;
        proto udp dport 50002 DNAT to 192.168.0.6;
        proto udp dport 50003 DNAT to 192.168.0.6;
      }
    }

    chain POSTROUTING {
      outerface (eth0) {
        proto udp dport 50001 SNAT to-source 192.168.0.3;
        proto udp dport 50002 SNAT to-source 192.168.0.3;
        proto udp dport 50003 SNAT to-source 192.168.0.3;
      }
    }
  }
}
```

[[!tag afu]]
