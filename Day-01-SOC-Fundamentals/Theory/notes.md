# SOC Fundamentals — Theory

## 1. What is SOC?

SOC stands for Security Operations Center.

A Security Operations Center monitors an organization's IT environment
for security threats and suspicious activity.

## 2. What does a SOC Analyst do?

A SOC Analyst:

- Monitors security alerts
- Analyzes logs
- Investigates suspicious activity
- Identifies potential threats
- Escalates security incidents
- Assists with incident response
- Documents investigations

## 3. What is an Event?

An event is an activity recorded by a system, application,
network device, or security tool.

Example:

A user successfully logs into Windows.

## 4. What is an Alert?

An alert is generated when a security tool identifies
potentially suspicious activity.

Example:

Multiple failed login attempts from the same source.

## 5. What is an Incident?

An incident is a confirmed or suspected security problem
that requires investigation or response.

## Event → Alert → Investigation → Incident → Response

Not every event is an alert.

Not every alert is an incident.

## 6. What are Security Logs?

Security logs contain records of activities occurring
within systems, applications, and security infrastructure.

SOC analysts use logs as evidence during investigations.

## 7. Important Windows Event IDs

| Event ID | Meaning |
|---|---|
| 4624 | Successful Logon |
| 4625 | Failed Logon |
| 4672 | Special Privileges Assigned |

## 8. Basic SOC Investigation

A SOC Analyst should ask:

### WHO?
Which user or account performed the activity?

### WHEN?
When did the activity happen?

### WHAT?
What activity occurred?

### WHERE FROM?
Where did the activity originate?

### WHAT NEXT?
What happened after the activity?
