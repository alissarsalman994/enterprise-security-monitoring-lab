# 05 - Splunk Universal Forwarder



---



## 1. Overview



The Splunk Universal Forwarder was deployed on all Windows systems within the Active Directory environment to securely forward Windows event logs to the centralized Splunk Enterprise server.



The forwarder enables centralized visibility across the enterprise by collecting endpoint telemetry, including Windows Security events, Sysmon events, and PowerShell logging.



---



## 2. Deployment Architecture



| Device | Operating System | Universal Forwarder |
|---------|------------------|---------------------|
| DC01 | Windows Server 2016 | Installed |
| WS01 | Windows 11 | Installed |
| WS02 | Windows 11 | Installed |



Destination Server



| Setting | Value |
|---------|-------|
| Splunk Server | splunk |
| Operating System | Ubuntu Server 22.04 LTS |
| Receiver Port | 9997 |
| Web Interface | 8000 |



---



## 3. Data Sources



The Universal Forwarder was configured to collect the following log sources.



| Log Source | Purpose |
|------------|---------|
| Windows Security | Authentication, account management and auditing |
| Sysmon | Process creation, network connections and endpoint telemetry |
| Windows PowerShell | Module Logging and Script Block Logging |



---



## 4. Log Forwarding Workflow



The following process is used to centralize endpoint logs.



1. Windows generates security events.

2. Sysmon generates endpoint telemetry.

3. PowerShell generates execution logs.

4. Splunk Universal Forwarder collects configured logs.

5. Events are securely forwarded to Splunk Enterprise.

6. Splunk indexes the events for searching, dashboards and alerting.



---



## 5. Verification



Successful deployment was verified by confirming:



- Splunk Universal Forwarder service running

- Windows Security events visible in Splunk

- Sysmon Operational events received

- PowerShell logging events received

- Windows endpoints reporting successfully



---



## 6. Result



The deployment successfully centralized security telemetry from all Windows systems, providing real-time visibility into authentication activity, endpoint behavior and administrative actions throughout the Active Directory environment.

