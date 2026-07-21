# 08 - MITRE ATT&CK Mapping

## Objective

This section maps the security monitoring capabilities implemented throughout the project to the MITRE ATT&CK Enterprise framework.

Rather than mapping individual Windows Event IDs directly to ATT&CK techniques, the mapping focuses on the adversary behaviours that the implemented logging and monitoring are capable of detecting or supporting during an investigation.

Only techniques that were configured and validated within this project have been included.

---

# MITRE ATT&CK Overview

MITRE ATT&CK (Adversarial Tactics, Techniques, and Common Knowledge) is a globally recognised knowledge base that documents the techniques used by real-world attackers during cyber intrusions.

Many Security Operations Centers (SOCs) use the ATT&CK framework to:

- Understand attacker behaviour
- Build detection rules
- Measure defensive coverage
- Identify visibility gaps
- Improve incident response

Throughout this project, Windows Security Auditing, Sysmon, PowerShell Logging, Active Directory auditing, and Splunk were configured to improve visibility into several ATT&CK techniques.

---

# ATT&CK Coverage Summary

| ATT&CK ID | Technique | ATT&CK Tactic | Lab Detection Evidence |
|-----------|-----------|---------|--------------------|
| T1110.001 | Password Guessing | Credential Access | Windows Event ID 4625, Splunk Alert |
| T1059.001 | PowerShell | Execution | Event IDs 4103, 4104, 4688, Sysmon Event ID 1 |
| T1078.002 | Domain Accounts | Initial Access / Persistence / Privilege Escalation / Defense Evasion | Event IDs 4624 and 4625 |
| T1039 | Data from Network Shared Drive | Collection | Event IDs 4656, 4663, 5140 and 5145 |

---

# Technique 1 - Password Guessing

## ATT&CK Technique

**Technique:** [T1110.001 – Password Guessing](https://attack.mitre.org/techniques/T1110/001/)

### Description

Password guessing involves repeatedly attempting different passwords against a user account until valid credentials are discovered.

Within enterprise environments, repeated authentication failures often indicate either user error or an attacker attempting to gain unauthorized access.

### Lab Implementation

A failed authentication scenario was generated against a domain account.

Windows Security Event ID 4625 recorded each failed logon attempt and forwarded the events to Splunk through the Universal Forwarder.

A Splunk detection rule was then configured to alert whenever more than five failed logon attempts occurred within the defined time period.

### Detection Evidence

- Windows Security Event ID 4625
- Username
- Source workstation
- Failure reason
- Time of authentication
- Splunk failed logon alert

### Outcome

The implemented monitoring provides visibility into repeated authentication failures that may indicate password guessing activity against Active Directory accounts.

---

# Technique 2 - PowerShell

## ATT&CK Technique

**Technique:** [T1059.001 – PowerShell](https://attack.mitre.org/techniques/T1059/001/)

### Description

PowerShell is a legitimate Windows administration tool frequently used by system administrators.

Because of its powerful scripting capabilities, it is commonly used by attackers to execute commands, automate tasks, and perform malicious actions after gaining access to a system.

### Lab Implementation

PowerShell Module Logging, Script Block Logging, and Transcription were enabled through Group Policy.

PowerShell activity generated Events 4103 and 4104.

Additional process execution visibility was provided through Windows Security Event ID 4688 and Sysmon Event ID 1.

### Detection Evidence

- Event ID 4103
- Event ID 4104
- Event ID 4688
- Sysmon Event ID 1
- Executed command line
- Parent process
- User account

### Outcome

The implemented logging provides detailed visibility into PowerShell execution and supports investigations involving suspicious administrative activity.

---

# Technique 3 - Domain Accounts

## ATT&CK Technique

**Technique:** [T1078.002 – Domain Accounts](https://attack.mitre.org/techniques/T1078/002/)

### Description

Adversaries frequently attempt to obtain legitimate domain credentials in order to access internal resources while appearing as authorized users.

Monitoring authentication activity allows analysts to identify abnormal logon behaviour and investigate potential account misuse.

### Lab Implementation

Successful and failed domain authentication events were collected from all domain-joined systems and forwarded to Splunk.

### Detection Evidence

- Event ID 4624
- Event ID 4625
- Username
- Source workstation
- Logon type
- Authentication time

### Outcome

The implemented monitoring supports investigations involving domain account activity.

A successful authentication event alone does not indicate malicious behaviour and should always be correlated with additional evidence.

---

# Technique 4 - Data from Network Shared Drive

## ATT&CK Technique

**Technique:** [T1039 – Data from Network Shared Drive](https://attack.mitre.org/techniques/T1039/)

### Description

Attackers often search accessible network shares to locate sensitive information after gaining access to a network.

Monitoring access to shared folders helps identify both authorized and unauthorized access attempts.

### Lab Implementation

Departmental network shares were protected using Active Directory security groups, NTFS permissions, and Share Permissions.

Object Access Auditing generated Windows Security Events whenever users attempted to access shared folders.

Authorized and unauthorized access attempts were verified within the lab and successfully forwarded to Splunk.

### Detection Evidence

- Event ID 4656
- Event ID 4663
- Event ID 5140
- Event ID 5145
- Username
- Share name
- Requested access
- Access result

### Outcome

The implemented monitoring provides visibility into activity occurring on departmental shared folders and supports investigations involving access to network resources.

---

# Supporting Sysmon Telemetry

Sysmon was deployed across the monitored Windows systems to provide additional endpoint visibility beyond standard Windows Security logging.

The following Sysmon events were validated during the project.

| Event ID | Description |
|-----------|-------------|
| 1 | Process Creation |
| 3 | Network Connection |
| 11 | File Creation |
| 13 | Registry Value Set |

These events improve endpoint visibility and support investigations by providing additional context surrounding process execution, network activity, file creation, and registry modifications.

Although these events are valuable for many ATT&CK techniques, they have not been individually mapped within this document because generic telemetry alone does not necessarily indicate a specific adversary technique.

---

# Summary

The monitoring capabilities implemented throughout this project provide visibility into several common attacker behaviours documented within the MITRE ATT&CK Enterprise framework.

By combining Windows Security Auditing, PowerShell Logging, Sysmon, Active Directory, and Splunk, the environment enables centralized monitoring of authentication activity, PowerShell execution, process creation, and access to shared resources.

The mappings presented in this document represent the detection capabilities validated during the project and should be interpreted as monitoring coverage rather than confirmation that a complete adversary attack was performed.
