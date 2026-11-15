# Wazuh SOC Analyst Home Lab: Windows Endpoint Monitoring and Investigation

## Project Overview

A hands-on blue-team home lab built to develop practical SOC Analyst skills using Wazuh SIEM, Windows endpoint monitoring, Sysmon, and File Integrity Monitoring (FIM).

The project demonstrates SIEM deployment, endpoint integration, security event collection, process investigation, and Windows authentication monitoring.

## Lab Architecture

| Component | Role |
|---|---|
| Ubuntu 22.04 LTS VM | Wazuh Manager, Indexer and Dashboard |
| Windows 11 Host | Monitored endpoint running Wazuh Agent and Sysmon |
| Oracle VirtualBox | Virtualization environment |
| Wazuh | SIEM and security event analysis |
| Microsoft Sysmon 15.22 | Detailed Windows process telemetry |
| Networking | Host-Only networking for endpoint-to-manager communication |

**Data flow:**

Windows 11 → Wazuh Agent → Ubuntu Wazuh Manager → Wazuh Indexer → Wazuh Dashboard

IP addresses and credentials are intentionally excluded from this repository.

## Technologies Used

- Wazuh 4.14.10
- Ubuntu 22.04 LTS
- Windows 11
- Microsoft Sysmon 15.22
- Oracle VirtualBox
- Windows Event Viewer
- Wazuh Dashboard and Discover

## Implemented Features

### 1. Wazuh SIEM Deployment

- Deployed Wazuh Manager, Indexer and Dashboard on Ubuntu 22.04.
- Installed and registered the Wazuh Agent on Windows 11.
- Configured agent-to-manager communication.
- Verified endpoint connectivity and active agent status through the Wazuh Dashboard.

### 2. File Integrity Monitoring (FIM)

Configured File Integrity Monitoring for the Windows test directory:

`C:\Wazuh-Lab`

Performed controlled file-system activities:

- File creation
- File modification
- File deletion

Observed Wazuh FIM rule IDs:

| Rule ID | Description |
|---|---|
| 554 | File added |
| 550 | File modified |
| 553 | File deleted |

Verified the resulting events through the Wazuh Dashboard.

### 3. Sysmon Integration and Process Monitoring

Installed Microsoft Sysmon on the Windows endpoint and configured the Wazuh Agent to collect events from:

`Microsoft-Windows-Sysmon/Operational`

Investigated the following Sysmon events:

| Event ID | Description |
|---|---|
| 1 | Process creation |
| 5 | Process termination |

Examined process telemetry, including:

- Process names and executable paths
- Process IDs and parent process IDs
- Parent-child process relationships
- User context
- Command-line information where available

### 4. Windows Process Investigation

Performed controlled process execution tests and investigated the resulting Sysmon telemetry.

Activities included:

- PowerShell process execution
- Notepad process creation
- Parent-child process relationship analysis
- Examination of executable paths and process information

Identified a Notepad process launched by PowerShell during controlled testing.

The reviewed activity was consistent with the test actions. No confirmed malicious execution was established.

### 5. PowerShell Process Monitoring

Investigated PowerShell execution through Sysmon process creation events.

Examined:

- PowerShell executable path
- User context
- Process ID
- Parent process
- Child process execution

**Limitation:** PowerShell Script Block Logging (Windows Event ID 4104) was not configured or verified during this project. The investigation focused on process-level telemetry using Sysmon Event ID 1.

### 6. Windows Authentication Monitoring

Collected and investigated Windows Security Event Log records through Wazuh.

| Event ID | Description |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |

Performed controlled authentication testing by entering an incorrect password.

Investigated the resulting failed authentication events using:

- Target username
- Source IP address
- Logon type
- Authentication package
- Failure status and substatus codes

Observed three failed logon events during the controlled test.

The events showed local interactive authentication failures consistent with the test activity.

## Investigation Findings

The project demonstrated the following:

- Successful deployment and operation of a Wazuh SIEM environment.
- Windows endpoint onboarding and telemetry collection.
- Detection of file creation, modification and deletion.
- Collection of Sysmon process creation and termination events.
- Investigation of PowerShell and Notepad process execution.
- Analysis of process relationships and user context.
- Collection and investigation of successful and failed Windows logons.

No confirmed malicious activity was established during the controlled investigations.

## Skills Demonstrated

- SIEM deployment and administration
- Wazuh configuration
- Windows endpoint monitoring
- Sysmon integration
- File Integrity Monitoring
- Windows Security Event Log analysis
- Process creation investigation
- Parent-child process analysis
- Authentication event investigation
- Linux administration
- Virtual machine networking
- Security event analysis and documentation

## Repository Structure

```text
wazuh-soc-home-lab/
│
├── README.md
│
├── docs/
│   └── architecture.md
│
└── evidence/
    └── README.md
```

Additional investigation reports and screenshots will be organized in the `docs/` and `evidence/` directories.

## Limitations and Future Improvements

- PowerShell Script Block Logging (Event ID 4104) was not verified.
- A live brute-force attack simulation was not completed.
- Custom Wazuh detection rules and automated response workflows were not implemented as part of this project.

Potential future improvements include:

- Additional authentication attack investigations.
- Custom detection-rule development.
- PowerShell Script Block Logging.
- Further endpoint threat detection scenarios.

## Security and Privacy

This repository does not contain:

- Wazuh administrator credentials.
- Agent authentication keys.
- Private keys or certificates.
- Sensitive configuration files.
- Unredacted logs containing personal information.

All testing was conducted in a controlled educational lab environment using personally managed systems.

## Conclusion

This home lab provided practical experience deploying a SIEM platform, integrating Windows endpoint telemetry, monitoring file-system changes, and investigating process and authentication events.

The project demonstrates foundational technical skills relevant to entry-level Security Operations Center (SOC) Analyst responsibilities.
