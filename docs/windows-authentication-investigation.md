# Investigation 03: Windows Authentication Monitoring

## 1. Objective

To monitor and investigate successful and failed Windows authentication events using Wazuh.

## 2. Environment

- Windows 11 endpoint
- Ubuntu 22.04 Wazuh server
- Wazuh 4.14.10
- Wazuh Windows Agent
- Windows Security Event Log

## 3. Events Investigated

| Event ID | Description |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |

## 4. Testing Methodology

Performed controlled authentication testing on the Windows endpoint, including entering an incorrect password.

Collected and reviewed the resulting Windows Security events through Wazuh Discover.

## 5. Investigation Findings

Three failed logon events (Event ID 4625) were observed during the controlled test.

The investigated events contained the following details:

| Field | Observed value |
|---|---|
| Target username | SRIJU |
| Source IP | 127.0.0.1 |
| Logon Type | 2 (Interactive) |
| Authentication Package | Negotiate |
| Failure Status | 0xc000006d |
| Failure Substatus | 0xc000006a |

The failure substatus was consistent with an incorrect password.

The source address indicated that the observed authentication failures originated locally.

## 6. Security Analysis

Event ID 4625 can help analysts investigate repeated authentication failures.

When multiple failures occur within a short period, analysts can examine:

- Targeted usernames.
- Source IP addresses.
- Failure frequency.
- Logon types.
- Authentication status codes.

These details can help identify activity that warrants further investigation.

The three observed events were generated during controlled testing and do not establish a brute-force attack.

## 7. Conclusion

Wazuh successfully collected Windows authentication events and allowed investigation of failed logon activity.

This exercise demonstrated foundational authentication monitoring and Windows Security Event Log analysis relevant to SOC operations.

## 8. Evidence

Screenshots are available under:

`evidence/04-Authentication-Monitoring/`
