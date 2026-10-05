
# Day 2 — Windows Authentication & Event Logs

## 🎯 Objective

Understand how Windows records authentication activity and learn how a SOC Analyst investigates successful and failed login attempts.

---

## 📚 Topics Covered

- Windows Event Viewer
- Windows Security Logs
- Event ID 4624 — Successful Logon
- Event ID 4625 — Failed Logon
- Windows Logon Types
- Logon Type 2 — Interactive
- Logon Type 3 — Network
- Logon Type 10 — RemoteInteractive / RDP
- Authentication failure reasons
- Source IP and workstation information
- Process information
- Basic process legitimacy investigation
- Authentication timeline analysis

---

## 🧪 Practical Lab

A controlled authentication test was performed on a Windows system.

### Test

1. Generated an intentional failed login.
2. Successfully logged in afterward.
3. Investigated Event ID 4625.
4. Investigated Event ID 4624.
5. Compared the authentication events.
6. Analyzed the account, logon type, source address and process information.
7. Built a basic authentication timeline.

---

## 🔎 Events Observed

| Event ID | Meaning |
|----------|---------|
| 4625 | Failed Logon |
| 4624 | Successful Logon |

### Authentication Timeline

```text
18:03:10 → 4625 → Failed Logon
18:03:14 → 4624 → Successful Logon
