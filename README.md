# SOC Brute Force and Persistence Investigation

## Overview

This project is a small SOC investigation in my isolated home lab focused on suspicious login activity on a Windows endpoint.

Kali Linux was used to generate multiple SMB login attempts against a Windows 11 machine. Splunk was used to collect and analyze the related logs and alerts.

The investigation follows the activity from failed login attempts to a successful login and later persistence activity.

I used Splunk, Windows Security logs, Sysmon, and PowerShell logs to investigate the incident and create a simple timeline.

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
