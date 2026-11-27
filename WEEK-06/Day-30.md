# Day 30 – Python Security Automation

## Objective
Use regular expressions, HTTP requests and structured log analysis for defensive automation.

## Introduction and Theoretical Concepts
Security automation transforms repetitive checks into reproducible scripts. Regular expressions can identify structured patterns, but are not a complete attack detection mechanism. HTTP clients can check service availability, response status and headers. Structured logs improve filtering and aggregation. Timeouts, error handling and explicit scope are important. A successful HTTP status does not prove that a service is secure.

## Practical Activity
Start a local HTTP server from an empty directory using `python3 -m http.server 8000 --bind 127.0.0.1`. In another terminal create `security_check.py`:

```python
import re
from collections import Counter
from urllib.request import urlopen
from urllib.error import URLError

records = [
    "status=200 path=/home",
    "status=403 path=/admin",
    "status=404 path=/missing",
    "status=403 path=/private",
]
pattern = re.compile(r"\bstatus=(\d{3})\b")
counts = Counter()
for record in records:
    match = pattern.search(record)
    if match:
        counts[match.group(1)] += 1
print("Synthetic status summary:", dict(counts))
print("Denied requests:", counts["403"])

try:
    with urlopen("http://127.0.0.1:8000/", timeout=5) as response:
        print("Local HTTP status:", response.status)
        print("Content type:", response.headers.get("Content-Type"))
except (URLError, TimeoutError) as error:
    print("HTTP check failed:", error)
```

Run `python3 security_check.py`. Expect two synthetic 403 records; the local HTTP status depends on the actual service. Stop the server and repeat to observe error handling. Distinguish synthetic log summaries from real service observations. Consider how the same skills could support a future WAF dashboard without implementing the project this week.

## Practical Evidence
Capture status summaries, HTTP response information and the handled connection failure. Record actual observations separately from expected results.

## Learning Outcomes
Apply regex, counters and HTTP clients to defensive automation and prepare for later project development.

## Conclusion
Use regular expressions, HTTP requests and structured log analysis for defensive automation. The exercise builds foundations for the planned WEEK-07 WAF-Honeypot project.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-29.md) | [Repository Home →](../README.md)
