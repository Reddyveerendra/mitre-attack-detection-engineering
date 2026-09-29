# 🔎 Reconnaissance Detection Engineering

This section focuses on developing and documenting detections for **MITRE ATT&CK Reconnaissance (TA0043)**.

Reconnaissance represents adversary activities performed to gather information about a target before attempting to compromise it. The objective of this section is to identify which reconnaissance behaviors can be detected through available security telemetry and translate those behaviors into actionable detection logic.

---

## 🎯 Objective

The goal is to:

* Understand reconnaissance techniques and adversary behavior
* Identify observable telemetry associated with reconnaissance activity
* Develop detection logic for relevant techniques and sub-techniques
* Map detections to MITRE ATT&CK
* Document expected false positives and limitations
* Test and refine detection logic
* Identify visibility gaps in reconnaissance detection

---

## 🧭 MITRE ATT&CK — Reconnaissance

**Tactic:** Reconnaissance
**ATT&CK ID:** TA0043

Reconnaissance techniques covered in this section include:

| Technique | Name                               | Detection Status |
| --------- | ---------------------------------- | ---------------- |
| T1595     | Active Scanning                    | 🟡 In Progress   |
| T1595.001 | Scanning IP Blocks                 | 🟡 In Progress   |
| T1595.002 | Vulnerability Scanning             | 🟡 In Progress   |
| T1595.003 | Wordlist Scanning                  | 🟡 In Progress   |
| T1595.004 | Scanning for Vulnerable Websites   | ⚪ Planned        |
| T1592     | Gather Victim Host Information     | ⚪ Planned        |
| T1590     | Gather Victim Network Information  | ⚪ Planned        |
| T1589     | Gather Victim Identity Information | ⚪ Planned        |
| T1591     | Gather Victim Org Information      | ⚪ Planned        |

> Detection feasibility depends on the availability of relevant telemetry. Some reconnaissance techniques may occur outside the organization's observable environment.

---

## 🔬 Detection Approach

Each reconnaissance technique is analyzed using the following process:

```text
MITRE ATT&CK Technique
        ↓
Adversary Behavior
        ↓
Observable Activity
        ↓
Available Telemetry
        ↓
Detection Logic
        ↓
Testing
        ↓
False Positive Analysis
        ↓
Tuning
        ↓
Final Detection
```

The focus is on **detectable behavior**, rather than simply creating a rule for every ATT&CK technique.

---

## 📁 Structure

```text
Reconnaissance/
│
├── README.md
│
├── T1595-Active-Scanning/
│   │
│   ├── T1595.001-Scanning-IP-Blocks/
│   │   ├── README.md
│   │   └── detection-rule
│   │
│   ├── T1595.002-Vulnerability-Scanning/
│   │   ├── README.md
│   │   └── detection-rule
│   │
│   ├── T1595.003-Wordlist-Scanning/
│   │   ├── README.md
│   │   └── detection-rule
│   │
│   └── T1595.004-Scanning-for-Vulnerable-Websites/
│       ├── README.md
│       └── detection-rule
│
├── T1592-Gather-Victim-Host-Information/
│
├── T1590-Gather-Victim-Network-Information/
│
├── T1589-Gather-Victim-Identity-Information/
│
└── T1591-Gather-Victim-Org-Information/
```

---

## 🛡️ Detection Considerations

Reconnaissance detection can be challenging because legitimate security activity may closely resemble malicious reconnaissance.

Examples include:

* Vulnerability scanners
* Penetration testing
* Security assessments
* Network monitoring
* IT administration
* Asset discovery
* External security services
* Automated application testing

Therefore, detections should consider:

* Source reputation
* Scan frequency
* Number of targets
* Number of ports/services accessed
* Request patterns
* Authentication context
* Known security tools
* Approved scanning infrastructure
* Historical baseline

---

## 📊 Detection Quality

Each detection should be evaluated using:

| Metric          | Purpose                                                    |
| --------------- | ---------------------------------------------------------- |
| Coverage        | What adversary behavior can be detected?                   |
| Visibility      | Is the required telemetry available?                       |
| Fidelity        | How accurately does the rule identify suspicious behavior? |
| False Positives | What legitimate activity triggers the rule?                |
| Tuning          | How can unnecessary alerts be reduced?                     |
| Validation      | Has the detection been tested?                             |
| Limitations     | What activity remains undetected?                          |

---

## 🧪 Validation

Where possible, detections should be validated using controlled activity that represents the behavior described by the corresponding MITRE ATT&CK technique.

Validation should answer:

1. Does the required telemetry exist?
2. Is the expected activity logged?
3. Does the detection trigger?
4. Does it trigger on the correct behavior?
5. What legitimate activity also triggers it?
6. Can the detection be tuned without losing meaningful coverage?

---

## ⚠️ Detection Limitations

Not every MITRE ATT&CK Reconnaissance technique can necessarily be detected from internal security telemetry.

For example, information gathered from:

* Public websites
* Social media
* WHOIS/DNS information
* Public documents
* Search engines
* Job postings
* Public cloud information

may occur outside the organization's monitoring boundary.

Therefore:

> **ATT&CK technique coverage does not automatically mean detection coverage.**

The availability and quality of telemetry determine whether a technique can realistically be detected.

---

## 📚 References

* [MITRE ATT&CK — Reconnaissance](https://attack.mitre.org/tactics/TA0043/)
* [MITRE ATT&CK — Active Scanning](https://attack.mitre.org/techniques/T1595/)
* [MITRE ATT&CK Enterprise](https://attack.mitre.org/matrices/enterprise/)

---

## 🚧 Status

**Current focus:** Active Scanning and its applicable sub-techniques.

This section will be expanded as additional reconnaissance techniques are researched, developed, tested, and documented.
