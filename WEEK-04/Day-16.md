# Day 16 – Introduction to Defensive Security

## Objective
Understand defensive security, defense-in-depth and the relationship between security controls and risk.

## Introduction
Defensive security protects systems, networks and information against unauthorized access, disruption and misuse. Its purpose is to prevent incidents where possible, detect suspicious behavior and recover safely when prevention fails.

Defense-in-depth combines multiple independent controls so that failure of one safeguard does not immediately expose the entire system. For example, a web application can be protected by a network firewall, a reverse proxy, application input validation and security monitoring.

## Topics Covered

| Concept | Description |
|---|---|
| Preventive control | Reduces the likelihood of an incident, such as access restrictions. |
| Detective control | Identifies suspicious activity, such as log monitoring. |
| Corrective control | Restores or improves security after an incident, such as patching. |
| Least privilege | Grants only the permissions needed for a task. |
| Attack surface | All exposed interfaces and functions that could be targeted. |
| Defense-in-depth | Uses multiple complementary layers of protection. |

Technical controls include firewalls, authentication and endpoint protection. Administrative controls include policies and training, while physical controls protect facilities and equipment. A control should be selected according to the asset, threat and potential impact.

## Practical Activity – Defensive Security Baseline
Use a personally controlled Debian or Kali VM. Inspect the current configuration without changing it.

```bash
whoami
id
ip -br address
ss -lntup
systemctl --failed
```

Identify the current account, interfaces, listening services and failed services. Some process details may require administrator privileges. A listening port is not automatically a vulnerability; evaluate its intended purpose and exposure.

Create a defense-in-depth plan for a sample web server:

| Layer | Proposed control | Purpose |
|---|---|---|
| Network | Restrict unnecessary inbound ports | Reduce exposure |
| Application | Validate incoming requests | Reduce malicious input |
| Host | Least privilege and updates | Limit damage |
| Monitoring | Review security logs | Detect unusual events |

Relate these layers to the planned WAF-honeypot project: the firewall limits network access, the WAF inspects web requests, and monitoring records security events.

## Practical Evidence
Attach a screenshot of the terminal showing the baseline commands and a completed control table. Record actual observations and distinguish proposed controls from controls already enabled.

## Learning Outcomes
- Explain preventive, detective and corrective controls.
- Identify basic host exposure and security layers.
- Design a defense-in-depth plan for a web service.

## Conclusion
Effective defense combines preventive measures, monitoring and recovery rather than depending on a single security product.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](../WEEK-03/Day-15.md) | [Next Day →](Day-17.md)
