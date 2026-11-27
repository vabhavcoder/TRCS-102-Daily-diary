# Day 27 – Linux Firewall Configuration

## Objective
Understand iptables chains and UFW rule management through an isolated lab.

## Introduction and Theoretical Concepts
Linux Netfilter provides packet filtering capabilities. iptables manages rules for chains such as INPUT (local incoming traffic), OUTPUT (local outgoing traffic) and FORWARD (routed traffic). ACCEPT permits packets, DROP discards them, and REJECT returns an error where supported. Rules are evaluated in order; connection tracking distinguishes established traffic from new connections. UFW provides a higher-level interface for firewall administration. Modern systems may use nftables underneath these tools; avoid mixing management interfaces on a live host.

## Practical Activity
Inspect the current configuration first:

```bash
sudo iptables -L -n -v
sudo iptables -S
```

Use a temporary network namespace to avoid altering the host firewall. This requires Linux, root access, iproute2 and iptables. Choose an unused namespace name.

```bash
sudo ip netns add fwlab06
sudo ip netns exec fwlab06 ip link set lo up
sudo ip netns exec fwlab06 iptables -A INPUT -p icmp --icmp-type echo-request -j DROP
sudo ip netns exec fwlab06 iptables -L -n -v
sudo ip netns exec fwlab06 ping -c 2 -W 1 127.0.0.1
```

The ping is expected to time out. Remove the exact rule and repeat the test:

```bash
sudo ip netns exec fwlab06 iptables -D INPUT -p icmp --icmp-type echo-request -j DROP
sudo ip netns exec fwlab06 ping -c 2 127.0.0.1
sudo ip netns del fwlab06
```

For UFW, if installed, inspect status and preview a rule without applying it:

```bash
sudo ufw status verbose
sudo ufw --dry-run allow 8080/tcp
```

If UFW is unavailable, document that fact. Do not enable it or change host policies for this exercise. Explain why a future WAF service and dashboard should have different access restrictions.

## Practical Evidence
Capture rule counters and ping results before and after removal, plus the UFW dry run if available. Record any permission or tool errors.

## Learning Outcomes
Explain chain evaluation, inspect rules, test packet filtering and safely remove temporary rules.

## Conclusion
Understand iptables chains and UFW rule management through an isolated lab. The exercise builds foundations for the planned WEEK-07 WAF-Honeypot project.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-26.md) | [Next Day →](Day-28.md)
