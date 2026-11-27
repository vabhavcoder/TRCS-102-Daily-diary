# Day 21 – Web Application Architecture and HTTP

## Objective
Understand client-server architecture and HTTP communication.

## Introduction and Theoretical Concepts
A web application normally consists of a browser, web server, application logic and a database. The browser sends an HTTP request and the server returns a response. HTTPS protects communication using TLS but does not automatically prevent application vulnerabilities.

| Component | Function |
|---|---|
| Client | Sends requests and renders responses. |
| Web server | Receives HTTP traffic and serves resources. |
| Application | Processes input and business logic. |
| Database | Stores and retrieves data. |
| Reverse proxy | Receives requests before forwarding to an upstream application. |

HTTP requests contain a method, target, headers and an optional body. GET retrieves resources; POST submits data; PUT replaces a resource; DELETE requests removal. Common status codes include 200 (success), 400 (bad request), 403 (forbidden), 404 (not found) and 500 (server error). Cookies can maintain session state; authentication identifies a user while authorization determines access.

## Practical Activity
Create a disposable local HTTP service in a dedicated directory:

```bash
mkdir -p ~/web-security-lab/http
cd ~/web-security-lab/http
printf '%s\n' 'Local web security lab' > index.html
python3 -m http.server 8000 --bind 127.0.0.1
```

In another terminal:

```bash
curl -i http://127.0.0.1:8000/
curl -I http://127.0.0.1:8000/
curl -i http://127.0.0.1:8000/missing.html
```

Identify the status line, response headers and body. Compare GET with HEAD and successful with missing resources. Stop the server using Ctrl+C.

## Practical Evidence
Capture the HTTP server terminal and cURL responses. Record actual status codes and explain their meaning.

## Learning Outcomes
Explain HTTP structure, identify response codes and describe where a WAF sits in the architecture.

## Conclusion
Understand client-server architecture and HTTP communication. The activity connects secure application design with the planned WAF-Honeypot project.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](../WEEK-04/Day-20.md) | [Next Day →](Day-22.md)
