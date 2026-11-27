# Day 12 – Reconnaissance and OSINT Fundamentals

## Objective
Differentiate passive and active reconnaissance and organize collected information responsibly.

## Introduction
Reconnaissance is the process of gathering information before a security assessment. Open-source intelligence (OSINT) involves collecting and evaluating publicly available information. Information should be verified and handled responsibly.

## Topics Covered

| Method | Description |
|---|---|
| Passive reconnaissance | Reviews existing information without directly probing the target. |
| Active reconnaissance | Interacts with a system to obtain information. |
| Source validation | Checks reliability, freshness and consistency. |
| Asset inventory | Records systems, services and ownership. |

Public information can be incomplete or outdated. DNS records, documentation and published service descriptions may reveal architectural information, but do not establish permission to test a system.

## Practical Activity – Local Asset Inventory
Inspect only your own Linux VM. Collect host information and review its local hostname records.

```bash
hostnamectl
cat /etc/os-release
cat /etc/hosts
ip -br address
ss -lnt
```

Create an inventory with columns for asset, address, operating system, observed service, evidence source and confidence. Compare the records with the VM settings. This local exercise demonstrates information collection, not a real-world OSINT investigation. Do not collect personal information about others.

## Practical Evidence
Attach a redacted inventory and terminal screenshot. Mark unverified information as unknown.

## Learning Outcomes
- Differentiate reconnaissance methods.
- Document assets.
- Evaluate information reliability.

## Conclusion
Differentiate passive and active reconnaissance and organize collected information responsibly. These concepts support responsible, evidence-based cybersecurity practice.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-11.md) | [Next Day →](Day-13.md)
