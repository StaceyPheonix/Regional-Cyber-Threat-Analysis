# SOC Case Study: Iranian-Linked OT Activity Targeting U.S. Water Infrastructure

**Author:** Stacey Menley  
**Created:** August 23, 2026  
**Focus:** SOC Analysis | Operational Technology (OT) | Critical Infrastructure | Detection Engineering

---

## 1. Case Summary

In July 2026, U.S. water and wastewater utilities reported cyber incidents involving internet-facing operational technology (OT), including programmable logic controllers (PLCs).

Federal agencies warned that malicious cyber actors were targeting exposed PLCs and that some incidents resulted in operational disruption.

The activity is significant from a Security Operations Center (SOC) perspective because compromise of OT systems can affect physical processes, operator visibility, and availability of essential services.

Although the activity has been widely discussed in connection with Iranian-affiliated threat actors, recent incidents have not been publicly and definitively attributed to Iran by U.S. federal investigators.

This case study focuses on the reported attacker behavior and the resulting SOC detection opportunities rather than threat-actor attribution.

---

## 2. Why This Matters to a SOC

OT environments differ from traditional enterprise IT environments.

A SOC analyst must consider:

- Availability of physical processes
- Safety implications
- PLC and HMI communications
- Engineering workstation activity
- Remote access
- Authentication behavior
- Network segmentation
- Changes to controller configurations

A successful compromise may not initially appear as traditional malware.

Instead, suspicious activity may appear as:

- An unexpected remote connection
- Unauthorized authentication
- PLC configuration changes
- Password changes
- Loss of operator visibility
- Unexpected communication between IT and OT systems

---

## 3. Attack Surface

The reported activity highlights several areas that should receive SOC monitoring:

| Attack Surface | SOC Concern |
|---|---|
| Internet-facing PLCs | Unauthorized remote access |
| Remote administration | Compromised credentials |
| Default or weak credentials | Account compromise |
| Exposed OT services | External reconnaissance |
| Poor network segmentation | IT-to-OT movement |
| Engineering workstations | High-value access point |
| PLC configuration interfaces | Unauthorized process changes |

---

## 4. Reported Attacker Behavior

Public reporting and federal advisories identify several behaviors relevant to defenders:

- Targeting internet-exposed PLCs
- Remote access to OT devices
- Unauthorized changes to device credentials
- Disruption of operator access
- Potential manipulation of operational processes
- Targeting of water and wastewater infrastructure

These behaviors provide useful detection opportunities even when complete forensic timelines are unavailable.

---

## 5. MITRE ATT&CK Mapping

| Behavior | MITRE ATT&CK | SOC Relevance |
|---|---|---|
| External access to exposed systems | T1190 - Exploit Public-Facing Application | Monitor exposed OT services |
| Valid credentials | T1078 - Valid Accounts | Detect abnormal authentication |
| Remote access | T1021 - Remote Services | Monitor unexpected remote connections |
| Network discovery | T1046 - Network Service Scanning | Identify reconnaissance |
| Configuration manipulation | T1565 - Data Manipulation | Monitor unauthorized changes |
| Impact to operational processes | T1495 - Firmware Corruption / OT impact concepts | Investigate controller integrity |

> **Analyst note:** ATT&CK mappings represent defensive hypotheses based on reported behavior. They do not establish that every mapped technique was confirmed in these incidents.

---

## 6. Detection Opportunities

### Detection 1 - Internet-Facing PLC Access

**Alert concept:**

Unexpected inbound connection to a PLC or OT management interface.

**Investigate:**

- Source IP
- Destination PLC
- Destination port
- Authentication result
- Time of connection
- Previous connections from the source
- Whether access was authorized

---

### Detection 2 - Abnormal PLC Authentication

**Alert concept:**

Repeated authentication failures followed by a successful login to an OT device.

**Investigate:**

- Account used
- Source IP
- Number of failures
- Successful authentication
- Device accessed
- Geographic source
- Maintenance schedule

---

### Detection 3 - Unauthorized PLC Configuration Change

**Alert concept:**

PLC configuration or control logic changes outside an approved maintenance window.

**Investigate:**

- Engineering workstation
- User account
- Source IP
- Configuration change
- Time of change
- Previous known-good configuration
- Related authentication events

---

### Detection 4 - Loss of OT Monitoring

**Alert concept:**

PLC or HMI suddenly stops communicating with the monitoring system.

**Investigate:**

- Network connectivity
- Device availability
- Authentication changes
- Firewall events
- Configuration changes
- Other affected devices

---

### Detection 5 - Unexpected IT-to-OT Communication

**Alert concept:**

A corporate endpoint communicates directly with an OT controller without an established business requirement.

**Investigate:**

- Source workstation
- Destination PLC
- Protocol
- Port
- User
- Process generating the connection
- Previous communication history

---

## 7. SOC Investigation Workflow

When an alert is generated, the analyst should establish:

### Who?

- User account
- Engineering account
- Source system

### What?

- PLC
- HMI
- Engineering workstation
- Configuration or credential change

### When?

- Timestamp
- Maintenance window
- First observed activity
- Duration

### Where?

- Source IP
- Destination IP
- OT network segment
- External infrastructure

### What changed?

- Credentials
- Configuration
- Control logic
- Network connectivity
- Device availability

---

## 8. Defensive Controls

Recommended controls include:

- Remove PLCs and other OT devices from direct internet exposure
- Enforce unique credentials
- Restrict remote access
- Segment IT and OT networks
- Monitor OT network traffic
- Restrict communications to authorized systems
- Maintain known-good PLC configurations
- Monitor engineering workstation activity
- Maintain manual operating procedures for critical processes

---

## 9. Analyst Takeaways

This case demonstrates several important SOC principles:

- OT security requires visibility beyond traditional endpoint telemetry.
- Internet-exposed industrial devices create a significant attack surface.
- Authentication events can provide early indicators of compromise.
- Configuration changes may be more important than traditional malware alerts.
- Network monitoring is critical when endpoint visibility is limited.
- Threat intelligence can be translated into concrete detection opportunities.
- Attribution should remain separate from behavioral analysis when evidence is incomplete.
