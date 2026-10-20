# SOC Brute Force and Persistence Investigation

## Overview

This project is a small SOC investigation in my isolated home lab focused on suspicious login activity on a Windows endpoint.

Kali Linux was used to generate multiple SMB login attempts against a Windows 11 machine. Splunk was used to collect and analyze the related logs and alerts.

The investigation follows the activity from failed login attempts to a successful login and later persistence activity.

I used Splunk, Windows Security logs, Sysmon, and PowerShell logs to investigate the incident and create a simple timeline.

## Lab Environment

- **Kali Linux** - used to generate SMB login attempts
- **Windows 11 (SOC-WIN11)** - monitored endpoint
- **Splunk** - used for log collection, searching, alerts, and investigation
- **Splunk Universal Forwarder** - forwards Windows logs to Splunk
- **Sysmon** - detailed endpoint activity
- **PowerShell Script Block Logging** - used to review executed PowerShell code
- **Isolated VMware network** - used to keep the lab separated from the rest of the network

## Logs Used

During the investigation, I used the following Windows and Sysmon events:

- **Event ID 4625** - Failed logon
- **Event ID 4624** - Successful logon
- **Sysmon Event ID 1** - Process creation
- **PowerShell Event ID 4104** - Script Block Logging

## Detection and Alerts

The following alerts were triggered during the investigation:

- **Multiple Failed Logons** - detected repeated failed login attempts for the user mnovak
- **Suspicious Run Key Persistence** - detected the creation of a Registry Run key used for persistence

![Triggered Alerts](images/triggered-alerts.png)

## Scenario

Multiple SMB login attempts were generated from Kali Linux against the Windows 11 endpoint.

Splunk was used to monitor the authentication activity and detect suspicious logon attempts.

## Initial Alert

Splunk triggered a `Multiple Failed Logons` alert.

The alert showed:

- User: `mnovak`
- 39 failed logon attempts
- Logon Type 3
- Source IP: `192.168.64.20`
- Host: `SOC-WIN11`

![Multiple Failed Logons](screenshots/multiple-failed-logons.png)
