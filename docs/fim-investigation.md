# Investigation 01: File Integrity Monitoring (FIM)

## 1. Objective

To configure and validate Wazuh File Integrity Monitoring on a Windows 11 endpoint by monitoring file creation, modification, and deletion activities.

## 2. Environment

- SIEM: Wazuh 4.14.10
- SIEM Server: Ubuntu 22.04 LTS
- Endpoint: Windows 11
- Endpoint Agent: Wazuh Windows Agent
- Monitored Directory: `C:\Wazuh-Lab`

## 3. Testing Methodology

Controlled file-system activities were performed on the monitored Windows endpoint:

1. Created a test file inside the monitored directory.
2. Modified the file contents.
3. Deleted the test file.
4. Reviewed the corresponding events in the Wazuh Dashboard.

## 4. Detection Results

The following Wazuh FIM events were observed:

| Rule ID | Description |
|---|---|
| 554 | File added |
| 550 | File modified |
| 553 | File deleted |

These events demonstrated that Wazuh was collecting and identifying the tested file-system changes.

## 5. Investigation Findings

The Wazuh Dashboard displayed events corresponding to the controlled file activities.

The observed rule IDs provided visibility into file additions, modifications, and deletions.

## 6. Conclusion

File Integrity Monitoring was successfully tested on the Windows endpoint.

The investigation demonstrated how Wazuh can monitor file-system changes and provide security telemetry that can assist SOC analysts in identifying potentially unauthorized modifications.

## 7. Evidence

Screenshots are organized under:

`evidence/02-File-Integrity-Monitoring/`

Note: Original FIM screenshots are not currently included in the repository.
