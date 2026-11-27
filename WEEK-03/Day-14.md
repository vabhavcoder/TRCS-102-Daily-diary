# Day 14 – Port Scanning and Service Identification

## Objective
Understand TCP port states and identify a deliberately exposed local service.

## Introduction
Port scanning checks whether network endpoints accept connections. Service identification attempts to determine which application is responding. Results describe observations, not proof of vulnerabilities.

## Topics Covered

| Port state | Meaning |
|---|---|
| Open | An application accepts connections. |
| Closed | The host responds but no application accepts connections on that port. |
| Filtered | Filtering or lack of response prevents a definitive classification. |

A TCP connect scan completes normal TCP connections. Version detection sends service-specific probes to identify responding applications; results can be uncertain.

## Practical Activity – Inspecting a Local HTTP Service
On your own Linux VM, start a temporary HTTP server in an empty directory, bound only to loopback:

```bash
mkdir -p ~/scan-lab
cd ~/scan-lab
printf 'Local security lab
' > index.html
python3 -m http.server 8000 --bind 127.0.0.1
```

In a second terminal, inspect the service:

```bash
ss -lnt
curl http://127.0.0.1:8000/
nmap -sT -sV -p 8000,8001 127.0.0.1 -oN services.txt
```

Compare the observed port states with `ss`. Stop the HTTP server using Ctrl+C, then repeat the scan to observe the change. A port may have another listener; verify rather than assuming the result.

## Practical Evidence
Record actual service identification and before/after port states. Attach screenshots and saved scan output.

## Learning Outcomes
- Interpret port states.
- Identify local services.
- Understand how stopping a service reduces exposure.

## Conclusion
Understand TCP port states and identify a deliberately exposed local service. These concepts support responsible, evidence-based cybersecurity practice.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-13.md) | [Next Day →](Day-15.md)
