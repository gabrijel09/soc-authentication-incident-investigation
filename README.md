# SOC Authentication Incident Investigation

## Overview

This project is a small SOC investigation lab focused on suspicious authentication activity in a Windows environment.

The scenario uses Kali Linux to generate multiple SMB login attempts against a Windows 11 endpoint. Splunk is used to collect and analyze the related Windows security logs and alerts.

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
