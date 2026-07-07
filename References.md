# References

This document contains publicly available sources used during the development of this defensive cybersecurity analysis.

Sources are provided for research transparency. Information from third-party reporting should be independently validated before making attribution or incident response decisions.

---

# Chelan County Cyber Incident (2026)

## Public Reporting

- Chelan County cyber incident reporting and recovery updates
- Government Technology reporting on the incident response and recovery process

Source:

Government Technology  
https://www.govtech.com/security/after-cyber-attack-chelan-county-wash-recovers-server

---

# Okanogan County Cyber Incidents

## 2021 Denial-of-Service Incident

Source:

Cyber Security Intelligence Database (CSIDB)  
https://www.csidb.net/

Incident Category:
- Denial of Service (DoS)

---

## 2026 Qilin Ransomware Incident

Source:

DeXpose Threat Intelligence Report  
https://www.dexpose.io/qilin-ransomware-strikes-okanogan-county-vets/

Reported Activity:
- Ransomware/extortion claim
- Threat of data disclosure
- Qilin ransomware group involvement

Analyst Note:

Threat actor claims from ransomware groups should be treated as intelligence leads and validated through additional sources whenever possible.

---

# Washington State Cybersecurity Statistics

Source:

Washington State Office of the Attorney General  
Data Breach Live Statistics

https://www.atg.wa.gov/data-breach-live-statistics

Purpose:

Used to understand broader cybersecurity trends affecting organizations in Washington State.

---

# MITRE ATT&CK Framework

Source:

MITRE ATT&CK Enterprise Framework

https://attack.mitre.org/

Referenced for:

- Threat behavior mapping
- Attack lifecycle analysis
- Detection methodology

Relevant Techniques:

| Technique | ID | Description |
|---|---|---|
| Phishing | T1566 | Adversaries attempt to gain access through phishing campaigns |
| Valid Accounts | T1078 | Use of legitimate credentials for access |
| Command and Control | T1071 | Communication using application layer protocols |
| Remote Services | T1021 | Remote access and lateral movement techniques |
| SMB/Windows Admin Shares | T1021.002 | Windows file sharing and administrative access |
| Data Encrypted for Impact | T1486 | Ransomware encryption activity |

---

# Analyst Methodology

This project applies defensive analysis practices including:

- Threat intelligence research
- Validation of public reporting
- Separation of confirmed facts from assumptions
- MITRE ATT&CK alignment
- SOC detection-focused analysis
