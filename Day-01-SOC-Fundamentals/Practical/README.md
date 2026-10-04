# Day 01 Practical — Windows Authentication Investigation

## Objective

Investigate Windows authentication activity using Windows Event Viewer.

## Environment

- Operating System: Windows
- Tool: Windows Event Viewer
- Log Source: Windows Security Log

## Practical Scenario

A user attempts to log in to a Windows system.

The SOC analyst needs to determine whether the authentication
activity is normal or potentially suspicious.

## Lab Procedure

1. Open Windows Event Viewer.
2. Navigate to Windows Logs → Security.
3. Generate a controlled failed login attempt.
4. Identify Event ID 4625.
5. Successfully log in.
6. Identify Event ID 4624.
7. Examine the event details.
8. Build an authentication timeline.

## Important Events

### Event ID 4625

Indicates a failed Windows logon attempt.

### Event ID 4624

Indicates a successful Windows logon.

## Investigation Questions

During the investigation, check:

- Username
- Timestamp
- Logon Type
- Source information
- Authentication details
- Number of failed attempts
- Successful login after failed attempts
- Related security events

## Evidence

Screenshots from the practical will be stored in:

`Screenshots/`

## Investigation Results

Results will be added after completing the practical lab.

## Status

🟡 Practical In Progress
