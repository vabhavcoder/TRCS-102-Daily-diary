# Day 11 – Introduction to Ethical Hacking

## Objective
Understand authorized security testing, its scope and professional responsibilities.

## Introduction
Ethical hacking is the authorized evaluation of systems to identify security weaknesses and recommend improvements. Permission, scope and responsible reporting distinguish legitimate testing from unauthorized intrusion.

## Topics Covered

| Concept | Description |
|---|---|
| Asset | A system, service or information requiring protection. |
| Threat | A potential cause of harm. |
| Vulnerability | A weakness that may be exploited. |
| Risk | Potential impact and likelihood of harm. |
| Control | A measure that reduces risk. |

## Testing Methodology
A typical assessment includes planning and authorization, information gathering, discovery, validation, reporting and remediation verification. Black-box testing uses limited prior knowledge, white-box testing uses detailed internal knowledge, and gray-box testing uses partial knowledge.

## Practical Activity – Establishing a Safe Lab
Use two personally controlled virtual machines on an isolated VirtualBox internal network. Document their roles, IP addresses and permitted testing activities. Avoid bridged networking for this exercise. Inspect the local configuration on each VM:

```bash
hostname
ip -br address
ip route
```

Define a scope that permits only discovery and non-destructive service inspection of the lab VMs. Specify excluded systems, stop conditions and evidence handling.

## Practical Evidence
Record the lab scope, VM names and actual interfaces. Attach a screenshot of the isolated network configuration.

## Learning Outcomes
- Explain authorization and scope.
- Distinguish threats, vulnerabilities and risks.
- Establish a controlled testing environment.

## Conclusion
Understand authorized security testing, its scope and professional responsibilities. These concepts support responsible, evidence-based cybersecurity practice.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](../WEEK-02/Day-10.md) | [Next Day →](Day-12.md)
