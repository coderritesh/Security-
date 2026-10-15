# Day 3 — Windows Authentication Attack Detection

## Objective
Learn how to investigate failed and successful Windows authentication events and identify patterns that may indicate suspicious login activity.

## Topics Covered
- Event ID 4625 — Failed Logon
- Event ID 4624 — Successful Logon
- Logon Types
- Source Network Address
- Status and SubStatus codes
- Brute-force attacks
- Password spraying
- Credential stuffing
- Authentication event correlation

## Tools Used
- Windows Event Viewer
- Windows Security Logs

## Practical Work
1. Opened Event Viewer.
2. Navigated to Windows Logs → Security.
3. Filtered for Event IDs 4624 and 4625.
4. Inspected failed logon event details.
5. Examined account name, logon type, source address, status, and substatus.
6. Compared failed logons with a subsequent successful logon.

## Findings
- Observed approximately 3–5 failed logon events in the reviewed period.
- Observed a successful logon after the failed attempts.
- Examined a failed logon targeting account `ASUS`.
- Observed Logon Type 2 and Source Network Address `127.0.0.1` in that failed event.
- Status `0xC000006D` indicated a general logon failure.
- SubStatus `0xC000006A` indicated an incorrect password.

## SOC Analysis
Multiple failed logons followed by a successful logon can be suspicious, but these events alone do not confirm a brute-force attack or account compromise.

A proper investigation should correlate timestamps, account names, logon types, source addresses, and subsequent activity. The successful logon's details must be checked independently before linking it to the same source or session.

## Key Learning
**Do not jump to conclusions. Correlate authentication events and investigate the evidence before classifying an incident.**

## Conclusion
This practical improved my understanding of Windows authentication monitoring and the initial investigation of potentially suspicious login patterns.

## Evidence
Screenshots and a detailed investigation report will be maintained in the `Practical` directory.
