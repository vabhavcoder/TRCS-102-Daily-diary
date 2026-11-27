# Day 22 – OWASP Top 10 and Burp Suite

## Objective
Recognize common web security risks and inspect local HTTP requests.

## Introduction and Theoretical Concepts
OWASP publishes awareness resources describing major web application security risks. The following are selected risk themes rather than a claim about a particular edition's complete ranking.

| Risk theme | Defensive measure |
|---|---|
| Broken access control | Enforce authorization on the server. |
| Injection | Separate commands from untrusted input. |
| Cryptographic failures | Protect sensitive data and use appropriate cryptography. |
| Security misconfiguration | Remove unsafe defaults and unnecessary features. |
| Authentication failures | Use secure sessions and strong authentication. |
| Logging and monitoring gaps | Record relevant events and review alerts. |

Burp Suite is an HTTP testing proxy. Its Proxy tool captures requests and responses, HTTP history records traffic, and Repeater supports manual examination and resending. Only inspect traffic from your own authorized lab. A WAF provides supplementary filtering, not a substitute for secure code.

## Practical Activity
Restart the localhost HTTP service from Day 21. Open Burp Suite and use its built-in browser under Proxy. Visit `http://127.0.0.1:8000/`. If interception is enabled, forward the request. Open HTTP history and inspect the method, host, path and response status. Send the request to Repeater and change only the path to `/missing.html`; compare the response.

If Burp is unavailable, inspect equivalent requests with:

```bash
curl -v http://127.0.0.1:8000/
curl -v http://127.0.0.1:8000/missing.html
```

Do not intercept third-party sessions or capture real credentials. Stop the local service after the exercise.

## Practical Evidence
Capture Burp HTTP history and Repeater results, or the cURL alternative. Redact unrelated headers and record the tool actually used.

## Learning Outcomes
Describe common web risks, inspect HTTP traffic and distinguish proxy testing from WAF protection.

## Conclusion
Recognize common web security risks and inspect local HTTP requests. The activity connects secure application design with the planned WAF-Honeypot project.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-21.md) | [Next Day →](Day-23.md)
