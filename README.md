# Wazuh SIEM Home Lab: Windows Endpoint Monitoring

A hands-on blue-team home lab built to practice endpoint monitoring,
file integrity monitoring (FIM), and basic SOC alert validation using
Wazuh.

## Project overview

This lab uses an Ubuntu virtual machine as the Wazuh manager and a
Windows 11 host as the monitored endpoint. The Windows Wazuh agent sends
telemetry to the manager, where alerts can be reviewed in the Wazuh
dashboard.

## Lab architecture

  -----------------------------------------------------------------------
  Component                           Role
  ----------------------------------- -----------------------------------
  Ubuntu 22.04 LTS VM                 Wazuh manager, Wazuh indexer, and
                                      Wazuh dashboard

  Windows 11 host                     Monitored endpoint running the
                                      Wazuh agent

  Oracle VirtualBox                   Hosts the Ubuntu virtual machine

  Network mode                        Bridged networking for
                                      endpoint-to-manager communication
  -----------------------------------------------------------------------

**Data flow:** Windows 11 endpoint → Wazuh agent → Ubuntu Wazuh manager
→ Wazuh dashboard.

> IP addresses are intentionally not published. The manager's bridged
> address may change depending on the local network.

## What I implemented

-   Deployed the Wazuh manager, indexer, and dashboard on Ubuntu 22.04
    LTS.
-   Installed the Wazuh agent on the Windows 11 host.
-   Registered the Windows endpoint with the Wazuh manager and confirmed
    it appeared in the Wazuh environment.
-   Configured Windows File Integrity Monitoring for the test directory
    `C:\Wazuh-Lab`.
-   Generated test activity by creating files, editing file contents,
    and deleting files in the monitored directory.
-   Reviewed the resulting alerts in the Wazuh dashboard and verified
    events for:
    -   File added to the system (rule ID `554`)
    -   File deleted (rule ID `553`)
    -   Integrity checksum changed (rule ID `550`)

## Validation performed

1.  Created a test file inside `C:\Wazuh-Lab`.
2.  Added and changed text in the file.
3.  Deleted the file.
4.  Repeated the test with additional files.
5.  Opened the Wazuh dashboard and reviewed the corresponding endpoint
    events.

The dashboard showed file-addition, file-deletion, and checksum-change
alerts associated with the Windows endpoint.

## Skills demonstrated

-   SIEM deployment and basic administration
-   Windows endpoint onboarding
-   Agent-to-manager connectivity
-   File Integrity Monitoring (FIM)
-   Basic alert validation and dashboard investigation
-   Linux virtual-machine administration
-   Basic understanding of security telemetry and event review

## Repository structure

``` text
wazuh-soc-home-lab/
├── README.md
├── .gitignore
├── docs/
│   └── architecture.md
└── evidence/
    └── README.md
```

Screenshots can be added to `evidence/` after removing or obscuring
passwords, tokens, private IP addresses, usernames, and other sensitive
information.

## Security and privacy

This repository deliberately does not contain:

-   Wazuh admin passwords or generated credentials
-   Agent authentication keys
-   Private keys, certificates, or keystores
-   Unredacted configuration files
-   Raw logs containing personal or sensitive system information

Do not commit secrets or credentials. If a credential has appeared in a
screenshot or chat, rotate it before publishing the project.

## Future improvements

Potential extensions include Windows Security Event Log monitoring,
PowerShell telemetry, additional detection scenarios, and documented
incident investigations. These should be added only after they have been
implemented and tested.
