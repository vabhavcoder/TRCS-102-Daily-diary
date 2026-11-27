# Day 08 – IP Addressing and Subnetting

## Objective
Understand IPv4, IPv6, CIDR notation and basic subnet calculations.

## Introduction
IP addresses identify network interfaces for communication. Subnetting divides an address block into smaller networks, improving address allocation and enabling segmentation when combined with routing and access controls.

## Topics Covered
- **IPv4:** A 32-bit address written in dotted decimal notation.
- **IPv6:** A 128-bit address written in hexadecimal notation.
- **Subnet mask:** Identifies the network and host portions of an IPv4 address.
- **CIDR prefix:** Specifies the number of network bits, such as /24.
- **Network address:** Identifies an IPv4 subnet.
- **Broadcast address:** Addresses all hosts on a conventional IPv4 subnet.

## Common Private IPv4 Ranges

| Address block | CIDR |
|---|---|
| 10.0.0.0 – 10.255.255.255 | 10.0.0.0/8 |
| 172.16.0.0 – 172.31.255.255 | 172.16.0.0/12 |
| 192.168.0.0 – 192.168.255.255 | 192.168.0.0/16 |

Private addresses are not globally routable. NAT can translate addresses but is not a substitute for firewall rules.

## Solved Example
For `192.168.56.10/26`, the mask is `255.255.255.192`. Six host bits give 64 total addresses and 62 conventional usable host addresses.

| Parameter | Value |
|---|---|
| Network address | 192.168.56.0 |
| First usable address | 192.168.56.1 |
| Last usable address | 192.168.56.62 |
| Broadcast address | 192.168.56.63 |

The usual host-count formula is 2^host_bits − 2 for conventional IPv4 subnets; /31 and /32 are special cases.

## Practical Activity – Verify Subnet Calculations

```bash
ip -4 address show
ip -6 address show
python3 - <<'PY'
import ipaddress
n = ipaddress.ip_interface('192.168.56.10/26').network
print('Network:', n.network_address)
print('Mask:', n.netmask)
print('Broadcast:', n.broadcast_address)
print('Total addresses:', n.num_addresses)
print('Usable range:', n.network_address + 1, n.broadcast_address - 1)
PY
```

Repeat with `192.168.56.10/24` and compare the results. The example address is illustrative; no interface changes are required.

## Practical Evidence
Record the actual interface prefix and the output of both subnet calculations.

## Learning Outcomes
- Differentiate IPv4 and IPv6.
- Calculate network, broadcast and usable address ranges.
- Explain the role of subnetting in network segmentation.

## Conclusion
Addressing and subnetting are essential for understanding network boundaries and planning secure network layouts.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-07.md) | [Next Day →](Day-09.md)
