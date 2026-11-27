# Day 07 – OSI and TCP/IP Models

## Objective
Understand layered network architecture, encapsulation and the relationship between OSI and TCP/IP models.

## Introduction
Layered models divide communication into manageable functions. Each layer provides services to the layer above it and uses services from the layer below it.

## Topics Covered

| OSI layer | Function | Example |
|---|---|---|
| 7 – Application | Network services for applications | HTTP, DNS |
| 6 – Presentation | Data representation and transformation | Encoding, encryption concepts |
| 5 – Session | Session establishment and management | Session control |
| 4 – Transport | End-to-end data delivery | TCP, UDP |
| 3 – Network | Logical addressing and routing | IP |
| 2 – Data Link | Local frame delivery | Ethernet, MAC addresses |
| 1 – Physical | Transmission of signals | Cables, radio signals |

## TCP/IP Model

| TCP/IP layer | Corresponding OSI layers |
|---|---|
| Application | 5–7 |
| Transport | 4 |
| Internet | 3 |
| Link | 1–2 |

The mapping is conceptual; real protocols do not always fit neatly into a single OSI layer.

## Encapsulation and Decapsulation
Application data is carried in a transport segment (TCP) or datagram (UDP), then an IP packet, then a link-layer frame. The receiver processes the headers in reverse order.

```text
Application data → TCP segment → IP packet → Ethernet frame → Signals
```

## Practical Activity – Observing Layered Communication
Start a local HTTP server in an empty test directory in one terminal:

```bash
mkdir -p ~/network-lab
cd ~/network-lab
printf 'Network lab test\n' > index.html
python3 -m http.server 8000 --bind 127.0.0.1
```

In another terminal:

```bash
curl -v http://127.0.0.1:8000/
ss -ltn
```

Identify the HTTP request and response at the application layer, TCP port 8000 at the transport layer and loopback IP at the internet layer. Loopback traffic does not traverse a physical Ethernet cable. Stop the server with Ctrl+C.

## Practical Evidence
Save the actual HTTP response and listening socket output. Record the layers identified.

## Learning Outcomes
- Explain all seven OSI layers and four TCP/IP layers.
- Describe encapsulation and decapsulation.
- Relate a local HTTP exchange to network layers.

## Conclusion
Layered models help isolate networking issues and understand where security controls operate.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-06.md) | [Next Day →](Day-08.md)
