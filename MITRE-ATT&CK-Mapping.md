# MITRE ATT&CK Mapping: Regional Cyber Threat Analysis

## Purpose

This document maps common attacker behaviors associated with malware, ransomware, and enterprise compromises to the MITRE ATT&CK framework.

The techniques listed below represent defensive analysis opportunities based on common attack patterns. They are not confirmed techniques used in the Chelan County or Okanogan County incidents unless publicly reported.

---

# Attack Lifecycle Mapping

| Tactic | Technique | MITRE ID | Defensive Relevance |
|---|---|---|---|
| Initial Access | Phishing | T1566 | Attackers frequently use phishing emails to obtain access or deliver malware |
| Initial Access | Valid Accounts | T1078 | Compromised credentials may allow attackers to access systems |
| Execution | Command and Scripting Interpreter | T1059 | Attackers may use PowerShell, command shell, or scripts to execute payloads |
| Persistence | Registry Run Keys / Startup Folder | T1547.001 | Malware may create persistence mechanisms to survive reboots |
| Discovery | Network Service Scanning | T1046 | Attackers identify available systems and services after access |
| Credential Access | OS Credential Dumping | T1003 | Attackers attempt to obtain credentials for privilege escalation or movement |
| Command and Control | Application Layer Protocol | T1071 | Malware may communicate with external infrastructure using common protocols |
| Lateral Movement | Remote Services | T1021 | Attackers may move through environments using remote access services |
| Lateral Movement | SMB/Windows Admin Shares | T1021.002 | Attackers may use Windows file sharing for internal movement |
| Impact | Data Encrypted for Impact | T1486 | Ransomware encrypts files and disrupts operations |

---

# SOC Detection Opportunities

## Initial Access Detection

Potential indicators:

- Suspicious email attachments
- Malicious links
- Lookalike domains
- Unexpected authentication events
- External login attempts

Recommended data sources:

- Email security logs
- Identity provider logs
- SIEM alerts

---

## Execution Detection

Potential indicators:

- Unusual PowerShell activity
- Command shell execution from unexpected locations
- Suspicious scripts
- Unknown executable files

Recommended data sources:

- Endpoint Detection and Response (EDR)
- Windows event logs
- Process monitoring

---

## Persistence Detection

Potential indicators:

- New registry run keys
- Startup folder modifications
- New scheduled tasks
- Unauthorized services

Recommended data sources:

- Endpoint telemetry
- Windows Registry monitoring
- File integrity monitoring

---

## Command and Control Detection

Potential indicators:

- Repeated outbound connections
- Unknown external IP addresses
- Suspicious DNS requests
- Beacon-like network patterns

Recommended data sources:

- Firewall logs
- DNS logs
- Network flow data
- IDS/IPS alerts

---

## Lateral Movement Detection

Potential indicators:

- Abnormal SMB traffic
- Remote service usage
- Privileged account movement
- Authentication from unusual systems

Recommended data sources:

- Authentication logs
- Windows security logs
- Network monitoring tools

---

## Impact Detection

Potential indicators:

- Large-scale file modification
- Encryption activity
- Backup deletion attempts
- Service disruption

Recommended data sources:

- Endpoint alerts
- File monitoring
- Backup system logs

---

# Analyst Assessment

A mature SOC investigation focuses on identifying attacker behavior rather than relying only on threat actor attribution.

MITRE ATT&CK provides a common language for:

- Documenting adversary behavior
- Building detection rules
- Improving incident response
- Communicating findings between security teams

---

# Related Training Experience

This mapping aligns with hands-on cybersecurity training and practical security analysis experience completed through:

- TryHackMe SOC learning paths and MITRE ATT&CK exercises
- KC7 cyber investigation labs focused on security monitoring and incident investigation
- MITRE ATT&CK Navigator analysis exercises
- PISCES network monitoring and analysis experience
- HELM Elastic SIEM home lab development focused on network visibility and detection engineering
