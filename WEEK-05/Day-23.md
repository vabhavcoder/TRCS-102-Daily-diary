# Day 23 – SQL Injection and Prevention

## Objective
Understand unsafe query construction and demonstrate parameterized queries.

## Introduction and Theoretical Concepts
SQL injection arises when untrusted input is interpreted as SQL syntax instead of data. It can compromise confidentiality, integrity and availability. String concatenation and unrestricted database privileges increase risk.

| Control | Purpose |
|---|---|
| Parameterized queries | Separate SQL structure from supplied values. |
| Input validation | Enforce expected data types and lengths. |
| Least privilege | Restrict database account capabilities. |
| Error handling | Avoid exposing database internals. |
| WAF monitoring | Flag suspicious patterns as an additional control. |

A WAF signature can produce false positives and false negatives; parameterization addresses the underlying query construction problem.

## Practical Activity
Create `sql_demo.py` using an in-memory SQLite database and synthetic records:

```python
import sqlite3

db = sqlite3.connect(':memory:')
db.execute('CREATE TABLE users (name TEXT)')
db.executemany('INSERT INTO users VALUES (?)', [('Alice',), ("O'Reilly",)])
for name in ['Alice', "O'Reilly", 'Unknown']:
    rows = db.execute('SELECT name FROM users WHERE name = ?', (name,)).fetchall()
    print(repr(name), rows)
db.close()
```

Run `python3 sql_demo.py`. Compare known and unknown names and observe that an apostrophe is treated as ordinary data. Explain why building SQL with concatenation would be unsafe. Do not test an external database.

## Practical Evidence
Capture the script and actual terminal output. Record how the parameter placeholder handles special characters.

## Learning Outcomes
Explain SQL injection causes, parameterized queries and the limitations of signature-based filtering.

## Conclusion
Understand unsafe query construction and demonstrate parameterized queries. The activity connects secure application design with the planned WAF-Honeypot project.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-22.md) | [Next Day →](Day-24.md)
