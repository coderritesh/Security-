
# Day 01 — Windows Authentication Investigation

## 1. Objective

Investigate Windows authentication events using Windows Event Viewer
and understand how failed and successful logons are recorded.

## 2. Environment

- Operating System: Windows
- Tool: Windows Event Viewer
- Log Source: Windows Security Log

## 3. Test Activity

A controlled authentication test was performed on the Windows system.

The test included:

1. Entering an incorrect password.
2. Observing the failed authentication event.
3. Entering the correct password.
4. Observing the successful authentication event.

## 4. Observed Events

### Event ID 4625 — Failed Logon

Event ID 4625 indicates that an account failed to log on.

Observed timestamp:

`12:50:36`

The event was recorded in:

`Windows Logs → Security`

The event showed:

- Event ID: 4625
- Task Category: Logon
- Keywords: Audit Failure

### Event ID 4624 — Successful Logon

Event ID 4624 indicates that an account successfully logged on.

Observed timestamp:

`12:50:41`

The event was recorded in:

`Windows Logs → Security`

The event showed:

- Event ID: 4624
- Task Category: Logon
- Keywords: Audit Success

## 5. Authentication Timeline

```text
12:50:36
    ↓
Event ID 4625
Failed Logon
    ↓
12:50:41
    ↓
Event ID 4624
Successful Logon
