# Day 19 – Honeypots and Deception Technology

## Objective
Explain honeypot categories and implement a basic local decoy service.

## Introduction
A honeypot is a deliberately deployed decoy resource designed to attract or observe interactions that may indicate suspicious activity. Deception technology uses decoy services, systems or assets to support detection and investigation.

Low-interaction honeypots simulate limited functionality, while high-interaction honeypots provide more realistic environments and require stronger containment. Honeypots complement other defenses and are not a replacement for access controls or monitoring.

## Topics Covered

| Concept | Description |
|---|---|
| Low-interaction honeypot | Simulates a limited service or interface. |
| High-interaction honeypot | Provides a more realistic isolated environment. |
| Honeynet | A network of decoy systems. |
| Honeytoken | A decoy data item used to detect unexpected access. |
| Containment | Limits the ability of a decoy to affect other systems. |

A web decoy can record request metadata without collecting real credentials. In a WAF-honeypot architecture, suspicious requests may be directed to a contained decoy according to a tested policy.

## Practical Activity – Local Web Decoy
Create a new file `honeypot_demo.py` on your own VM. This simple decoy binds only to loopback, returns a fixed response and records minimal metadata. It does not collect credentials or execute user input.

```python
from http.server import BaseHTTPRequestHandler, HTTPServer
from datetime import datetime, timezone

class Decoy(BaseHTTPRequestHandler):
    def do_GET(self):
        print(datetime.now(timezone.utc).isoformat(),
              "decoy_access", "method=GET", flush=True)
        body = b"Demonstration decoy service"
        self.send_response(200)
        self.send_header("Content-Type", "text/plain")
        self.send_header("Content-Length", str(len(body)))
        self.end_headers()
        self.wfile.write(body)

    def log_message(self, format, *args):
        pass

HTTPServer(("127.0.0.1", 5001), Decoy).serve_forever()
```

Run the server in one terminal:

```bash
python3 honeypot_demo.py
```

In another terminal:

```bash
curl -i http://127.0.0.1:5001/
curl -i http://127.0.0.1:5001/demo
```

Observe the response and the decoy event messages. If port 5001 is occupied, choose an unused local port and update both commands. Stop the server with Ctrl+C. Do not expose this demonstration to public networks. A real deployment would require network isolation, resource limits and secure log handling.

## Practical Evidence
Capture the terminal running the decoy and the HTTP response from curl. Record the actual event count and response status. Label all requests as controlled laboratory traffic.

## Learning Outcomes
- Distinguish types of honeypots.
- Run a local low-interaction decoy service.
- Explain containment and its role in WAF integration.

## Conclusion
Honeypots can improve visibility into unexpected interactions when they are isolated, monitored and deployed with clear security objectives.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-18.md) | [Next Day →](Day-20.md)
