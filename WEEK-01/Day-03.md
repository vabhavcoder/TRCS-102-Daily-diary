# Day 03 – Kali Linux and Virtual Lab Setup

## Objective
Understand virtualization and prepare a controlled environment for cybersecurity learning.

## Introduction
Kali Linux is a Linux distribution designed for security assessment and related technical tasks. Virtualization allows a guest operating system to run inside a host operating system, making it useful for isolated practical exercises.

## Tools and Technologies
- Oracle VirtualBox: virtualization platform.
- Kali Linux: guest operating system.
- Windows: example host operating system.

## Virtual Machine Configuration
For an 8 GB RAM host, a reasonable starting configuration is 2 virtual CPUs, 2 GB RAM and a 30 GB dynamically allocated virtual disk. Adjust according to available resources and guest requirements.

## Practical Procedure
1. Obtain Kali Linux from https://www.kali.org/get-kali/ and VirtualBox from https://www.virtualbox.org/.
2. Create a virtual machine or import the official prebuilt image.
3. Configure NAT for updates when needed. Use an internal network for isolated multi-VM security testing.
4. Start the virtual machine and log in.
5. Verify the operating system and network configuration using the terminal.

```bash
cat /etc/os-release
uname -r
whoami
ip a
free -h
df -h
```

## Security Precautions
Avoid exposing intentionally vulnerable services to public networks. Test only systems owned by you or explicitly authorized for testing. Take a VM snapshot before significant configuration changes.

## Practical Evidence
Attach actual screenshots of the VM configuration, Kali desktop and terminal verification. An existing Kali VM may be used instead of reinstalling it.

## Learning Outcomes
- Understand host and guest operating systems.
- Differentiate NAT and internal networking.
- Verify basic Linux system configuration.

## Conclusion
A virtual laboratory provides a controlled environment for practicing cybersecurity concepts without unnecessarily exposing external systems.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*
