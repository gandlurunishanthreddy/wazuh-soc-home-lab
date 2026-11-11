# Lab Architecture

## Components

-   **Ubuntu 22.04 LTS virtual machine:** hosts the Wazuh manager,
    indexer, and dashboard.
-   **Windows 11 host:** runs the Wazuh agent and acts as the monitored
    endpoint.
-   **VirtualBox:** provides the Ubuntu virtual-machine environment.
-   **Bridged networking:** allows the Windows endpoint and Ubuntu
    manager to communicate on the local network.

## Telemetry path

1.  The Windows Wazuh agent collects endpoint telemetry.
2.  The agent forwards events to the Wazuh manager.
3.  Wazuh processes the events and makes alerts available in the
    dashboard.
4.  The analyst reviews the endpoint and alert details in the dashboard.

## File Integrity Monitoring test

The Windows agent was configured to monitor `C:\Wazuh-Lab`. Test files
were created, modified, and deleted. The Wazuh dashboard showed the
corresponding file-addition, file-deletion, and checksum-change events.

No fixed IP address is documented because bridged addresses can change
when the local network changes.
