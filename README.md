# MITRE ATT&CK Detection Engineering

A practical detection engineering repository focused on developing, documenting, testing, and mapping security detections to the **MITRE ATT&CK framework**.

The goal of this project is to understand how adversary behaviors can be translated into actionable detection logic across different security data sources and detection technologies.

---

## 🎯 Objectives

* Build detections mapped to **MITRE ATT&CK techniques and sub-techniques**
* Understand adversary behavior and attack patterns
* Develop detection logic based on observable security events
* Document detection assumptions, data sources, and limitations
* Reduce false positives through detection refinement
* Develop threat-hunting and detection-engineering skills
* Create a structured detection portfolio covering the ATT&CK Enterprise matrix

---

## 🧭 MITRE ATT&CK Coverage

The repository follows the **MITRE ATT&CK Enterprise** framework and is organized around its tactical structure.

| Tactic               | Status         |
| -------------------- | -------------- |
| Reconnaissance       | 🟡 In Progress |
| Resource Development | ⚪ Planned      |
| Initial Access       | ⚪ Planned      |
| Execution            | ⚪ Planned      |
| Persistence          | ⚪ Planned      |
| Privilege Escalation | ⚪ Planned      |
| Defense Evasion      | ⚪ Planned      |
| Credential Access    | ⚪ Planned      |
| Discovery            | ⚪ Planned      |
| Lateral Movement     | ⚪ Planned      |
| Collection           | ⚪ Planned      |
| Command and Control  | ⚪ Planned      |
| Exfiltration         | ⚪ Planned      |
| Impact               | ⚪ Planned      |

> Status will be updated as detections are developed and validated.

---

## 📁 Repository Structure

```text
mitre-attack-detection-engineering/
│
├── README.md
│
├── Reconnaissance/
│   ├── T1595-Active-Scanning/
│   │   ├── T1595.001-Scanning-IP-Blocks/
│   │   ├── T1595.002-Vulnerability-Scanning/
│   │   └── T1595.003-Wireless-Scanning/
│   │
│   ├── T1592-Gather-Victim-Host-Information/
│   └── ...
│
├── Resource-Development/
│
├── Initial-Access/
│
├── Execution/
│
├── Persistence/
│
├── Privilege-Escalation/
│
├── Defense-Evasion/
│
├── Credential-Access/
│
├── Discovery/
│
├── Lateral-Movement/
│
├── Collection/
│
├── Command-and-Control/
│
├── Exfiltration/
│
└── Impact/
```

---

## 🔎 Detection Development Approach

Each detection follows a consistent detection-engineering workflow:

```text
MITRE ATT&CK Technique
        ↓
Adversary Behavior
        ↓
Attack Scenario
        ↓
Required Telemetry
        ↓
Detection Logic
        ↓
Testing & Validation
        ↓
False Positive Analysis
        ↓
Detection Tuning
        ↓
Documented Detection
```

The focus is not simply on writing a query or rule, but on understanding **what behavior is being detected, what telemetry supports the detection, and how the detection can be validated**.

---

## 🧩 Detection Documentation

Each detection aims to document the following:

| Component           | Description                                |
| ------------------- | ------------------------------------------ |
| MITRE Technique     | ATT&CK technique or sub-technique          |
| Tactic              | Associated ATT&CK tactic                   |
| Detection Objective | What the detection is intended to identify |
| Attack Scenario     | Example adversary behavior                 |
| Data Sources        | Required telemetry or log sources          |
| Detection Logic     | Logic used to identify the behavior        |
| Indicators          | Relevant observables or patterns           |
| False Positives     | Expected legitimate activity               |
| Tuning              | Methods to improve detection quality       |
| Validation          | How the detection can be tested            |
| Limitations         | Known gaps and visibility requirements     |
| References          | Relevant ATT&CK and security research      |

---

## 🛡️ Detection Philosophy

This project follows several principles:

### 1. Behavior over Indicators

Where possible, detections focus on **adversary behavior** rather than relying exclusively on static indicators such as IP addresses, domains, or hashes.

### 2. ATT&CK Mapping

Every detection is mapped to the relevant MITRE ATT&CK technique or sub-technique.

### 3. Telemetry Awareness

A detection is only useful when the required telemetry is available and reliable.

### 4. False Positive Management

Legitimate administrative, automated, and business activities are considered during detection development.

### 5. Validation

Detections should be tested against realistic attack behavior whenever possible.

### 6. Continuous Improvement

Detection logic is treated as an iterative process:

```text
Develop → Test → Analyze → Tune → Validate → Improve
```

---

## 🧪 Detection Lifecycle

Each detection progresses through the following stages:

```text
Research
   ↓
Design
   ↓
Development
   ↓
Testing
   ↓
Validation
   ↓
Tuning
   ↓
Documentation
   ↓
Monitoring
```

---

## 🔬 Example Detection Areas

The repository may cover behaviors such as:

* Network and vulnerability scanning
* Account discovery
* Process discovery
* PowerShell activity
* Command and scripting interpreter abuse
* Credential access
* Brute-force activity
* Suspicious authentication
* Persistence mechanisms
* Lateral movement
* Remote service abuse
* Defense evasion
* Command and control
* Data collection
* Data exfiltration
* Impact techniques

---

## 📊 Detection Maturity

Detections may be classified according to their development stage:

```text
Planned
   ↓
Research
   ↓
Developed
   ↓
Tested
   ↓
Validated
   ↓
Tuned
```

A detection being present in the repository does not necessarily mean it has been production validated.

---

## 🚧 Current Focus

### Reconnaissance

The initial phase of this project focuses on **MITRE ATT&CK Reconnaissance techniques**.

Current work includes researching and developing detections around:

* **T1595 — Active Scanning**
* **T1595.001 — Scanning IP Blocks**
* **T1595.002 — Vulnerability Scanning**
* **T1595.003 — Wordlist Scanning**
* Additional Reconnaissance techniques as development progresses

The objective is to understand which reconnaissance behaviors can be detected from available security telemetry and what limitations exist.

---

## 📚 References

* [MITRE ATT&CK](https://attack.mitre.org/)
* [MITRE ATT&CK Enterprise Matrix](https://attack.mitre.org/matrices/enterprise/)
* [MITRE ATT&CK Techniques](https://attack.mitre.org/techniques/enterprise/)

---

## ⚠️ Disclaimer

This repository is intended for **educational, research, and detection-engineering development purposes**.

Detection logic may require modification depending on the organization's:

* Logging architecture
* Data sources
* SIEM/EDR platform
* Network architecture
* Baseline activity
* Threat model
* Detection requirements

A detection should be tested and validated in an appropriate environment before being used in production.

---

## 👤 Author

**Veerendra Reddy**

Cybersecurity | SOC | Detection Engineering | Threat Detection

---

⭐ This repository documents my hands-on journey toward building practical, ATT&CK-aligned detection engineering capabilities.
