# Day 26 – Firewall Fundamentals and Types

## Objective
Understand firewall policies, traffic direction and defense in depth.

## Introduction and Theoretical Concepts
A firewall enforces rules governing network communication. Inbound traffic enters a host or network, while outbound traffic leaves it. Rules may match source and destination addresses, protocols, ports and connection state.

| Type | Description |
|---|---|
| Packet filtering | Checks packet header fields. |
| Stateful firewall | Tracks connection state and permits traffic according to policy. |
| Proxy firewall | Intermediates communication at the application layer. |
| Host firewall | Protects an individual computer. |
| Network firewall | Controls traffic between network segments. |
| WAF | Inspects HTTP requests; complements rather than replaces a network firewall. |

A default-deny policy permits only explicitly authorized communication. Least privilege, rule ordering and logging reduce unnecessary exposure. A listening socket does not necessarily mean that a remote client can reach it.

## Practical Activity
Inspect the Linux VM without modifying its configuration:

```bash
ip -br address
ip route
ss -lntup
sudo iptables -S
```

In one terminal start a loopback-only HTTP service in an empty directory:

```bash
mkdir -p ~/firewall-lab
cd ~/firewall-lab
python3 -m http.server 8000 --bind 127.0.0.1
```

In another terminal run:

```bash
curl -I http://127.0.0.1:8000/
ss -lntp
```

Identify the listening address, protocol, port and client/server roles. Stop the server using Ctrl+C. Draft a policy permitting only required lab services, denying unnecessary inbound traffic and allowing established replies. Do not apply the draft to a live system.

## Practical Evidence
Capture the listening sockets and HTTP response; redact sensitive addresses if needed. Record which services were actually observed.

## Learning Outcomes
Explain firewall types, identify traffic direction and distinguish a listening port from an authorized network connection.

## Conclusion
Understand firewall policies, traffic direction and defense in depth. The exercise builds foundations for the planned WEEK-07 WAF-Honeypot project.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](../WEEK-05/Day-25.md) | [Next Day →](Day-27.md)
