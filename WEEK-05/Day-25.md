# Day 25 – Web Application Firewall and Reverse Proxy

## Objective
Understand WAF architecture and simulate defensive request classification.

## Introduction and Theoretical Concepts
A reverse proxy accepts client requests and forwards them to an upstream server. A Web Application Firewall (WAF) inspects HTTP traffic and applies security policies. Network firewalls primarily control network flows, while WAFs focus on application-layer traffic.

| Feature | Purpose |
|---|---|
| Request inspection | Examine relevant HTTP fields. |
| Signature rules | Identify known suspicious patterns. |
| Rate limiting | Restrict excessive request frequency. |
| Logging | Support investigation and monitoring. |
| Deception | Route selected suspicious traffic to an isolated decoy under a controlled policy. |

Conceptual project flow: Client → WAF/reverse proxy → legitimate application or isolated honeypot → security logs → dashboard. The SSH decoy is a separate service. False positives affect legitimate users; false negatives miss suspicious requests. A production WAF requires robust parsing, normalization, testing and secure upstream configuration.

## Practical Activity
Create `waf_demo.py` to classify synthetic events without network access:

```python
from collections import Counter

events = [
    {'path': '/home', 'signal': 'normal'},
    {'path': '/search', 'signal': 'injection_alert'},
    {'path': '/profile', 'signal': 'xss_alert'},
    {'path': '/files', 'signal': 'traversal_alert'},
    {'path': '/help', 'signal': 'normal'},
]
counts = Counter()
for event in events:
    action = 'allow' if event['signal'] == 'normal' else 'review_or_decoy'
    counts[action] += 1
    print(event['path'], event['signal'], action)
print(dict(counts))
```

Run `python3 waf_demo.py`. This models policy decisions using pre-labelled events; it does not detect attacks or forward traffic. Draw a diagram of the proposed WAF-honeypot architecture and describe how logs can connect detection decisions to a dashboard. Plan tests for benign traffic, suspicious alerts and false positives before implementing real forwarding in Week 06.

## Practical Evidence
Capture classification output and your architecture diagram. Label simulated events clearly; do not present them as real attack detections.

## Learning Outcomes
Differentiate firewalls and WAFs, explain reverse proxies and describe how deception and monitoring integrate with request filtering.

## Conclusion
Understand WAF architecture and simulate defensive request classification. The activity connects secure application design with the planned WAF-Honeypot project.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

---

## Navigation

[← Previous Day](Day-24.md) | [Next Day →](../WEEK-06/Day-26.md)
