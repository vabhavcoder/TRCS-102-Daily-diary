# Day 28 – Python Fundamentals for Cybersecurity

## Objective
Practice functions, collections, file handling and exception handling.

## Introduction and Theoretical Concepts
Python is useful for repeatable security tasks such as parsing logs, validating input and calculating summaries. Lists hold ordered records, dictionaries represent structured events, sets store unique values, and functions support reusable logic. Exception handling prevents predictable file or data errors from terminating an entire workflow. Context managers close files automatically. Security scripts should avoid hard-coded credentials, validate inputs and distinguish errors from successful results.

## Practical Activity
Create `event_summary.py` using synthetic events:

```python
from pathlib import Path
from collections import Counter

path = Path("lab_events.txt")
path.write_text("ALLOW /home\nDENY /admin\nALLOW /help\n", encoding="utf-8")

def summarize(filename):
    counts = Counter()
    try:
        with open(filename, encoding="utf-8") as handle:
            for line in handle:
                fields = line.split(maxsplit=1)
                if fields and fields[0] in {"ALLOW", "DENY"}:
                    counts[fields[0]] += 1
    except OSError as error:
        print(f"File error: {error}")
        return None
    return dict(counts)

print(summarize(path))
print(summarize("missing_lab_file.txt"))
```

Run `python3 event_summary.py`. The synthetic data should produce two ALLOW and one DENY entries. Change the input to include blank lines and unexpected labels, then observe how the function behaves. Explain why a missing file must not be interpreted as zero alerts.

## Practical Evidence
Capture the script and actual console output, including the handled missing-file error. Label all events as synthetic.

## Learning Outcomes
Use Python functions, dictionaries, counters and exceptions to summarize local security records.

## Conclusion
Practice functions, collections, file handling and exception handling. The exercise builds foundations for the planned WEEK-07 WAF-Honeypot project.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*

---

## Navigation

[← Previous Day](Day-27.md) | [Next Day →](Day-29.md)
