# SOC Case Study: Iranian-Linked OT Activity Targeting U.S. Water Infrastructure

**Author:** Stacey Menley<br>
**Created:** August 23, 2026<br>
**Focus:** SOC Analysis | Operational Technology (OT) | Critical Infrastructure | Detection Engineering

---

## 1. Case Summary

In July 2026, U.S. water and wastewater utilities reported cyber incidents involving internet-facing operational technology (OT), including programmable logic controllers (PLCs).

Federal agencies warned that malicious cyber actors were targeting exposed PLCs and that some incidents resulted in operational disruption.

From a SOC perspective, this activity is significant because compromise of OT systems can affect physical processes, operator visibility, and availability of essential services.

Although the activity has been publicly associated with Iranian-affiliated threat actors, attribution should be treated cautiously unless supported by authoritative evidence.

**SOC Focus:**

This case examines observable attacker behavior, potential telemetry, detection opportunities, and analyst investigation steps rather than attempting to prove attribution.

---

## 2. SOC Investigation Objectives

A SOC analyst investigating this activity would attempt to determine:

* Was an OT device exposed to the internet?
* Was unauthorized authentication observed?
* Did an external system establish communication with a PLC?
* Were credentials changed?
* Were PLC configurations modified?
* Was communication between IT and OT networks abnormal?
* Did operator visibility or device availability change?
* What activity occurred immediately before and after the event?

---

## 3. Relevant Attack Surface

| Attack Surface              | SOC Monitoring Concern             |
| --------------------------- | ---------------------------------- |
| Internet-facing PLCs        | Unauthorized inbound connections   |
| Remote administration       | Credential compromise              |
| Default or weak credentials | Authentication attacks             |
| Exposed OT services         | Reconnaissance                     |
| Engineering workstations    | High-value administrative access   |
| IT-to-OT connectivity       | Lateral movement                   |
| PLC management interfaces   | Unauthorized configuration changes |
| HMI systems                 | Loss of operator visibility        |

---

## 4. Reported Attacker Behaviors

Public reporting and federal cybersecurity advisories describe behaviors relevant to defenders, including:

* Targeting internet-exposed PLCs
* Remote access to OT devices
* Unauthorized credential changes
* Disruption of operator access
* Potential manipulation of operational processes
* Targeting water and wastewater infrastructure

These behaviors can be translated into SOC detection opportunities even when complete forensic timelines are unavailable.

---

## 5. MITRE ATT&CK Mapping

| Reported / Suspected Behavior      | MITRE ATT&CK                                                                            | SOC Relevance                                    |
| ---------------------------------- | --------------------------------------------------------------------------------------- | ------------------------------------------------ |
| Exploitation of exposed OT systems | [T1190 - Exploit Public-Facing Application](https://attack.mitre.org/techniques/T1190/) | Monitor internet-facing OT services              |
| Use of legitimate credentials      | [T1078 - Valid Accounts](https://attack.mitre.org/techniques/T1078/)                    | Detect abnormal authentication                   |
| Remote access                      | [T1021 - Remote Services](https://attack.mitre.org/techniques/T1021/)                   | Monitor unexpected remote connections            |
| Network reconnaissance             | [T1046 - Network Service Scanning](https://attack.mitre.org/techniques/T1046/)          | Identify scanning activity                       |
| Manipulation of systems or data    | [T1565 - Data Manipulation](https://attack.mitre.org/techniques/T1565/)                 | Monitor unauthorized changes                     |
| Impact to OT operations            | [MITRE ATT&CK for ICS](https://attack.mitre.org/matrices/ics/)                          | Investigate changes affecting physical processes |

> **Analyst Note:** These mappings represent defensive hypotheses based on publicly reported behavior. They do not establish that every technique was confirmed during the incidents.

---

## 6. Detection Opportunities

### Detection 1 — Internet-Facing PLC Access

**Detection Objective:**

Identify unexpected external access to PLCs or OT management interfaces.

**Potential Telemetry:**

* Firewall logs
* Network flow
* IDS/IPS
* PLC authentication logs
* Remote access logs

**Alert Concept:**

```text
External Source
       ↓
Internet-Facing OT Device
       ↓
Unexpected Connection
```

**Investigate:**

* Source IP
* Destination PLC
* Destination port
* Protocol
* Authentication result
* Previous connections from source
* Whether access was authorized
* Maintenance schedule

---

### Detection 2 — Abnormal PLC Authentication

**Detection Objective:**

Identify possible credential attacks against OT devices.

**Potential Telemetry:**

* PLC authentication logs
* Identity provider logs
* Firewall logs
* Remote access logs
* SIEM authentication events

**Alert Concept:**

```text
Multiple Authentication Failures
       ↓
Successful Authentication
       ↓
OT Device Access
```

**Investigate:**

* Account used
* Source IP
* Number of failures
* Successful authentication
* Device accessed
* Geographic source
* Maintenance window
* Related authentication activity

---

### Detection 3 — Unauthorized PLC Configuration Change

**Detection Objective:**

Detect changes to PLC configuration or control logic outside approved maintenance activity.

**Potential Telemetry:**

* PLC logs
* Engineering workstation logs
* Authentication logs
* Change-management records
* Network telemetry

**Alert Concept:**

```text
Engineering Workstation
       ↓
PLC Configuration Change
       ↓
Outside Approved Maintenance Window
```

**Investigate:**

* Engineering workstation
* User account
* Source IP
* Configuration changed
* Time of change
* Known-good configuration
* Related authentication events
* Other systems accessed by the same account

---

### Detection 4 — Loss of OT Monitoring

**Detection Objective:**

Identify unexpected loss of communication between PLCs/HMIs and monitoring systems.

**Potential Telemetry:**

* Network monitoring
* Firewall logs
* HMI logs
* PLC availability monitoring
* SIEM alerts

**Alert Concept:**

```text
PLC / HMI
    ↓
Loss of Expected Communication
    ↓
Monitoring System Alert
```

**Investigate:**

* Network connectivity
* Device availability
* Authentication changes
* Firewall events
* Configuration changes
* Other devices affected at the same time

---

### Detection 5 — Unexpected IT-to-OT Communication

**Detection Objective:**

Identify unauthorized communication from corporate systems into the OT environment.

**Potential Telemetry:**

* Firewall logs
* NetFlow
* IDS/IPS
* Endpoint telemetry
* DNS logs
* SIEM network events

**Alert Concept:**

```text
Corporate Endpoint
       ↓
Unexpected OT Connection
       ↓
PLC / HMI / Engineering System
```

**Investigate:**

* Source workstation
* Destination PLC
* Protocol
* Port
* User
* Process generating the connection
* Previous communication history
* Whether the connection is normally authorized

---

## 7. SOC Investigation Workflow

When an alert is generated, the analyst should establish:

### WHO?

* User account
* Engineering account
* Source system
* Administrative account

### WHAT?

* PLC
* HMI
* Engineering workstation
* Configuration change
* Authentication event
* Network connection

### WHEN?

* First observed activity
* Authentication time
* Configuration change time
* Last known-good activity
* Maintenance window

### WHERE?

* Source IP
* Destination IP
* OT network segment
* External infrastructure
* Geographic origin

### WHAT CHANGED?

* Credentials
* Configuration
* Control logic
* Network connectivity
* Device availability
* Operator visibility

---

## 8. Detection Engineering Considerations

A mature detection should avoid relying on a single indicator.

For example:

```text
External Connection
       +
Authentication Success
       +
OT Device Access
       +
Configuration Change
       =
High-Priority Investigation
```

Additional context should be incorporated where available:

* Asset criticality
* Known maintenance windows
* User identity
* Source reputation
* Historical communication patterns
* Network segmentation
* Device baseline

The strongest detection logic should combine multiple signals rather than alerting on a single event in isolation.

---

## 9. Defensive Controls

Recommended defensive controls include:

* Remove PLCs and OT devices from direct internet exposure
* Enforce unique credentials
* Restrict remote access
* Segment IT and OT networks
* Monitor OT network traffic
* Restrict communication to authorized systems
* Maintain known-good PLC configurations
* Monitor engineering workstation activity
* Maintain manual operating procedures for critical processes

These controls support both prevention and SOC visibility.

---

## 10. Analyst Assessment

This case demonstrates several important SOC principles:

* OT security requires visibility beyond traditional endpoint telemetry.
* Internet-exposed industrial devices create significant attack surface.
* Authentication activity can provide early indicators of compromise.
* Configuration changes may be more important than traditional malware alerts.
* Network monitoring is critical when endpoint visibility is limited.
* Threat intelligence can be translated into concrete detection opportunities.
* Attribution should remain separate from behavioral analysis when evidence is incomplete.

### Primary SOC Takeaway

> **Detect the behavior, validate the telemetry, establish the timeline, and investigate the impact.**

---

## 11. Analyst Skills Demonstrated

This case demonstrates practical SOC skills including:

* Threat intelligence analysis
* OT security monitoring
* MITRE ATT&CK mapping
* Detection engineering
* Network security monitoring
* Authentication analysis
* Incident investigation methodology
* Alert triage
* Defensive security analysis

---

## 12. References

The following sources provide the authoritative and technical context used to develop this case study. Sources are included directly in this document so the case study can be reviewed independently without requiring a separate reference file.

### Federal Government and Critical Infrastructure Sources

* [CISA — Water and Wastewater Sector](https://www.cisa.gov/topics/critical-infrastructure-security-and-resilience/critical-infrastructure-sectors/water-and-wastewater-sector) — Federal cybersecurity and critical-infrastructure guidance relevant to U.S. water and wastewater organizations.

* [CISA — Industrial Control Systems Advisories](https://www.cisa.gov/news-events/ics-advisories) — Technical advisories concerning industrial control systems, vulnerabilities, and defensive mitigations.

* [CISA — Cybersecurity Performance Goals](https://www.cisa.gov/cybersecurity-performance-goals-cpgs) — Recommended baseline cybersecurity practices for critical infrastructure organizations.

* [FBI — Cybersecurity](https://www.fbi.gov/investigate/cyber) — Federal cybersecurity information and reporting from the Federal Bureau of Investigation.

* [NSA — Cybersecurity Advisories and Guidance](https://www.nsa.gov/Press-Room/Cybersecurity-Advisories-Guidance/) — National Security Agency cybersecurity guidance and technical resources.

### MITRE ATT&CK Sources

* [MITRE ATT&CK — T1190: Exploit Public-Facing Application](https://attack.mitre.org/techniques/T1190/)

* [MITRE ATT&CK — T1078: Valid Accounts](https://attack.mitre.org/techniques/T1078/)

* [MITRE ATT&CK — T1021: Remote Services](https://attack.mitre.org/techniques/T1021/)

* [MITRE ATT&CK — T1046: Network Service Scanning](https://attack.mitre.org/techniques/T1046/)

* [MITRE ATT&CK — T1565: Data Manipulation](https://attack.mitre.org/techniques/T1565/)

* [MITRE ATT&CK for ICS](https://attack.mitre.org/matrices/ics/) — Industrial Control Systems-specific adversary tactics, techniques, and procedures.

### Cybersecurity Reporting

* [Recorded Future News — The Record](https://therecord.media/) — Cybersecurity reporting and analysis concerning nation-state activity, critical infrastructure, and cyber operations.

### Source Validation Note

This case study distinguishes between confirmed reporting, publicly documented attacker behavior, and analyst inference.

MITRE ATT&CK techniques are used to translate reported behaviors into defensive detection hypotheses. Their inclusion does not independently establish that a specific technique was confirmed during the incidents.

Public reporting and threat-intelligence claims should be independently validated before being used for attribution, incident response, or operational decision-making.

**Research approach:** The analysis prioritizes authoritative government and technical sources where available and uses reputable cybersecurity reporting for additional context. The primary analytical focus is on observable behavior, telemetry, detection opportunities, and SOC investigation methodology rather than attribution alone.

