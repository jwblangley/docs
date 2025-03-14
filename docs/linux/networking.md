# Networking

## IP rules

The `iptables` command can be used to create IP rules such as dropping, rejecting, masquerading or forwarding packets that meet certain criteria.
This is how wireguard is configured.
It is important to note, however, that `iptables` rules only persist whilst the host is up and are lost at reboot.

A good alternative is the uncomplicated firewall of `ufw`, which uses `iptables` under the hood, but provides a more user-friendly interface and manages persistence of `iptables` rules.
A very important notice is that docker creates it's own `iptables` rules for it's own networking capabilities.
This happens in the layer before `ufw` and therefore `ufw` rules configured for endpoints that docker controls **will not take affect!**

`iptables` can be used for network address translation (or NAT).
Whilst this works perfectly for TCP connections that have state,
UDP packets are stateless, without additional software (such as a [STUN server](https://en.wikipedia.org/wiki/STUN)),
UDP packets cannot successfully be routes through NATs since they require full bidirectional communication before they are considered `ESTABLISHED` (at which point a NAT entry would suffice).
This can be confirmed using `conntrack` and wireshark.

### Choice of VPN software

There is a long-fought argument between Wireguard and OpenVPN.
I have personally had success with both, however since Wireguard makes use of a new network kernel interface (called `wg0`) NAT is as-good-as mandatory.
Due to the issues above with UDP and NAT, I prefer to use OpenVPN since it can be configured (without NAT) much more easily.
