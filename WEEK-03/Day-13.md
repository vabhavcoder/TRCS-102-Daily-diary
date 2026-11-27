# Day 13 – Network Discovery Using Nmap

## Objective
Learn host discovery and interpret results within an authorized isolated network.

## Introduction
Nmap is a network discovery and security assessment tool. Host discovery identifies systems that respond to discovery probes. A missing response does not necessarily mean a system is offline, because firewalls and network configuration can affect results.

## Topics Covered

| Option | Purpose |
|---|---|
| `-sn` | Host discovery without port scanning. |
| `-n` | Disables reverse DNS resolution. |
| `-oN` | Saves normal text output. |

On a directly connected Ethernet network, Nmap may use ARP discovery. ICMP and other probes may be used depending on the environment and privileges.

## Practical Activity – Discovering a Lab Host
Verify the target address from the console of your own second VM. The example below assumes an isolated lab target at `192.168.56.10`; replace it with the verified address if different. Do not scan a shared campus, public or workplace network.

```bash
ip -br address
ping -c 4 192.168.56.10
nmap -sn -n 192.168.56.10 -oN discovery.txt
```

Compare the Nmap output with the target VM configuration. If discovery fails, inspect virtual adapter settings and IP configuration before repeating the test.

## Practical Evidence
Save discovery.txt and record the observed host state and any connectivity errors.

## Learning Outcomes
- Perform authorized host discovery.
- Interpret reachability.
- Distinguish discovery from port scanning.

## Conclusion
Learn host discovery and interpret results within an authorized isolated network. These concepts support responsible, evidence-based cybersecurity practice.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-12.md) | [Next Day →](Day-14.md)
