# Day 17 – Intrusion Detection and Prevention Systems

## Objective
Differentiate IDS and IPS and understand signature-based and anomaly-based detection.

## Introduction
An intrusion detection system (IDS) monitors activity and generates alerts when suspicious behavior is identified. An intrusion prevention system (IPS) can additionally take action, such as dropping traffic, when deployed in a position where it can enforce policy.

Network-based systems inspect network traffic, whereas host-based systems monitor activity on individual computers. Encrypted traffic can limit visibility into application content unless inspection occurs at an appropriate endpoint.

## Topics Covered

| Concept | Description |
|---|---|
| NIDS | Network-based intrusion detection. |
| HIDS | Host-based intrusion detection. |
| Signature detection | Matches known patterns of suspicious activity. |
| Anomaly detection | Identifies deviations from expected behavior. |
| False positive | Benign activity incorrectly flagged. |
| False negative | Suspicious activity not detected. |

An IDS generally alerts; an inline IPS may block. Detection policies require tuning to balance missed threats against unnecessary alerts. Suricata and Snort are examples of network security monitoring engines.

## Practical Activity – Simulating Signature Detection
Create a small local Python program that inspects synthetic event records. This is an educational simulation, not a production IDS or IPS.

Save as `ids_demo.py`:

```python
import re

events = [
    "LOGIN_SUCCESS user=labuser",
    "LOGIN_FAILED user=labuser",
    "HTTP_REQUEST path=/index.html",
    "LOGIN_FAILED user=demo"
]
pattern = re.compile(r"\bLOGIN_FAILED\b")
for event in events:
    if pattern.search(event):
        print("ALERT:", event)
    else:
        print("NORMAL:", event)
```

```bash
python3 ids_demo.py
```

Add one benign synthetic event and one failed-login event, then run the program again. Compare classifications with the known event labels. Explain why a single failed login is not proof of an intrusion. Consider how repeated failures, time windows and context could improve detection.

The program only labels events; it does not inspect live packets or block traffic. In the WAF project, request classification similarly needs careful validation before enforcement.

## Practical Evidence
Capture the source code and actual terminal output. Record expected versus observed labels and any false positives or false negatives in your test data.

## Learning Outcomes
- Differentiate IDS from IPS.
- Explain signature and anomaly detection.
- Implement and evaluate a simple alerting simulation.

## Conclusion
Detection identifies potentially suspicious behavior, while prevention requires an enforcement mechanism and a carefully tested policy.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-16.md) | [Next Day →](Day-18.md)
