# Wazuh SOC Lab – Detection and Event Analysis

## Overview

This lab demonstrates a hands-on SOC workflow using Wazuh and Sysmon to monitor and analyze activity on a Windows endpoint.

The goal of this lab was to deploy an endpoint agent, generate telemetry, simulate attacker behavior, and validate that meaningful security events could be detected and investigated through the platform.

---

## Objective

Build and validate a SOC monitoring environment by deploying Wazuh and Sysmon on a Windows endpoint, generating activity, and analyzing resulting security events.

---

### Wazuh Agent Deployment

The Wazuh agent was installed on the Windows endpoint using PowerShell.

![Wazuh Agent Deployment UI](screenshots/01_installation/Lab01_01_Wazuh_Agent_Deploy_UI.png)

The installation command was generated directly from the Wazuh dashboard and executed on the system.

![Agent Install Command](screenshots/01_installation/Lab01_02_Agent_Install_Command.png)

After installation, the agent service was started and verified to be running.

![Agent Installation PowerShell](screenshots/01_installation/Lab01_03_Agent_Installation_PowerShell.png)

---

### Agent Connectivity

Once installed, the agent successfully connected to the Wazuh manager.

![Agent Service Connection](screenshots/02_network_setup/Lab01_01_Agent_Service_Connection.png)

The endpoint appeared as active in the Wazuh dashboard, confirming proper communication between the agent and the manager.

![Agent Visible in Wazuh](screenshots/02_network_setup/Lab01_02_Agent_Visible_in_Wazuh.png)

---

### Wazuh Dashboard

The Wazuh dashboard provides centralized visibility into agent status and security activity across the environment.

![Agent Active Status](screenshots/03_dashboard/Lab01_01_Agent_Active_Status.png)

This view highlights alerts and system activity, allowing for quick identification of potential issues.

![Security Dashboard Overview](screenshots/03_dashboard/Lab01_02_Security_Dashboard_Overview.png)

---

### Sysmon Configuration

Sysmon was configured to collect detailed endpoint telemetry, including process creation and file activity.

![Sysmon Config Added](screenshots/04_detection/01_sysmon_setup/Lab01_01_Sysmon_Config_Added.png)

The configuration was applied successfully, and the Sysmon service was verified to be running.

![Sysmon Config Applied](screenshots/04_detection/01_sysmon_setup/Lab01_02_Sysmon_Config_Apply.png)

![Sysmon Service Running](screenshots/04_detection/01_sysmon_setup/Lab01_03_Sysmon_Service_Running.png)

---

### Command Execution Simulation

PowerShell commands were executed on the endpoint to simulate common attacker behavior.

![PowerShell Command Execution](screenshots/04_detection/02_command_execution/Lab01_04_Powershell_Command_Execution.png)

---

### Wazuh Detection

The simulated activity was successfully captured and correlated within Wazuh.

![Wazuh Security Events](screenshots/04_detection/03_wazuh_detection/Lab01_05_Wazuh_Security_Events.png)

---

### Event Analysis

Alerts were reviewed to understand the actions performed on the system and the context around them.

![Whoami Event Details](screenshots/04_detection/04_event_analysis/Lab01_06_Powershell_Whoami_Event_Details.png)

![Get-Process Event Details](screenshots/04_detection/04_event_analysis/Lab01_07_Powershell_GetProcess_Event_Details.png)

These logs provide visibility into executed commands, associated processes, and user context.

---

### Attack Simulation

A controlled simulation was performed to replicate common attacker behavior and validate detection across different stages.

#### Network Reconnaissance

An Nmap scan was executed from a Kali Linux machine to simulate the reconnaissance phase.

![Nmap Scan](screenshots/05_attack_simulation/Nmap_Scan_From_Kali.png)

#### Suspicious File Creation

A file was created in a temporary directory to simulate potentially malicious activity.

![File Creation Command](screenshots/05_attack_simulation/Suspicious_File_Creation_Command.png)

#### Detection in Wazuh

The activity was successfully detected and logged within Wazuh.

![File Detected](screenshots/05_attack_simulation/Suspicious_File_Detected_Wazuh.png)

![Detection Details](screenshots/05_attack_simulation/Suspicious_File_Detected_Wazuh_Details.png)

![Wazuh Alerts](screenshots/05_attack_simulation/Wazuh_Alerts_From_Attack.png)

![Critical Alerts](screenshots/05_attack_simulation/Critical_Alerts_Sysmon_Wazuh.png)

---

## What This Demonstrates

- Deployment and configuration of endpoint monitoring tools (Wazuh, Sysmon)
- Ability to generate and analyze security-relevant events
- Understanding of SOC workflows, including detection and investigation
- Experience working with SIEM-based visibility and alert correlation

---

## Conclusion

This lab demonstrates how combining Wazuh and Sysmon provides strong visibility into endpoint activity and supports effective detection of potentially malicious behavior.

It also reinforces key SOC concepts such as centralized logging, event correlation, and alert analysis.

This environment serves as a foundation for more advanced scenarios, including privilege escalation, lateral movement, and persistence, which will be explored in future labs.
