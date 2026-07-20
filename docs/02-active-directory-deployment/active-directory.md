# 02 - Active Directory Deployment



## 1. Objective



This phase of the project established the Active Directory infrastructure for the NorthBridge Technologies enterprise environment. A dedicated Windows Server 2016 virtual machine was promoted to a Domain Controller, providing centralized authentication, authorization, DNS, and directory services for all Windows endpoints within the lab.



The Active Directory environment forms the foundation of the enterprise network and will later support Group Policy deployment, centralized security monitoring, attack simulation, and incident investigation.



---



## 2. Technologies Used



| Component | Technology |
|---|---|
| Operating System | Windows Server 2016 |
| Directory Service | Active Directory Domain Services (AD DS) |
| DNS | Microsoft DNS |
| Domain Functional Level | Windows Server 2016 |
| Client Operating System | Windows 11 |
| Management Tools | Server Manager, Active Directory Users and Computers, Group Policy Management |



---



## 3. Domain Configuration



| Setting | Value |
|---|---|
| Organisation | NorthBridge Technologies |
| Active Directory Domain | corp.northbridge.com |
| NetBIOS Name | CORP |
| Domain Controller | DC01 |
| DNS Server | DC01 |
| DNS Address | 192.168.126.10 |



The Domain Controller hosts both Active Directory Domain Services and the integrated DNS service. All Windows clients use the Domain Controller as their preferred DNS server, allowing them to locate domain resources and authenticate users.



---



## 4. Organisational Unit Structure



To simulate a realistic enterprise environment, dedicated Organizational Units (OUs) were created for both business departments and infrastructure components.



### Business Units



- Executive

- Finance

- Human Resources

- Information Technology

- Marketing

- Operations

- Sales



### Infrastructure Units



- Servers

- Workstations

- Groups

- Service Accounts



This structure provides logical separation of users and computer objects while simplifying administration and future Group Policy deployment.



---



## 5. User and Computer Management



Representative user accounts were created for each department to simulate a corporate environment.



Windows endpoints were joined to the Active Directory domain and placed within the Workstations Organizational Unit.



| Computer | Status |
|---|---|
| DC01 | Domain Controller |
| WS01 | Domain Joined |
| WS02 | Domain Joined |


This allows centralized authentication, policy management, and administrative control across all Windows systems.



---



## 6. Domain Services



The Active Directory deployment provides the following services throughout the environment:



- Centralized authentication

- Centralized authorization

- Integrated DNS

- Computer account management

- User account management

- Security group management

- Organizational Unit administration

- Group Policy support



These services form the foundation for the security controls implemented later in the project.



---



## 7. Verification



The Active Directory deployment was verified by confirming:



- Successful promotion of DC01 to Domain Controller

- Successful creation of the corp.northbridge.com domain

- DNS resolution through DC01

- Successful domain join of WS01

- Successful domain join of WS02

- Computer objects appearing in the Workstations OU

- User authentication using domain credentials



Supporting screenshots are stored within:



screenshots/active-directory/



---



## 8. Outcome



A fully functional Active Directory environment was successfully deployed to simulate a small enterprise network. The completed domain infrastructure provides centralized identity management and serves as the foundation for Group Policy, endpoint monitoring, SIEM integration, and future security testing and detection validation as the project continues to evolve.



---



## 9. Next Phase



The next stage focuses on implementing enterprise security controls through Group Policy, including password policies, account lockout settings, advanced auditing, and PowerShell logging.

