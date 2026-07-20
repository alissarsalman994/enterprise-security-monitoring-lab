# 03 - Group Policy Security Baseline



## 1. Objective



Following the successful deployment of Active Directory, a centralized security baseline was implemented using Group Policy Objects (GPOs). The objective of this phase was to establish consistent security settings across all domain-joined systems while improving authentication security, endpoint visibility, and audit logging.



The implemented policies provide the foundation for centralized security management and generate the telemetry required for security monitoring, threat detection, and incident investigation.



---



## 2. Technologies Used



| Component | Technology |
|---|---|
| Operating System | Windows Server 2016 |
| Directory Service | Active Directory Domain Services |
| Policy Management | Group Policy Management Console (GPMC) |
| Target Systems | Windows 11 Domain-Joined Workstations |



---



## 3. Group Policy Deployment



A dedicated Group Policy Object named \*\*Enterprise Security Baseline\*\* was created and linked to the \*\*corp.northbridge.com\*\* domain.



The policy is automatically applied to all domain-joined systems, allowing security settings to be managed from a single centralized location rather than configuring each workstation individually.



---



## 4. Password Policy



To strengthen authentication security, the following password policies were configured.



| Policy | Configuration |
|---|---|
| Enforce Password History | 24 Passwords |
| Maximum Password Age | 90 Days |
| Minimum Password Age | 1 Day |
| Minimum Password Length | 14 Characters |
| Password Complexity | Enabled |
| Store Passwords Using Reversible Encryption | Disabled |



These settings help reduce weak passwords, password reuse, and unauthorized access through credential guessing.



---



## 5. Account Lockout Policy



To reduce the effectiveness of brute-force and password spraying attacks, account lockout policies were configured.



| Policy | Configuration |
|---|---|
| Account Lockout Threshold | 5 Invalid Logon Attempts |
| Account Lockout Duration | 15 Minutes |
| Reset Account Lockout Counter | 15 Minutes |



This configuration balances security with usability by temporarily locking accounts after repeated failed authentication attempts.



---



## 6. Advanced Audit Policy



Windows Advanced Audit Policies were enabled to increase visibility into authentication events, administrative activity, and security-relevant system actions.



The following audit categories were configured:



- Account Logon

- Logon and Logoff

- Account Management

- Detailed Tracking

- Directory Service Access

- Object Access

- Policy Change

- Privilege Use

- System Events



These policies ensure that important security events are written to the Windows Security Event Log, where they can later be collected and analyzed by the SIEM platform.



---



## 7. PowerShell Logging



To improve visibility into PowerShell activity, additional logging was enabled through Group Policy.



The following features were configured:



- PowerShell Script Block Logging

- PowerShell Module Logging

- PowerShell Transcription



These settings provide detailed records of PowerShell execution, improving the ability to investigate administrative actions and detect potentially malicious scripts.



---



## 8. Policy Deployment



After configuration, the Enterprise Security Baseline GPO was linked to the Active Directory domain and applied to domain-joined systems.



Policy deployment was verified by forcing a Group Policy update and confirming that the policy was successfully applied to the target workstations.



Verification included:



- Updating Group Policy using `gpupdate /force`

- Confirming policy application using `gpresult`

- Reviewing configured settings through the Group Policy Management Console



---



## 9. Outcome



A centralized Windows security baseline was successfully implemented across the enterprise environment.



By enforcing password policies, account lockout settings, advanced auditing, and PowerShell logging through Group Policy, the environment now provides stronger authentication controls, improved endpoint visibility, and the audit data required for centralized security monitoring and future detection engineering.



---



## 10. Next Phase



The next phase focuses on deploying Splunk Enterprise and configuring centralized log collection using the Splunk Universal Forwarder.

