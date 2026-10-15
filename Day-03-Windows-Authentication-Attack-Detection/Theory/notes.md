# Day 3 — Windows Authentication Attack Detection

## 1. Introduction

Windows authentication logs help SOC Analysts investigate login activity, identify suspicious patterns, and determine whether further investigation is necessary.

The primary tool used in this practical is Windows Event Viewer.

Path: `Event Viewer → Windows Logs → Security`

## 2. Important Windows Event IDs

| Event ID | Description |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4672 | Special privileges assigned to a new logon |
| 4720 | User account created |
| 4726 | User account deleted |
| 4732 | Member added to a security-enabled local group |
| 1102 | Security audit log cleared |

These events provide useful evidence, but their presence alone does not prove malicious activity.

## 3. Event ID 4625 — Failed Logon

Event ID 4625 is generated when a logon attempt fails.

Important fields:
- TargetUserName: Account associated with the failed attempt.
- LogonType: Type of logon attempted.
- IpAddress: Source network address, if recorded.
- Status: General authentication failure status.
- SubStatus: More specific failure information, when available.
- TimeCreated: Timestamp of the event.

### Common status codes

| Code | Meaning |
|---|---|
| `0xC000006D` | General logon failure |
| `0xC000006A` | Incorrect password |
| `0xC0000064` | User name does not exist |

The interpretation of a failure should be based on the complete event and its fields.

## 4. Event ID 4624 — Successful Logon

Event ID 4624 records a successful logon.

Important fields:
- Account Name
- Logon Type
- Logon ID
- Source Network Address, when available
- Authentication Package
- Timestamp

A successful login following failed attempts deserves review when the timing, source, account, or surrounding activity is unusual.

## 5. Common Logon Types

| Type | Meaning |
|---|---|
| 2 | Interactive logon, typically at the local computer |
| 3 | Network logon |
| 4 | Batch logon |
| 5 | Service logon |
| 7 | Workstation unlock |
| 10 | RemoteInteractive, commonly Remote Desktop |
| 11 | CachedInteractive |

Logon Type 2 generally indicates interactive authentication. It does not, by itself, prove who physically initiated the attempt.

## 6. Authentication Attack Types

### Brute-force attack
Repeated password guesses against an account.

### Password spraying
Trying a small number of commonly used passwords across multiple accounts.

### Credential stuffing
Testing previously exposed username/password combinations against another service.

### Important distinction
Repeated failed logons can also result from mistyped passwords, stale saved credentials, automated services, or other legitimate activity.

No universal count of failed logons proves an attack. Analysts must consider the time window, source, accounts targeted, environment, and successful logons.

## 7. Understanding the Loopback Address

`127.0.0.1` is an IPv4 loopback address. It refers to the local machine.

When this address appears in a log, do not interpret it as an external attacker's public IP address. Review the event context and related telemetry.

## 8. SOC Investigation Methodology

1. Identify relevant failed and successful logon events.
2. Compare timestamps and affected accounts.
3. Review logon types and source addresses.
4. Examine status and substatus codes.
5. Correlate nearby authentication events.
6. Check for suspicious activity after successful authentication.
7. Document the evidence and state the confidence of the assessment.
8. Escalate according to the organization's incident-response procedure when warranted.

## 9. Key Takeaways

- Event ID 4625 means failed logon.
- Event ID 4624 means successful logon.
- A successful login after failures does not automatically mean an account was compromised.
- A single failed login does not prove brute force.
- Source address, account, timestamps, logon type, and surrounding activity help establish context.
- Good SOC analysis separates observed facts from hypotheses.

## 10. Conclusion

Windows authentication events are valuable sources of evidence during security investigations. Accurate conclusions require event correlation, contextual analysis, and clear documentation rather than assumptions based on a single event.
