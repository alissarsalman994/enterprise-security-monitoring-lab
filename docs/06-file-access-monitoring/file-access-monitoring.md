# 06 - File Access Monitoring



---



# 1. Overview



This document describes the implementation of centralized file access monitoring within the Active Directory environment. Departmental shared folders were created on the Domain Controller and secured using Active Directory security groups, NTFS permissions, and Share permissions.



Windows Security Auditing was configured through Group Policy to generate detailed audit events whenever users accessed, modified, or attempted to access protected resources. These events were forwarded to Splunk Enterprise for centralized monitoring, investigation, and visualization.



---



# 2. Objectives



The objectives of this implementation were to:



- Create secure departmental file shares.

- Restrict access using the principle of least privilege.

- Monitor successful and failed file access attempts.

- Detect unauthorized access to sensitive departmental resources.

- Visualize file access activity using Splunk dashboards.



---



# 3. Department Shares



The following departmental shares were created on the Domain Controller.



| Department | Security Group |
|------------|----------------|
| Finance | Finance |
| Human Resources | HR |
| Information Technology | IT\_Admins |
| Sales | Sales |



Each department was granted access only to its designated folder.



---



# 4. Access Control Implementation



Access to each departmental share was controlled using two permission layers.



## NTFS Permissions



NTFS permissions were configured to ensure only authorized users could access departmental folders.



## Share Permissions



Share permissions were configured to allow network access while maintaining security through Active Directory group membership.



The combination of NTFS and Share permissions ensured users could only access resources assigned to their department.



---



# 5. Windows Security Auditing



Group Policy was configured to audit file system activity on the departmental shares.



Auditing was enabled for both successful and failed access attempts.



This generated Windows Security events whenever users attempted to access protected folders.



---



# 6. Security Events Collected



The following Windows Security Event IDs were monitored.



| Event ID | Description |
|----------|-------------|
| 4656 | Handle requested to an object |
| 4663 | Object accessed |
| 5140 | Network share accessed |
| 5145 | Detailed network share access |



These events were forwarded to Splunk Enterprise through the Splunk Universal Forwarder.



---



# 7. Detection Validation



Multiple validation scenarios were performed to confirm that auditing and monitoring were functioning correctly.



Validation included:



- Authorized access to departmental folders.

- Unauthorized access attempts.

- Successful file access.

- Failed file access.

- Verification of generated Windows Security events.

- Verification of log ingestion within Splunk Enterprise.



All expected audit events were successfully generated and indexed.



---



# 8. Dashboard Implementation



A dedicated dashboard named \*\*Active Directory Security Monitoring\*\* was created within Splunk Enterprise to visualize departmental file access activity.



The dashboard includes:



- Total Failed Access Attempts

- Successful Access Attempts

- Failed Access Attempts by Department

- Top Users Triggering Failed Access

- Recent Failed Access Attempts



These visualizations provide real-time visibility into user activity across departmental file shares.



---



# 9. Security Benefits



Implementing centralized file access monitoring provides several security benefits, including:



- Visibility into user access to sensitive resources.

- Detection of unauthorized access attempts.

- Support for incident investigation.

- Improved auditability of enterprise file systems.

- Centralized monitoring through Splunk Enterprise.



---



# 10. Summary



Departmental file shares were successfully secured using Active Directory security groups and Windows permissions. File access auditing generated detailed Windows Security events that were centralized within Splunk Enterprise, enabling real-time monitoring of authorized and unauthorized access attempts across the enterprise environment.

