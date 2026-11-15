# Investigation 02: Windows Process Monitoring Using Sysmon

## 1. Objective

To integrate Microsoft Sysmon with Wazuh and investigate Windows process creation and termination events.

## 2. Environment

- Windows 11 endpoint
- Ubuntu 22.04 Wazuh server
- Wazuh 4.14.10
- Microsoft Sysmon 15.22
- Wazuh Windows Agent

## 3. Sysmon Integration

Installed Sysmon on the Windows endpoint and configured the Wazuh Agent to collect events from:

`Microsoft-Windows-Sysmon/Operational`

The collected events were searchable through Wazuh Discover using the `wazuh-archives-*` index pattern.

## 4. Events Investigated

| Event ID | Description |
|---|---|
| 1 | Process creation |
| 5 | Process termination |

## 5. Investigation Activities

Performed controlled process execution tests and examined the resulting telemetry.

Investigated:

- PowerShell process execution.
- Notepad process creation.
- Executable paths.
- User context.
- Process IDs and parent process IDs.
- Parent-child process relationships.

A Notepad process launched by PowerShell was identified during controlled testing.

## 6. Findings

Sysmon successfully generated process telemetry, which was collected by Wazuh.

The investigation demonstrated how process information and parent-child relationships can help analysts understand application execution.

The reviewed activity was consistent with the controlled testing performed. No confirmed malicious execution was established.

## 7. PowerShell Monitoring Limitation

PowerShell process creation was investigated using Sysmon Event ID 1.

PowerShell Script Block Logging (Event ID 4104) was not configured or verified during this project.

Therefore, the investigation focused on process-level telemetry rather than detailed PowerShell script-content monitoring.

## 8. Conclusion

The integration of Sysmon with Wazuh provided additional visibility into Windows process activity.

This investigation demonstrated foundational endpoint monitoring and process analysis techniques relevant to SOC operations.

## 9. Evidence

Screenshots are available under:

`evidence/03-Sysmon-Investigations/`
