# CrowdStrike Falcon Investigation Portfolio

This repository contains documented security investigations performed in a controlled home lab using CrowdStrike Falcon.

Each investigation follows a structured incident response workflow, including:

- Alert Analysis
- Process Investigation
- Detection Analysis
- MITRE ATT&CK Mapping
- Impact Assessment
- Root Cause Analysis
- Incident Classification
- Lessons Learned

> **Note**
>
> All investigations were intentionally performed inside an isolated home lab for learning and validation purposes. No production systems or third-party environments were involved.

---

## Investigation Summary

| # | Investigation | MITRE ATT&CK | Severity | Status |
|---|---------------|--------------|----------|--------|
| 01 | Credential Access via SAM Hive Export | T1003 - OS Credential Dumping | Critical | Closed |

---

## Repository Structure

```
CrowdStrike-Investigations
│
├── README.md
│
├── Investigation-01-Credential-Access-SAM-Hive
│   ├── README.md
│   └── images
│
├── Investigation-02
│
├── Investigation-03
│
└── Investigation-04
```

More investigations will be added as additional attack techniques are validated and analyzed.
