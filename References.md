# References

This document contains publicly available sources used throughout the development of the **Regional Cyber Threat Analysis** project, including local, national, and international cybersecurity research, incident analysis, threat intelligence, and defensive SOC methodology.

Sources are provided for research transparency. Information from third-party reporting should be independently validated before making attribution or incident-response decisions.

---

# Local Cyber Incidents

## Chelan County Cyber Incident (2026)

### Public Reporting

* Chelan County cyber incident reporting and recovery updates
* Government Technology reporting on the incident response and recovery process

**Source:**

Government Technology

https://www.govtech.com/security/after-cyber-attack-chelan-county-wash-recovers-server

---

## Okanogan County Cyber Incidents

### 2021 Denial-of-Service Incident

**Source:**

Cyber Security Intelligence Database (CSIDB)

https://www.csidb.net/

**Incident Category:**

* Denial of Service (DoS)

---

### 2026 Qilin Ransomware Incident

**Source:**

DeXpose Threat Intelligence Report

https://www.dexpose.io/qilin-ransomware-strikes-okanogan-county-vets/

**Reported Activity:**

* Ransomware/extortion claim
* Threat of data disclosure
* Qilin ransomware group involvement

**Analyst Note:**

Threat actor claims from ransomware groups should be treated as intelligence leads and validated through additional sources whenever possible.

---

# National SOC Case Studies

## Iranian-Linked OT Activity Targeting U.S. Water Infrastructure

This case study examines publicly reported cyber activity targeting operational technology (OT), including programmable logic controllers (PLCs), used by U.S. water and wastewater utilities.

The following sources support the analysis of reported attacker behaviors, defensive recommendations, and SOC detection opportunities documented in the national case study.

### FBI / EPA — Water and Wastewater PLC Activity

**Federal Bureau of Investigation (FBI) and Environmental Protection Agency (EPA)**

*Malicious Cyber Actors Targeting Water and Wastewater Sector Internet-Facing Programmable Logic Controllers, Causing Operational Disruptions*

**Published:** July 30, 2026

https://www.fbi.gov/investigate/cyber/alerts/2026/malicious-cyber-actors-targeting-water-and-wastewater-sector-internet--facing-programmable-logic-controllers-causing-operational-disruptions

**Supports analysis of:**

* Internet-facing PLC exposure
* Remote access to OT devices
* Unauthorized password changes
* IP address changes
* Loss of monitoring and control
* PLC project file modifications
* Network and authentication investigation
* OT incident response

---

### FBI — Iranian-Affiliated Cyber Actors Exploiting PLCs

**Federal Bureau of Investigation (FBI)**

*Iranian-Affiliated Cyber Actors Exploit Programmable Logic Controllers Across U.S. Critical Infrastructure*

**Published:** 2026

https://www.fbi.gov/investigate/cyber/alerts/2026

**Supports analysis of:**

* Iranian-affiliated cyber activity
* PLC targeting
* Critical infrastructure
* Operational technology
* Threat intelligence
* Adversary behavior

---

### CISA / FBI / NSA / EPA — Iranian-Affiliated PLC Activity

**Cybersecurity and Infrastructure Security Agency (CISA)**

*IRGC-Affiliated Cyber Actors Exploit PLCs in Multiple Sectors, Including U.S. Water and Wastewater Systems Facilities*

https://www.cisa.gov/news-events/cybersecurity-advisories/aa23-335a

**Supports analysis of:**

* Internet-exposed PLCs
* Default or weak credentials
* PLC and HMI targeting
* Iranian-affiliated threat activity
* OT security controls
* Network segmentation
* Remote access protection

---

# Washington State Cybersecurity Statistics

**Source:**

Washington State Office of the Attorney General

**Data Breach Live Statistics**

https://www.atg.wa.gov/data-breach-live-statistics

**Purpose:**

Used to understand broader cybersecurity trends affecting organizations in Washington State.

---

# MITRE ATT&CK Framework

MITRE ATT&CK is used throughout this project to map adversary behaviors to recognized tactics and techniques and to support threat-informed detection engineering and SOC investigation.

## MITRE ATT&CK Enterprise

**Source:**

MITRE ATT&CK Enterprise

https://attack.mitre.org/

**Referenced for:**

* Threat behavior mapping
* Attack lifecycle analysis
* Detection engineering
* SOC investigation methodology
* Threat-informed defense
* Enterprise and network-based adversary activity

**Relevant Enterprise Techniques:**

| Technique                 | ID        | Description                                                   |
| ------------------------- | --------- | ------------------------------------------------------------- |
| Phishing                  | T1566     | Adversaries attempt to gain access through phishing campaigns |
| Valid Accounts            | T1078     | Use of legitimate credentials for access                      |
| Command and Control       | T1071     | Communication using application layer protocols               |
| Remote Services           | T1021     | Remote access and lateral movement techniques                 |
| SMB/Windows Admin Shares  | T1021.002 | Windows file sharing and administrative access                |
| Data Encrypted for Impact | T1486     | Ransomware encryption activity                                |

---

## MITRE ATT&CK for ICS

**Source:**

MITRE ATT&CK for Industrial Control Systems (ICS)

https://attack.mitre.org/matrices/ics/

**Referenced for:**

* Operational technology (OT) threat analysis
* Industrial control system (ICS) attack behavior
* PLC and HMI targeting
* Industrial process manipulation
* OT-specific detection engineering
* Threat-informed defense of industrial environments

**Project Application:**

The MITRE ATT&CK for ICS knowledge base is used specifically for national OT case studies involving industrial control systems, programmable logic controllers (PLCs), human-machine interfaces (HMIs), and other industrial environments.

Case-specific ATT&CK for ICS technique mappings are documented within the applicable case study and are not duplicated in this master reference section.

---

# Analyst Methodology

This project applies defensive cybersecurity analysis practices including:

* Threat intelligence research
* Public-source intelligence (OSINT) research
* Validation and cross-checking of public reporting
* Separation of confirmed facts from assumptions
* Threat behavior analysis
* MITRE ATT&CK alignment
* Detection engineering
* SOC investigation methodology
* Defensive recommendations based on observable behaviors

Threat-actor attribution is not treated as a substitute for technical evidence.

Public reporting and threat-intelligence claims should be independently validated before being used for attribution or incident-response decisions.
