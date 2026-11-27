# Day 09 – Network Protocols, Ports and Commands

## Objective
Understand common network protocols, transport ports and basic diagnostic commands.

## Introduction
Protocols define rules for communication. Ports identify transport-layer endpoints, allowing multiple applications to communicate through the same IP address.

## Topics Covered

| Protocol | Common port / transport | Purpose |
|---|---|---|
| HTTP | 80/TCP | Web communication |
| HTTPS | 443/TCP; HTTP/3 uses UDP | Encrypted web communication |
| SSH | 22/TCP | Secure remote administration |
| DNS | 53/UDP or TCP | Name resolution |
| DHCPv4 | 67, 68/UDP | Automatic address configuration |
| SMTP | 25/TCP | Mail transfer |
| FTP | 21/TCP (control) | File transfer |
| ICMP | No transport port | Network diagnostics and error reporting |

These are conventional defaults; services can use different ports.

## TCP and UDP
TCP provides reliable, ordered byte-stream delivery using connections, acknowledgments and retransmission. Its connection establishment normally uses SYN, SYN-ACK and ACK. UDP provides connectionless datagrams without built-in delivery or ordering guarantees.

## Practical Activity – Network Diagnostics

| Command | Purpose |
|---|---|
| `ip route` | View routing table |
| `ss -tuln` | Display listening TCP and UDP sockets |
| `ip neigh` | View neighbor cache |
| `ping -c 4 127.0.0.1` | Test loopback connectivity |
| `getent hosts localhost` | Inspect local hostname resolution |
| `traceroute -n 127.0.0.1` | Demonstrate route tracing if installed |

Start the local HTTP server from Day 07 and execute:

```bash
ss -ltn
curl -I http://127.0.0.1:8000/
```

Identify the listening port and HTTP status. Stop the server after testing. A listening port alone does not prove that the service is reachable from other devices; interface binding and firewall rules also matter.

## Practical Evidence
Record the actual listening sockets, HTTP status and diagnostic output. Note any unavailable commands rather than inventing results.

## Learning Outcomes
- Explain the differences between TCP and UDP.
- Identify common protocol and port associations.
- Interpret basic Linux network diagnostic commands.

## Conclusion
Protocol and port knowledge helps identify legitimate services and understand network exposure.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-08.md) | [Next Day →](Day-10.md)
