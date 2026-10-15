# Day 3 — Windows Authentication Investigation Report

## 1. Investigation Overview

**Objective:** Analyze Windows authentication events to identify patterns that may indicate suspicious login activity.

**Tool:** Windows Event Viewer  
**Log Source:** Windows Logs → Security  
**Events Reviewed:** 4625 (Failed Logon), 4624 (Successful Logon)

## 2. Observed Evidence

During the lab, approximately 3–5 failed logon events were observed, followed by a successful logon.

One examined failed logon contained the following details:

| Field | Value |
|---|---|
| Event ID | 4625 |
| TargetUserName | ASUS |
| Logon Type | 2 |
| Source Network Address | 127.0.0.1 |
| Status | `0xC000006D` |
| SubStatus | `0xC000006A` |

## 3. Evidence Interpretation

### Event ID 4625

The event records an unsuccessful authentication attempt.

- The target account shown was `ASUS`.
- Logon Type 2 indicates an interactive logon.
- `127.0.0.1` is the local loopback address.
- Status `0xC000006D` represents a general logon failure.
- SubStatus `0xC000006A` indicates an incorrect password.

### Event ID 4624

A successful logon was observed after the failed attempts.

The successful event must be examined independently to verify its account, timestamp, logon type, and source address. The available findings alone do not establish that the same source generated every event.

## 4. Timeline Summary

| Sequence | Event | Observation |
|---|---|---|
| 1 | 4625 | Failed authentication |
| 2 | 4625 | Additional failed authentication |
| 3 | 4625 | Additional failed authentication |
| 4 | 4625 | Additional failed authentication |
| 5 | 4624 | Successful authentication observed afterward |

**Note:** Exact timestamps were not recorded in this summary. Use the timestamps displayed in your actual Windows logs if adding a precise timeline.

## 5. SOC Assessment

**Assessment: Further investigation required.**

Repeated failed logons followed by a successful logon may reflect legitimate password-entry mistakes or potentially suspicious activity.

The observed events do not independently confirm a brute-force attack or account compromise.

## 6. Recommended Investigation Steps

1. Compare the timestamps of the failed and successful logons.
2. Verify whether the account names match.
3. Compare logon types and source network addresses.
4. Review the successful logon details and authentication package.
5. Check for unusual account changes, privilege assignments, or other suspicious activity around the same period.
6. Validate the activity with the account owner or authorized IT team when appropriate.
7. Preserve relevant logs and escalate according to the organization's incident-response procedure if evidence indicates potential compromise.

## 7. Conclusion

This investigation demonstrated how Windows Security Logs can be used to review failed and successful authentication events.

The main lesson is to correlate evidence and investigate context before deciding whether activity represents a security incident.

## 8. Evidence Files

Expected screenshots in this directory:

- `Screenshots/event-4625-failed-logon.png`
- `Screenshots/event-4625-details.png`
- `Screenshots/event-4624-successful-logon.png`

Upload the actual screenshots before treating the evidence checklist as complete.
