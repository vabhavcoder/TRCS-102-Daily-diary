# Day 06 – Introduction to Computer Networking

## Objective
Understand computer networks, their components, topologies and relevance to cybersecurity.

## Introduction
A computer network connects devices so they can exchange data and share resources. Understanding communication paths helps security professionals identify exposed services, investigate connectivity problems and design effective security controls.

## Topics Covered

| Network type | Description |
|---|---|
| PAN | Connects personal devices over a short distance. |
| LAN | Connects devices within a limited local area. |
| MAN | Covers a metropolitan area. |
| WAN | Connects networks across large geographical areas. |
| WLAN | Uses wireless communication within a local area. |

## Network Components
- **Switch:** Forwards Ethernet frames using MAC addresses.
- **Router:** Forwards IP packets between networks.
- **Access point:** Connects wireless clients to a network.
- **Firewall:** Controls network traffic according to security rules.
- **Network interface:** Allows a device to communicate over a network.
- **Default gateway:** Provides a route to destinations outside the local subnet.

## Network Topologies
Star connects devices to a central switch; bus uses a shared backbone; ring connects devices in a loop; mesh provides multiple paths. Modern Ethernet LANs commonly use a star topology.

## Practical Activity – Exploring a Local Network
Use a personally controlled Linux VM and inspect its configuration.

```bash
ip -br address
ip link show
ip route show
ping -c 4 127.0.0.1
```

Identify the interface name, IP address, prefix length and default gateway, if configured. Ping the gateway only if it belongs to your authorized lab. Loopback testing checks the local IP stack, not external connectivity.

## Practical Evidence
Record the actual interface, address, gateway and ping results. Attach a terminal screenshot with private details redacted where necessary.

## Learning Outcomes
- Differentiate common network types and topologies.
- Explain the functions of network devices.
- Identify local interfaces and routing information.

## Conclusion
Networking fundamentals provide the foundation for understanding network security and troubleshooting communication failures.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](../WEEK-01/Day-05.md) | [Next Day →](Day-07.md)
