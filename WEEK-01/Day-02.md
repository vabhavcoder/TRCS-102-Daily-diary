# Day 02 – Cybersecurity Principles and Threats

## Objective
Understand the CIA Triad, common cyber threats and fundamental security controls.

## CIA Triad
The CIA Triad represents three core objectives of information security.

| Principle | Meaning | Example control |
|---|---|---|
| Confidentiality | Information is accessible only to authorized parties. | Encryption and access control |
| Integrity | Information remains accurate and protected against unauthorized modification. | Hashing and digital signatures |
| Availability | Authorized users can access resources when required. | Backups and redundancy |

## Common Cyber Threats
- **Phishing:** Deceptive messages intended to obtain sensitive information.
- **Malware:** Malicious software designed to damage, disrupt or misuse systems.
- **Ransomware:** Malware that restricts access to data or systems and demands payment.
- **Denial of service:** Attempts to disrupt the availability of a service.
- **Social engineering:** Manipulation of individuals to bypass security controls.
- **Password attacks:** Attempts to obtain or guess account credentials.

## Types of Hackers
White-hat hackers perform authorized security testing. Black-hat hackers engage in unauthorized malicious activity. Grey-hat hackers may act without authorization even when they do not intend harm. Security testing must remain within explicit permission and scope.

## Practical Activity – Integrity Verification
Create a sample file in a Linux environment and calculate its SHA-256 hash. Modify the file and compare the hashes.

```bash
printf 'Cybersecurity lab\n' > sample.txt
sha256sum sample.txt
printf 'Modified content\n' >> sample.txt
sha256sum sample.txt
```

**Expected result:** The two hashes should differ because the file contents changed. A trusted reference hash is needed to detect unauthorized changes reliably.

## Practical Evidence
Record both actual hash values and attach a terminal screenshot after executing the commands.

## Learning Outcomes
- Explain confidentiality, integrity and availability.
- Identify common threats and appropriate preventive controls.
- Understand the role of hashing in integrity verification.

## Conclusion
The CIA Triad provides a foundation for designing security controls and evaluating the impact of cyber threats.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*
