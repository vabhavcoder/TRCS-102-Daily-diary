# Day 20 – Incident Response and System Hardening

## Objective
Understand incident response, evidence handling and safe system hardening practices.

## Introduction
Incident response is a coordinated process for identifying, investigating, containing and recovering from security incidents. Preparation and lessons learned improve readiness for future events.

System hardening reduces unnecessary exposure by applying secure configurations, maintaining software, restricting permissions and disabling unneeded functionality. Hardening changes should be tested and documented because incorrect configurations can interrupt legitimate services.

## Topics Covered

| Response activity | Purpose |
|---|---|
| Preparation | Establish responsibilities, tools and procedures. |
| Detection and analysis | Validate alerts and determine scope and impact. |
| Containment | Limit further harm. |
| Eradication | Remove the cause of the incident. |
| Recovery | Restore and verify normal operations. |
| Lessons learned | Improve controls and response procedures. |

Evidence should be preserved with timestamps and integrity checks. Avoid deleting relevant records before investigation. For a WAF alert, review context before declaring an incident; a flagged request alone is not proof of compromise.

## Practical Activity – Hardening and Incident Response Exercise
Review your VM without disabling services or changing firewall rules:

```bash
ss -lntup
systemctl --failed
id
apt list --upgradable 2>/dev/null
```

The last command is for Debian-based systems and depends on package metadata. Review unnecessary services, update availability and account privileges. Record recommendations rather than applying unverified changes.

Practice file hardening using a new local test directory:

```bash
mkdir -p ~/defense-lab/hardening
cd ~/defense-lab/hardening
printf '%s\n' 'Synthetic incident evidence' > evidence.txt
ls -l evidence.txt
chmod 600 evidence.txt
ls -l evidence.txt
sha256sum evidence.txt > evidence.sha256
sha256sum -c evidence.sha256
```

Explain how restrictive permissions reduce access and how a hash can help verify file integrity against a trusted baseline.

## Tabletop Incident Response Scenario
A simulated WAF alert indicates repeated unusual requests to a lab web service. Draft a response plan: review the alert and related logs, establish whether the event is a genuine incident, contain affected services if necessary, identify and fix the cause, verify recovery, and document improvements. This is a hypothetical exercise, not a report of a real incident.

## Practical Evidence
Capture the permission changes and checksum verification output. Attach a completed tabletop response plan and record actual baseline observations. Do not claim remediation or incident recovery unless performed and verified.

## Learning Outcomes
- Explain the incident response process.
- Apply restrictive permissions to a test file.
- Verify evidence integrity and propose hardening measures.

## Conclusion
Incident response and hardening complement detection and deception by reducing exposure and supporting evidence-based recovery.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-19.md) | [Repository README →](../README.md)
