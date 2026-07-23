# 09 - Project Summary and Evaluation

# Executive Summary

This project documents the implementation of a Windows-based enterprise security monitoring environment using Active Directory, Group Policy, Sysmon, Windows Security Auditing, PowerShell logging, and Splunk Enterprise. The lab simulates a small enterprise network where centralized logging, endpoint monitoring, and access controls are used to monitor authentication activity, process execution, PowerShell usage, and access to shared resources.

Windows endpoints were configured to generate security telemetry that was forwarded to Splunk using Universal Forwarders for centralized collection and analysis. Additional controls, including Active Directory security groups, NTFS permissions, and Share Permissions, were implemented to secure departmental network shares and monitor both authorized and unauthorized access attempts.

The project also includes documentation covering the environment configuration, implemented security controls, detection capabilities, Windows event monitoring, file access auditing, and mapping of validated detections to the MITRE ATT&CK framework.

---

# Implemented Security Controls

The following security controls were successfully implemented throughout the project.

- Active Directory Domain Services (AD DS)
- Organizational Units (OUs)
- Domain users and security groups
- Group Policy Objects (GPOs)
- Windows Security Auditing
- PowerShell Module Logging
- PowerShell Script Block Logging
- PowerShell Transcription
- Sysmon endpoint monitoring
- Splunk Enterprise
- Splunk Universal Forwarders
- Departmental network shares
- NTFS permissions
- Share permissions
- Centralized event collection
- Failed logon detection

Each control was configured, validated, and documented throughout the project.

---

# Detection Capabilities

The completed environment provides visibility into several common Windows activities through centralized logging.

The validated monitoring capabilities include:

- Successful domain logons
- Failed authentication attempts
- PowerShell execution
- Process creation
- File creation
- Registry modifications
- Network connections
- Network share access
- File access activity
- User account management events

These events provide sufficient visibility to support basic security investigations and demonstrate how endpoint telemetry can be centralized within Splunk.

---

# Logging Coverage

The project successfully collected telemetry from multiple Windows logging sources.

## Windows Security Log

Collected events include:

- Event ID 4624 – Successful logon
- Event ID 4625 – Failed logon
- Event ID 4656 – Handle requested
- Event ID 4663 – Object access
- Event ID 4688 – Process creation
- Event ID 5140 – Network share accessed
- Event ID 5145 – Detailed share access

## PowerShell Operational Log

Collected events include:

- Event ID 4103 – Module Logging
- Event ID 4104 – Script Block Logging

## Sysmon

Validated Sysmon telemetry includes:

- Event ID 1 – Process Creation
- Event ID 3 – Network Connection
- Event ID 11 – File Creation
- Event ID 13 – Registry Value Set

All validated telemetry was successfully forwarded to Splunk Enterprise through the configured Universal Forwarders.

---

# Project Strengths

The completed environment demonstrates several enterprise security concepts within a single integrated lab.

Key strengths include:

- Centralized log collection through Splunk
- Active Directory domain administration
- Endpoint monitoring using Sysmon
- Windows native security auditing
- PowerShell logging
- Departmental access control through Active Directory groups
- NTFS and Share permission implementation
- Detection of repeated failed authentication attempts
- Mapping monitoring capabilities to the MITRE ATT&CK framework

Rather than focusing on a single technology, the project demonstrates how multiple Microsoft security technologies can be integrated to improve visibility across an enterprise environment.

---

# Project Limitations

Although the environment provides useful security visibility, it represents a simplified enterprise network and does not include every security capability found within a production environment.

Current limitations include:

- Monitoring is limited to Windows systems.
- No Endpoint Detection and Response (EDR) platform has been implemented.
- Detection content is limited to basic monitoring and correlation searches.
- Email security telemetry is not collected.
- Firewall, VPN, and network appliance logs are not integrated into Splunk.
- Threat intelligence feeds are not integrated.
- Automated incident response has not been implemented.

These limitations were intentionally accepted to maintain a realistic project scope while focusing on Windows event monitoring and centralized log collection.

---

# Future Enhancements

Several improvements could further expand the environment.

Potential enhancements include:

- Microsoft Defender for Endpoint integration
- Windows Event Forwarding (WEF)
- Sigma rule implementation
- Threat intelligence integration
- Automated alerting using Splunk Enterprise Security
- SOAR integration for automated incident response
- Additional Windows servers and workstations
- Linux endpoint monitoring
- Network device log collection
- Email security monitoring

These enhancements would increase monitoring coverage, improve detection capabilities, and further align the environment with enterprise security operations.

---

# Project Outcomes

The project successfully demonstrates the implementation of a Windows-based security monitoring environment using Active Directory, Group Policy, Sysmon, Windows Security Auditing, PowerShell logging, and Splunk Enterprise.

The completed environment provides centralized visibility into authentication activity, process execution, PowerShell usage, network share access, file access, and endpoint telemetry across multiple Windows systems.

Throughout the project, enterprise security concepts including identity management, access control, endpoint monitoring, log management, and security event analysis were implemented, validated, and documented.

The completed lab provides a practical foundation for future expansion into more advanced detection engineering, threat hunting, incident response, and enterprise security monitoring.