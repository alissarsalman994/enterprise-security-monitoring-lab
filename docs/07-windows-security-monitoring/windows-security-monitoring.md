# 07 - Windows Security Monitoring



---



# 1. Overview



This document describes the implementation of centralized Windows security monitoring within the Active Directory environment. Windows Security logs, Sysmon telemetry, and PowerShell logs were collected from all Windows systems and forwarded to Splunk Enterprise for centralized monitoring, investigation, and visualization.



The monitoring solution provides visibility into authentication activity, PowerShell execution, process creation, and endpoint telemetry across the environment, allowing security events to be monitored from a single platform.



---



# 2. Objectives



The objectives of this implementation were to:



- Centralize Windows security telemetry.

- Monitor user authentication activity.

- Detect failed logon attempts.

- Monitor PowerShell activity.

- Collect enhanced endpoint telemetry using Sysmon.

- Visualize security events through Splunk dashboards.



---



# 3. Windows Security Monitoring



Windows Security auditing was configured through Group Policy to generate security events related to authentication, account management, policy changes, privilege use, and process creation.



These events were forwarded to Splunk Enterprise, providing centralized visibility into security activity across all Windows systems within the Active Directory environment.



---



# 4. PowerShell Logging



PowerShell Module Logging and Script Block Logging were enabled through Group Policy to improve visibility into PowerShell activity.



Collecting these events allows administrators and security analysts to review executed PowerShell commands and investigate suspicious or unauthorized administrative activity.



---



# 5. Sysmon Monitoring



Sysmon was deployed across all Windows systems to provide enhanced endpoint telemetry beyond standard Windows Security logs.



The configured deployment provides visibility into:



- Process creation

- Network connections

- Driver loading

- Image loading

- File creation

- Registry activity



This additional telemetry strengthens endpoint monitoring and supports security investigations.



---



# 6. Security Events Collected



The following event sources were monitored throughout the environment.



| Event Source | Event IDs | Purpose |
|--------------|-----------|---------|
| Windows Security | 4624 | Successful user logons |
| Windows Security | 4625 | Failed user logons |
| Windows Security | 4688 | Process creation |
| Windows PowerShell | 4103 | Module Logging |
| Windows PowerShell | 4104 | Script Block Logging |
| Sysmon | Multiple Event IDs | Enhanced endpoint telemetry |



---



# 7. Detection Validation



The monitoring configuration was validated by generating and reviewing security events within the environment.



Validation activities included:



- Successful user authentication.

- Failed logon attempts.

- PowerShell command execution.

- Process creation events.

- Verification of Windows Security events.

- Verification of Sysmon telemetry.

- Verification of PowerShell logging.

- Confirmation that all events were successfully received and indexed by Splunk Enterprise.



The generated events were successfully collected and made available for searching, dashboard visualization, and investigation.



---



# 8. Dashboard Implementation



A dedicated dashboard named \*\*Windows Security Monitoring\*\* was created within Splunk Enterprise to provide centralized visibility into Windows security activity.



The dashboard includes:



- Failed Logon Attempts

- Failed Logons Over Time

- Top Users with Failed Logons

- Top Source IP Addresses

- PowerShell Activity

- Recent PowerShell Commands

- Recent Security Events



Together with the \*\*Active Directory Security Monitoring\*\* dashboard described in Document 06, these dashboards provide centralized visibility into authentication activity, endpoint behavior, and file access across the Active Directory environment.



---



# 9. Security Benefits



Implementing centralized Windows security monitoring provides several security benefits, including:



- Early detection of authentication failures.

- Improved visibility into PowerShell activity.

- Enhanced endpoint telemetry through Sysmon.

- Faster investigation of security events.

- Centralized analysis using Splunk Enterprise.

- Improved visibility across the Active Directory environment.



---



# 10. Summary



Windows Security auditing, Sysmon, and PowerShell logging were successfully centralized within Splunk Enterprise, providing comprehensive visibility into endpoint activity across the Active Directory environment.



The implemented monitoring solution enables efficient detection, investigation, and visualization of authentication events, PowerShell activity, and endpoint telemetry through centralized dashboards and searchable security logs.

