# Day 24 – Cross-Site Scripting and Directory Traversal

## Objective
Understand unsafe output rendering and path handling, and apply defensive controls.

## Introduction and Theoretical Concepts
Cross-site scripting (XSS) occurs when untrusted content is interpreted as executable browser content. Reflected XSS originates in a request, stored XSS persists in application data, and DOM-based XSS arises through unsafe client-side processing. Context-specific output encoding, safe DOM APIs and Content Security Policy help reduce risk.

Directory traversal occurs when user-controlled paths allow access outside an intended directory. Defenses include fixed resource identifiers, canonical path checks and least privilege. URL encoding and normalization complicate detection; simplistic substring checks are insufficient.

| Vulnerability | Primary defense |
|---|---|
| XSS | Context-aware output encoding and safe rendering. |
| Directory traversal | Restrict resource access to authorized paths. |

A WAF can record suspicious input, but the application must enforce its own security boundaries.

## Practical Activity
Create `validation_demo.py`:

```python
from html import escape
from pathlib import Path

for value in ['Hello', '<b>Example</b>', 'A & B']:
    print(value, '=>', escape(value))

base = (Path.cwd() / 'public').resolve()
for name in ['index.html', 'docs/help.html', '../outside.txt']:
    candidate = (base / name).resolve()
    print(name, 'allowed' if candidate.is_relative_to(base) else 'denied')
```

Run with Python 3.9 or newer. The examples operate on strings and paths only; no outside files are read. Observe HTML escaping and path containment. Explain why HTML escaping is not suitable for every JavaScript or URL context, and why production file serving also needs authorization and safe handling of filesystem changes.

## Practical Evidence
Capture the output showing encoded text and allowed/denied paths. Record actual results and limitations.

## Learning Outcomes
Distinguish XSS types, explain traversal, and demonstrate basic output encoding and path validation.

## Conclusion
Understand unsafe output rendering and path handling, and apply defensive controls. The activity connects secure application design with the planned WAF-Honeypot project.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-23.md) | [Next Day →](Day-25.md)
