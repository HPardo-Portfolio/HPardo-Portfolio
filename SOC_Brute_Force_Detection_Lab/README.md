# SOC Lab – Brute Force Detection & Response

## Objective
Simulate and detect a brute force attack using Windows Event Logs, Sysmon, and Splunk SIEM.

---

## Lab Environment
- Windows 11 (Target)
- Kali Linux (Attacker simulation)
- Splunk Enterprise (SIEM)
- Sysmon (Endpoint telemetry)

---

## Attack Simulation
Multiple failed login attempts were generated against a Windows user account (soclab), triggering Event ID 4625.

---

## Detection

### Event Viewer
- Log: Security
- Event ID: 4625
- Result: Multiple failed login attempts (Audit Failure)

### Splunk Query
```
index=main EventCode=4625
```

---

## Analysis
- Repeated authentication failures detected
- Target account: soclab
- Source: Localhost (127.0.0.1)
- Pattern consistent with brute force attack

---

## MITRE ATT&CK Mapping
- T1110 – Brute Force

---

## Impact
- Account locked due to multiple failed login attempts

---

## Response & Remediation
- Accessed system via Safe Mode
- Re-enabled account:
```
net user soclab /active:yes
```
- Reset password
- Disabled lockout threshold:
```
net accounts /lockoutthreshold:0
```

---

## Screenshots

![Lab Setup](lab01_01_setup.png)
![Sysmon Logs](lab01_02_eventviewer_sysmon.png)
![Brute Force Attempts](lab01_03_eventviewer_bruteforce_attempt.png)
![Splunk Ready](lab01_04_splunk_ready.png)
![Splunk Detection](lab01_05_splunk_detection.png)
![Splunk Event Details](lab01_06_splunk_event_details.png)
![Account Lockout](lab01_07_account_lockout.png)
![Safe Mode Recovery](lab01_08_safe_mode_recovery.png)
![Account Unlock Command](lab01_09_account_unlock_cmd.png)

---

## Skills Demonstrated
- Log analysis (Windows Event Logs)
- SIEM investigation (Splunk)
- Threat detection
- Incident response
- MITRE ATT&CK mapping

---

## Summary
This lab demonstrates the detection and response to a brute force attack using real-world SOC workflows, including log analysis, SIEM correlation, and system remediation.
