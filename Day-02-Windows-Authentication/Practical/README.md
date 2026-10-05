
# Day 2 — Windows Authentication Practical

## Objective

The objective of this practical was to understand how Windows records user authentication activities in the Security Event Log.

I performed a controlled authentication test by intentionally entering an incorrect password and then logging in with the correct password.

The generated events were investigated using Windows Event Viewer.

---

## Environment

- Operating System: Windows
- Tool: Windows Event Viewer
- Log Source: Windows Security Log
- Lab Type: Local/Controlled Lab

---

## Practical Scenario

The following authentication sequence was performed:

```text
Incorrect Password
        ↓
Event ID 4625
Failed Logon
        ↓
Correct Password
        ↓
Event ID 4624
Successful Logon
