# T1595 — Active Scanning

**MITRE ATT&CK Tactic:** Reconnaissance
**MITRE ATT&CK Technique:** T1595 — Active Scanning

## Overview

Active Scanning covers adversary activity that actively probes the organization's IP space, exposed services, and web content to gather information about potential targets.

This project focuses on detecting externally originated scanning activity that is observable through organizational security telemetry.

The detection approach is based on identifying **systematic, repeated, or high-volume probing behavior** rather than treating individual connection attempts as malicious.

---

## Detection Objective

Identify external sources actively probing organizational assets through:

* Network sweeps
* Horizontal port scanning
* Sequential IP probing
* Vulnerability probing
* Scanner-like behavior
* Multi-host vulnerability scanning
* Directory enumeration
* URI/resource enumeration
* Automated wordlist scanning

---

## Sub-Techniques

| ID            | Technique              | Detection Rules |
| ------------- | ---------------------- | --------------: |
| **T1595.001** | Scanning IP Blocks     |               3 |
| **T1595.002** | Vulnerability Scanning |               3 |
| **T1595.003** | Wordlist Scanning      |               3 |

**Total:** 3 sub-techniques / 9 analytics rules

---

# 📁 Detection Structure

```text
T1595-Active-Scanning/
│
├── README.md
│
├── T1595.001-Scanning-IP-Blocks/
│   ├── README.md
│   ├── REC-T1595.001-001-Network-Sweep
│   ├── REC-T1595.001-002-Horizontal-Port-Scan
│   └── REC-T1595.001-003-Sequential-IP-Probing
│
├── T1595.002-Vulnerability-Scanning/
│   ├── README.md
│   ├── REC-T1595.002-001-Vulnerability-Probe
│   ├── REC-T1595.002-002-Scanner-Fingerprint
│   └── REC-T1595.002-003-Multi-Host-Vulnerability-Scan
│
└── T1595.003-Wordlist-Scanning/
    ├── README.md
    ├── REC-T1595.003-001-Directory-Enumeration
    ├── REC-T1595.003-002-URI-Resource-Enumeration
    └── REC-T1595.003-003-Automated-Wordlist-Scanning
```

---

# T1595.001 — Scanning IP Blocks

Focuses on identifying external sources systematically probing multiple IP addresses within the organization's monitored address space.

### Detection Rules

| Rule ID           | Detection             | Data Source              | Severity |
| ----------------- | --------------------- | ------------------------ | -------- |
| REC-T1595.001-001 | Network Sweep         | Firewall / NetFlow / IDS | Medium   |
| REC-T1595.001-002 | Horizontal Port Scan  | Firewall / NetFlow / IDS | Medium   |
| REC-T1595.001-003 | Sequential IP Probing | Firewall / NetFlow / IDS | Medium   |

### Detection Signals

Key signals include:

* High number of distinct destination IPs
* Multiple connection attempts
* Same destination port across multiple hosts
* Systematic probing of addresses
* External source IP
* Short observation window

---

# T1595.002 — Vulnerability Scanning

Focuses on detecting external sources actively probing exposed assets for known vulnerabilities or recognizable vulnerable services.

### Detection Rules

| Rule ID           | Detection                     | Data Source              | Severity    |
| ----------------- | ----------------------------- | ------------------------ | ----------- |
| REC-T1595.002-001 | Vulnerability Probe           | IDS/IPS / WAF / Web Logs | High        |
| REC-T1595.002-002 | Scanner Fingerprint           | IDS/IPS / WAF / Web Logs | Medium–High |
| REC-T1595.002-003 | Multi-Host Vulnerability Scan | IDS/IPS / Firewall / WAF | High        |

### Detection Signals

Key signals include:

* Known vulnerability-probe signatures
* Scanner fingerprints
* Scanner-like User-Agent
* Recognizable network signatures
* Vulnerability-probe behavior
* Multiple targeted hosts
* High request volume

A stronger detection combines multiple signals rather than relying solely on a scanner User-Agent or signature.

---

# T1595.003 — Wordlist Scanning

Focuses on identifying systematic discovery of web resources through automated requests to multiple paths or URIs.

### Detection Rules

| Rule ID           | Detection                   | Data Source            | Severity    |
| ----------------- | --------------------------- | ---------------------- | ----------- |
| REC-T1595.003-001 | Directory Enumeration       | WAF / Web Server       | Medium      |
| REC-T1595.003-002 | URI/Resource Enumeration    | WAF / Web Server / CDN | Medium      |
| REC-T1595.003-003 | Automated Wordlist Scanning | WAF / Web Server       | Medium–High |

### Detection Signals

Key signals include:

* High URI diversity
* Large number of requested paths
* Elevated 403/404 response rate
* Short request intervals
* Automated request behavior
* Scanner characteristics

A stronger detection correlates:

```text
High URI Diversity
        +
High 403/404 Ratio
        +
Short Request Intervals
        +
Automated Behavior
        ↓
Automated Wordlist Scanning
```

---

# 🔬 Detection Methodology

Each rule follows a common detection-development process:

```text
MITRE ATT&CK Technique
        ↓
Adversary Behavior
        ↓
Observable Telemetry
        ↓
Detection Hypothesis
        ↓
Analytics Rule
        ↓
Testing
        ↓
False Positive Analysis
        ↓
Tuning
        ↓
Validation
```

---

# 🛡️ False Positive & Tuning Considerations

Active scanning can also be generated by legitimate security activity.

Examples include:

* Authorized vulnerability scanners
* Penetration testing
* Security assessments
* Security-testing infrastructure
* Monitoring systems
* Legitimate automated clients

Production detections should therefore maintain an **approved scanner / penetration-testing allowlist**.

Additional tuning should consider:

* Source reputation
* Request frequency
* Number of targets
* Number of unique destinations
* Number of unique ports
* URI diversity
* 403/404 ratios
* Known scanner signatures
* Normal organizational traffic patterns

---

# 📊 Detection Confidence

Individual indicators may have limited value.

Higher confidence can be achieved through correlation:

```text
External Source
      +
Systematic Activity
      +
Multiple Targets
      +
High Request / Connection Volume
      +
Scanner Characteristics
      ↓
Higher-Confidence Reconnaissance Detection
```

---

# ⚠️ Detection Limitations

Detection capability depends on available telemetry.

Potential data sources include:

* Firewall
* NetFlow
* IDS/IPS
* WAF
* Web server logs
* CDN telemetry
* Network security events

An ATT&CK technique being documented does not automatically mean that the behavior is detectable in every environment.

---

# 📈 Detection Coverage

| Technique                          | Rules | Status         |
| ---------------------------------- | ----: | -------------- |
| T1595.001 — Scanning IP Blocks     |     3 | 🟡 In Progress |
| T1595.002 — Vulnerability Scanning |     3 | 🟡 In Progress |
| T1595.003 — Wordlist Scanning      |     3 | 🟡 In Progress |
| **Total**                          | **9** | 🟡             |

---

## References

* [MITRE ATT&CK — T1595 Active Scanning](https://attack.mitre.org/techniques/T1595/)
* [MITRE ATT&CK — Reconnaissance](https://attack.mitre.org/tactics/TA0043/)

---

> **Detection Engineering Principle:**
> The objective is not to create a rule for every possible activity. A detection should be developed when sufficient telemetry exists to observe the behavior and distinguish it from legitimate activity with reasonable confidence.

This aligns closely with your uploaded catalog's core principle: **only create an analytics rule when the organization has enough telemetry to observe the behavior and distinguish it from legitimate activity.** 

For your next GitHub level, I’d then make **`T1595.001-Scanning-IP-Blocks/README.md`** and put the three actual detections inside it, rather than putting all the KQL/pseudocode directly into the T1595 README.
