# Day 18 – Security Logging and Monitoring

## Objective
Understand security logs, event correlation and basic monitoring techniques.

## Introduction
Security logging records events that can help investigate failures, unauthorized access and abnormal activity. Monitoring reviews these records to identify trends and events requiring attention. Useful logs include timestamps, event types, outcomes and relevant context.

Centralized monitoring can combine records from multiple services. A security information and event management (SIEM) system supports collection, correlation, alerting and investigation. Logs must be protected from unauthorized modification and should not contain passwords, session tokens or unnecessary personal data.

## Topics Covered

| Log source | Typical information |
|---|---|
| Authentication logs | Login attempts and authentication outcomes. |
| System logs | Service events, warnings and errors. |
| Web access logs | Request paths, methods and response codes. |
| Firewall logs | Traffic matching configured logging rules. |
| Application logs | Application events and errors. |

Correlation combines related events, often using timestamps and identifiers. Retention policies balance investigation needs, storage and privacy.

## Practical Activity – Local Log Review and Synthetic Events
On a Linux VM using systemd, review recent entries:

```bash
journalctl -n 20 --no-pager
journalctl -p warning -n 10 --no-pager
systemctl --failed
```

Access may be limited by permissions. If journal logs are unavailable, continue using the synthetic exercise below.

```bash
mkdir -p ~/defense-lab
cd ~/defense-lab
printf '%s\n' 'INFO service_started' 'WARN login_failed' 'INFO request_allowed' 'WARN login_failed' 'ERROR service_timeout' > security-demo.log
cat security-demo.log
grep -n 'WARN' security-demo.log
grep -c 'login_failed' security-demo.log
tail -n 3 security-demo.log
```

Identify the event categories and count failed-login records. These records are deliberately synthetic and must not be described as actual attacks. Draft a log format for the WAF containing timestamp, request method, sanitized path, decision and reason. Avoid recording credentials or full sensitive request bodies.

## Practical Evidence
Capture the log review and filtered synthetic output. Record the actual count and explain which events would warrant further investigation. Redact sensitive information from real system logs.

## Learning Outcomes
- Identify common security log sources.
- Filter and count relevant events.
- Design privacy-conscious application logging.

## Conclusion
Reliable logs provide evidence for detection, troubleshooting and incident response when they are accurate, protected and interpreted in context.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-17.md) | [Next Day →](Day-19.md)
