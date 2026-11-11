Wazuh File Integrity Monitoring (FIM) Test

Date: November 11, 2026

Objective

Configure and test Wazuh File Integrity Monitoring to detect file creation, modification, and deletion on a Windows 11 endpoint.

Lab Environment

Wazuh Manager: Ubuntu 22.04 Virtual Machine

Endpoint: Windows 11 Host

SIEM: Wazuh

Agent: Wazuh Windows Agent

Monitored Directory: C:\Wazuh-Lab

Configuration

Configured the Wazuh Windows agent to monitor C:\Wazuh-Lab using:

check_all="yes"

report_changes="yes"

realtime="yes"

Testing Performed

Created a text file.

Modified the file contents.

Deleted the file.

Results

Wazuh successfully detected the file operations and generated these alerts:

Wazuh Rule ID

Description

554

File added to the system

550

Integrity checksum changed

553

File deleted

All three alert types were visible in Wazuh Threat Hunting and associated with the Windows 11 agent.

Skills Practised

Wazuh agent deployment and registration

File Integrity Monitoring configuration

Windows endpoint monitoring

SIEM alert investigation

Security event analysis

Conclusion

Successfully configured and validated real-time File Integrity Monitoring using Wazuh. The lab demonstrated detection of file creation, modification, and deletion activities on a monitored Windows endpoint.
