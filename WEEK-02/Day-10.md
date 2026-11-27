# Day 10 – Packet Capturing and Analysis Using Wireshark

## Objective
Understand packet capture, protocol analysis and the use of Wireshark for network troubleshooting and security monitoring.

## Introduction
Wireshark is a network protocol analyzer that displays captured traffic and decodes supported protocols. Packet analysis helps investigate communication failures and inspect protocol behavior. Capture only traffic from systems and networks you own or are authorized to monitor.

## Topics Covered
- **Capture interface:** The interface from which packets are collected.
- **Capture filter:** Determines which packets are collected.
- **Display filter:** Selects which captured packets are displayed.
- **Packet details:** Shows decoded protocol headers and fields.
- **Packet bytes:** Displays the raw captured data.
- **PCAP/PCAPNG:** File formats used to store packet captures.

## Common Display Filters

| Filter | Purpose |
|---|---|
| `icmp` | IPv4 ICMP messages |
| `tcp` | TCP traffic |
| `udp` | UDP traffic |
| `dns` | Decoded DNS messages |
| `http` | Decoded HTTP messages |
| `tcp.port == 8000` | TCP traffic involving port 8000 |
| `ip.addr == 127.0.0.1` | IPv4 loopback traffic |
| `tcp.flags.syn == 1` | TCP packets with the SYN flag set |

## Practical Activity – Capture Local ICMP and HTTP Traffic
Install Wireshark if necessary using the appropriate package manager and configure capture permissions through the distribution's supported procedure. Run the graphical application as a normal user.

1. Start Wireshark and select the loopback interface (`lo` on Linux).
2. Begin capturing packets.
3. Execute `ping -c 4 127.0.0.1` in a terminal.
4. Start the local HTTP server from Day 07 and execute `curl http://127.0.0.1:8000/` in another terminal.
5. Stop the capture and apply the `icmp` and `tcp.port == 8000` display filters separately.
6. Inspect ICMP echo requests and replies, TCP connection establishment and HTTP request/response data where decoded. If needed, use Decode As to identify HTTP on the test port.
7. Save the test capture locally and stop the HTTP server.

## Expected Observations
ICMP echo requests may have corresponding echo replies. A new successful TCP connection normally shows SYN, SYN-ACK and ACK, followed by application data. Plain HTTP content may be readable in the capture, whereas TLS protects application content in transit. These are expected behaviors, not measured results.

## Practical Evidence
Attach screenshots of the actual filtered ICMP and TCP traffic. Record packet numbers and observed flags. Avoid uploading captures containing credentials, private traffic or other sensitive information.

## Learning Outcomes
- Distinguish capture filters from display filters.
- Identify ICMP and TCP packets.
- Explain the visibility of unencrypted HTTP traffic.

## Conclusion
Packet analysis connects networking theory with observable protocol behavior and provides a foundation for defensive network monitoring.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-09.md) | [Next Week →](../WEEK-03/Day-11.md)
