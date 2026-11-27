# Day 15 – Vulnerability Assessment and Network Defense

## Objective
Distinguish vulnerability assessment from penetration testing and document defensive recommendations.

## Introduction
Vulnerability assessment identifies and prioritizes security weaknesses. Penetration testing may additionally validate exploitability within an explicitly authorized scope. Automated findings require manual review because false positives and false negatives are possible.

## Topics Covered

| Concept | Description |
|---|---|
| CVE | Identifier for a publicly disclosed vulnerability. |
| CVSS | Framework for scoring vulnerability severity. |
| False positive | A reported issue that is not present. |
| Remediation | Removing or reducing a confirmed weakness. |

Severity is not identical to organizational risk: exposure, asset importance and existing controls also matter. Defense includes minimizing unnecessary services, applying updates, restricting access and reviewing logs.

## Practical Activity – Local Security Baseline
Review your own Linux VM without modifying firewall rules or disrupting services.

```bash
ss -lntup
ip -br address
systemctl --failed
apt list --upgradable 2>/dev/null
```

The final command applies to Debian-based systems and depends on available package metadata. On a system using systemd, inspect relevant local service logs if needed. Review each listening service and determine whether it is necessary, whether its bind address matches its intended use and whether updates are available. Do not treat every open port or available update as a confirmed vulnerability.

## Assessment Report Template

| Observation | Evidence | Risk rationale | Recommendation |
|---|---|---|---|
| To be recorded | Actual command output | Based on verified exposure | Appropriate corrective action |

Prioritize verified findings and retest after any authorized corrective action.

## Practical Evidence
Record actual listening services, update status and justified recommendations. Redact sensitive identifiers from screenshots.

## Learning Outcomes
- Differentiate assessment and penetration testing.
- Review local security posture.
- Prepare an evidence-based remediation report.

## Conclusion
Distinguish vulnerability assessment from penetration testing and document defensive recommendations. These concepts support responsible, evidence-based cybersecurity practice.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-14.md) | [Next Day →](../WEEK-04/Day-16.md)
