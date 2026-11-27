# Day 29 – Python Networking and Socket Programming

## Objective
Understand TCP client-server communication using Python sockets.

## Introduction and Theoretical Concepts
A socket represents a communication endpoint. TCP provides reliable ordered byte streams; UDP provides connectionless datagrams. A TCP server binds to an address and port, listens and accepts connections. A client connects to that endpoint. Data must be encoded as bytes before transmission and decoded for display. TCP does not preserve message boundaries; robust protocols use framing and timeouts. Binding to 127.0.0.1 keeps the demonstration accessible only locally.

## Practical Activity
Create `server.py`:

```python
import socket

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as server:
    server.bind(("127.0.0.1", 9091))
    server.listen(1)
    server.settimeout(30)
    print("Listening on localhost:9091")
    conn, addr = server.accept()
    with conn:
        conn.settimeout(5)
        print("Peer:", addr)
        print("Received:", conn.recv(1024).decode("utf-8", errors="replace"))
        conn.sendall(b"ACK")
```

Create `client.py`:

```python
import socket

with socket.create_connection(("127.0.0.1", 9091), timeout=5) as client:
    client.sendall(b"hello lab")
    print(client.recv(1024).decode())
```

Run `python3 server.py` in one terminal and `python3 client.py` in another within 30 seconds. If port 9091 is occupied, choose another unused port in both files. The server handles one client and exits. This is a minimal demonstration, not a production protocol. Try running the client after the server exits and document the connection error.

## Practical Evidence
Capture both terminals showing the sent message and acknowledgment. Record the actual error when no listener is present.

## Learning Outcomes
Explain socket creation, binding, listening, connecting, sending, receiving and timeouts.

## Conclusion
Understand TCP client-server communication using Python sockets. The exercise builds foundations for the planned WEEK-07 WAF-Honeypot project.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-28.md) | [Next Day →](Day-30.md)
