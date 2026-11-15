# Lab Architecture

## Components

- **Ubuntu 22.04 LTS virtual machine:** Hosts the Wazuh Manager, Indexer and Dashboard.
- **Windows 11 host:** Runs the Wazuh Agent and acts as the monitored endpoint.
- **VirtualBox:** Provides the Ubuntu virtual-machine environment.
- **Host-Only networking:** Provides communication between the Windows host and Ubuntu VM.
- **NAT networking:** Provides the Ubuntu VM with external network connectivity.

## Network Configuration

| System | Network Interface | IP Address |
|---|---|---|
| Ubuntu VM | Host-Only | `192.168.56.10` |
| Windows host | Host-Only | `192.168.56.1` |
| Ubuntu VM | NAT | `10.0.2.15` |

## Telemetry Path

1. The Windows Wazuh Agent collects endpoint telemetry.
2. The agent forwards events to the Wazuh Manager.
3. Wazuh processes the events and makes alerts and collected data available through the dashboard.
4. The analyst reviews endpoint events and investigation details.

## File Integrity Monitoring

The Windows Agent was configured to monitor:

`C:\Wazuh-Lab`

Controlled test files were created, modified and deleted. The Wazuh Dashboard displayed corresponding file-addition, file-deletion and checksum-change events.

## Sysmon Integration

Microsoft Sysmon was installed on Windows 11.

The Wazuh Agent collects events from:

`Microsoft-Windows-Sysmon/Operational`

Process creation (Event ID 1) and process termination (Event ID 5) were investigated through Wazuh Discover.

## Windows Authentication Monitoring

Windows Security events were collected and investigated:

- Event ID 4624: Successful logon.
- Event ID 4625: Failed logon.

Controlled authentication testing was used to validate failed-logon event collection.# Lab Architecture

## Components

- **Ubuntu 22.04 LTS virtual machine:** Hosts the Wazuh Manager, Indexer and Dashboard.
- **Windows 11 host:** Runs the Wazuh Agent and acts as the monitored endpoint.
- **VirtualBox:** Provides the Ubuntu virtual-machine environment.
- **Host-Only networking:** Provides communication between the Windows host and Ubuntu VM.
- **NAT networking:** Provides the Ubuntu VM with external network connectivity.

## Network Configuration

| System | Network Interface | IP Address |
|---|---|---|
| Ubuntu VM | Host-Only | `192.168.56.10` |
| Windows host | Host-Only | `192.168.56.1` |
| Ubuntu VM | NAT | `10.0.2.15` |

## Telemetry Path

1. The Windows Wazuh Agent collects endpoint telemetry.
2. The agent forwards events to the Wazuh Manager.
3. Wazuh processes the events and makes alerts and collected data available through the dashboard.
4. The analyst reviews endpoint events and investigation details.

## File Integrity Monitoring

The Windows Agent was configured to monitor:

`C:\Wazuh-Lab`

Controlled test files were created, modified and deleted. The Wazuh Dashboard displayed corresponding file-addition, file-deletion and checksum-change events.

## Sysmon Integration

Microsoft Sysmon was installed on Windows 11.

The Wazuh Agent collects events from:

`Microsoft-Windows-Sysmon/Operational`

Process creation (Event ID 1) and process termination (Event ID 5) were investigated through Wazuh Discover.

## Windows Authentication Monitoring

Windows Security events were collected and investigated:

- Event ID 4624: Successful logon.
- Event ID 4625: Failed logon.

Controlled authentication testing was used to validate failed-logon event collection.
