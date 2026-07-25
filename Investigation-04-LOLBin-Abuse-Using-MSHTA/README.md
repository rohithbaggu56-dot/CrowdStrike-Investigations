# 🚨 Investigation 04 – Living-off-the-Land Binary (LOLBin) Abuse Using MSHTA

## 📌 Investigation Summary

This investigation demonstrates how adversaries can abuse the legitimate Microsoft Windows binary **MSHTA (mshta.exe)** to execute malicious scripts while blending in with normal operating system activity.

Three Atomic Red Team simulations were executed to validate CrowdStrike Falcon's behavioral detection and prevention capabilities against different MSHTA execution techniques.

Instead of creating three separate investigations, these related attack scenarios have been documented together to demonstrate how the same LOLBin can be abused in multiple ways while generating different detection behaviors inside CrowdStrike Falcon.

---

# 🧪 Lab Environment

- Platform: Windows 10 Virtual Machine
- EDR: CrowdStrike Falcon
- Attack Framework: Atomic Red Team
- Shell: PowerShell
- MITRE ATT&CK: T1218.005 – Mshta
- Investigation Type: Home SOC Lab

---

# 🎯 Investigation Objectives

- Simulate Living-off-the-Land Binary (LOLBin) abuse
- Observe CrowdStrike Falcon behavioral detections
- Analyze process execution chains
- Investigate AI Powered IOAs
- Document prevention actions
- Map observed behavior to MITRE ATT&CK

---

# ⚔️ Attack Scenarios

This investigation contains three different MSHTA abuse scenarios.

## Scenario 1 – VBScript Execution via MSHTA

**Technique**

- MSHTA executes embedded VBScript
- VBScript launches PowerShell
- Falcon detects obfuscated script execution

Evidence Location

```
Scenario-1-VBScript-Execution/
```

---

## Scenario 2 – HTA Execution via MSHTA

**Technique**

- MSHTA executes a malicious HTML Application (HTA)
- PowerShell retrieves and launches the HTA
- Falcon identifies exploit-kit style behavior and blocks execution

Evidence Location

```
Scenario-2-HTA-Execution/
```

---

## Scenario 3 – PowerShell Execution via MSHTA

**Technique**

- MSHTA proxies PowerShell execution
- Falcon detects suspicious command execution
- Behavioral IOA generated before execution continues

Evidence Location

```
Scenario-3-PowerShell-Execution/
```

---

# 🔍 Investigation Workflow

Each scenario followed the same SOC investigation process.

```
Atomic Red Team Execution
            │
            ▼
CrowdStrike Falcon Detection
            │
            ▼
Alert Review
            │
            ▼
Process Tree Analysis
            │
            ▼
Behavior Analysis
            │
            ▼
MITRE ATT&CK Mapping
            │
            ▼
Impact Assessment
            │
            ▼
Incident Classification
            │
            ▼
Case Closed
```

---

# 🛡 CrowdStrike Detection Summary

Across the three scenarios, CrowdStrike Falcon successfully identified suspicious MSHTA execution using behavioral analytics rather than relying solely on signatures.

Observed detections included:

- AI Powered IOA
- Execution via User Execution
- Execution via Command and Scripting Interpreter
- Defense Evasion
- Exploit Kit Detection
- Obfuscated Command Detection
- Process Blocked
- Process Killed

---

# 🎯 MITRE ATT&CK

## Atomic Red Team Simulation

- T1218.005 – Mshta

## CrowdStrike Behavioral Mapping

The executed Atomic technique simulated **T1218.005 (Mshta)**. Depending on the observed behavior, CrowdStrike Falcon generated behavioral detections including:

- User Execution
- Command and Scripting Interpreter
- Defense Evasion
- Exploitation for Defense Evasion

This demonstrates how behavioral EDR detections may differ from the original Atomic ATT&CK technique while still identifying malicious activity.

---

# 📈 Investigation Outcome

All three attack scenarios were successfully detected by CrowdStrike Falcon.

Falcon generated multiple behavioral detections, correlated suspicious process execution, and prevented malicious activity by blocking or terminating the associated processes.

No persistence, credential theft, lateral movement, or unauthorized compromise occurred because all tests were intentionally executed inside an isolated home SOC laboratory.

---

# 🏷 Incident Classification

**Classification:** Benign True Positive

**Reason**

The activity was intentionally generated using Atomic Red Team to validate CrowdStrike Falcon detection and prevention capabilities in a controlled lab environment.

---

# 📚 Skills Demonstrated

- CrowdStrike Falcon Investigation
- Process Tree Analysis
- Behavioral Detection Analysis
- MITRE ATT&CK Mapping
- Atomic Red Team Testing
- Incident Triage
- Threat Hunting
- Detection Validation
- SOC Documentation
- IOC Analysis

---

# 📁 Repository Structure

```
Investigation-04-LOLBin-Abuse-Using-MSHTA

├── README.md
├── Scenario-1-VBScript-Execution
├── Scenario-2-HTA-Execution
└── Scenario-3-PowerShell-Execution
```

---

# 📝 Lessons Learned

- Legitimate Windows binaries can be abused to execute malicious code.
- Behavioral detections provide greater visibility than signature-based detection alone.
- The same ATT&CK technique can generate different behavioral detections depending on execution flow.
- Reviewing process relationships and command-line arguments is critical during endpoint investigations.
- CrowdStrike Falcon effectively identified and prevented multiple MSHTA abuse techniques within a controlled lab environment.
