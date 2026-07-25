# 🚨 Investigation 04 – Living-off-the-Land Binary (LOLBin) Abuse Using MSHTA

## 📌 Investigation Summary

This investigation demonstrates how Microsoft HTML Application Host (**MSHTA.exe**) can be abused as a Living-off-the-Land Binary (LOLBin) to execute malicious scripts while blending with legitimate Windows activity.

Using **Atomic Red Team (T1218.005)**, three different MSHTA execution techniques were simulated inside an isolated home SOC lab protected by **CrowdStrike Falcon**.

Rather than documenting each detection as an independent investigation, this repository combines all three related attack scenarios to demonstrate how the same LOLBin can generate different behavioral detections depending on the execution method.

---

# 🧪 Lab Environment

| Component | Value |
|-----------|-------|
| Operating System | Windows 10 |
| Endpoint Protection | CrowdStrike Falcon |
| Attack Framework | Atomic Red Team |
| LOLBin | MSHTA.exe |
| Shell | PowerShell |
| MITRE ATT&CK | T1218.005 – Mshta |
| Investigation Type | Home SOC Lab |

---

# 🎯 Investigation Objectives

- Simulate LOLBin abuse using MSHTA
- Observe CrowdStrike Falcon behavioral detections
- Analyze process execution chains
- Investigate AI Powered IOAs
- Review process trees and timelines
- Map observed behavior to MITRE ATT&CK
- Validate Falcon prevention capabilities
- Produce SOC-style investigation documentation

---

# ⚔️ Attack Scenarios

This investigation contains three different MSHTA abuse techniques.

---

# Scenario 1 – VBScript Execution via MSHTA

### Technique

- MSHTA executes embedded VBScript
- VBScript launches PowerShell
- Falcon detects suspicious script execution
- AI Powered IOA generated
- Process blocked before malicious execution

## Detection Overview

![Detection Overview](Scenario-1-VBScript-Execution/Images/01-detection-overview.png)

---

## Detection Details

![Detection Details](Scenario-1-VBScript-Execution/Images/02-detection-details.png)

---

## Process Tree

![Process Tree](Scenario-1-VBScript-Execution/Images/03-process-tree.png)

---

## Event Timeline

![Event Timeline](Scenario-1-VBScript-Execution/Images/04-event-timeline.png)

---

## Alert Closure

![Alert Closed](Scenario-1-VBScript-Execution/Images/05-alert-closed.png)

## Prevention Demonstration

🎥 Video

Scenario-1-VBScript-Blocked.mp4
### 🎥 Scenario Demos
* Click to watch: (Scenario-1-VBScript-Execution/Videos/Scenario-1-VBScript-Blocked.mp4)


---

# Scenario 2 – HTA Execution via MSHTA

### Technique

- PowerShell downloads and launches a malicious HTA
- MSHTA executes the HTA
- Falcon detects exploit-like behavior
- AI Powered IOA generated
- Process terminated immediately

## Detection Overview

![Detection Overview](Scenario-2-HTA-Execution/Images/01-detection-overview.png)

---

## Detection Details

![Detection Details](Scenario-2-HTA-Execution/Images/02-detection-details.png)

---

## Process Tree

![Process Tree](Scenario-2-HTA-Execution/Images/03-process-tree.png)

---

## Event Timeline

![Event Timeline](Scenario-2-HTA-Execution/Images/04-event-timeline.png)

---

## Alert Closure

![Alert Closed](Scenario-2-HTA-Execution/Images/05-alert-closed.png)

---

## Prevention Demonstration

🎥 Video

Scenario-2-HTA-Blocked.mp4

---

# Scenario 3 – PowerShell Execution via MSHTA

### Technique

- MSHTA launches PowerShell
- PowerShell executes suspicious commands
- Falcon generates multiple behavioral detections
- Process blocked before completion

## Detection Overview

![Detection Overview](Scenario-3-PowerShell-Execution/Images/01-detection-overview.png)

---

## Process Tree

![Process Tree](Scenario-3-PowerShell-Execution/Images/02-process-tree.png)

---

## Event Timeline

![Event Timeline](Scenario-3-PowerShell-Execution/Images/03-event-timeline.png)

---

## Alert Closure

![Alert Closed](Scenario-3-PowerShell-Execution/Images/04-alert-closed.png)

---

## Prevention Demonstration

🎥 Video

Scenario-3-PowerShell-Blocked.mp4

---

# 🔍 Investigation Workflow

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

# 🛡️ CrowdStrike Detection Summary

Across all three attack scenarios, CrowdStrike Falcon successfully identified suspicious MSHTA activity using behavioral analytics rather than traditional signature-based detection.

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

# 📊 Detection Comparison

| Scenario | Execution Method | MITRE Technique | Falcon Response |
|-----------|-----------------|----------------|----------------|
| Scenario 1 | VBScript | T1218.005 | Process Blocked |
| Scenario 2 | HTA | T1218.005 | Process Killed |
| Scenario 3 | PowerShell | T1218.005 | Process Blocked |

---

# 🎯 MITRE ATT&CK Mapping

## Atomic Red Team Simulation

- **T1218.005 – Mshta**

## CrowdStrike Behavioral Detections

During execution, Falcon generated behavioral detections associated with:

- User Execution
- Command and Scripting Interpreter
- Defense Evasion
- Exploitation for Defense Evasion

This demonstrates that behavioral EDR detections may differ from the original Atomic Red Team technique while still identifying malicious activity.

---

# 🔎 Key Findings

- MSHTA can execute multiple script types without requiring additional executables.
- CrowdStrike relied on behavioral analytics instead of signature-based detection.
- Different execution methods generated different behavioral detections.
- AI Powered IOAs successfully correlated suspicious process activity.
- Parent-child process relationships provided valuable investigation context.
- Falcon interrupted execution before persistence or system compromise occurred.

---

# 📈 Investigation Outcome

All three simulated attack scenarios were successfully detected by CrowdStrike Falcon.

The platform generated multiple behavioral detections, correlated related process activity, and prevented execution by blocking or terminating suspicious processes.

No persistence, credential theft, privilege escalation, lateral movement, or unauthorized compromise occurred because all activity was intentionally executed inside a controlled home SOC laboratory.

---

# 📋 Incident Classification

| Field | Value |
|--------|-------|
| Classification | Benign True Positive |
| Severity | High |
| Status | Closed |
| Environment | Home SOC Lab |
| Root Cause | Authorized Atomic Red Team simulation |
| Business Impact | None |

---

# 🧠 Skills Demonstrated

- CrowdStrike Falcon Investigation
- Endpoint Detection & Response (EDR)
- AI Powered IOA Analysis
- Process Tree Analysis
- Event Timeline Investigation
- Behavioral Detection Analysis
- MITRE ATT&CK Mapping
- Living-off-the-Land Binary (LOLBin) Analysis
- Atomic Red Team Testing
- Incident Triage
- Threat Hunting
- IOC Analysis
- SOC Documentation

---

# 📂 Repository Structure

```
Investigation-04-LOLBin-Abuse-Using-MSHTA
│
├── README.md
│
├── Scenario-1-VBScript-Execution
│   ├── Images
│   └── Videos
│
├── Scenario-2-HTA-Execution
│   ├── Images
│   └── Videos
│
└── Scenario-3-PowerShell-Execution
    ├── Images
    └── Videos
```

---

# 📚 Lessons Learned

- Legitimate Windows binaries can be abused to execute malicious code.
- Behavioral EDR detection provides greater visibility than signature-based detection alone.
- Different execution methods of the same ATT&CK technique can produce different behavioral detections.
- Reviewing process relationships and command-line arguments is essential during endpoint investigations.
- CrowdStrike Falcon effectively detected and prevented multiple MSHTA abuse techniques inside a controlled SOC lab.
