# Day 1 — SOC Fundamentals

## Objective

Understand the fundamentals of a Security Operations Center (SOC),
SOC Analyst responsibilities, security events, alerts, incidents,
and basic Windows security log investigation.

## Topics Covered

- What is a SOC?
- SOC Analyst responsibilities
- Security events
- Security alerts
- Security incidents
- Event vs Alert vs Incident
- Security logs
- Basic SOC investigation methodology
- Windows Event Viewer
- Windows Security Event IDs

## Tools Used

- Windows Event Viewer
- Windows Security Logs

## Practical Lab

Performed a controlled authentication test on a Windows system.

1. Generated failed login attempts intentionally.
2. Investigated the Windows Security logs.
3. Identified Event ID 4625.
4. Successfully logged in.
5. Identified Event ID 4624.
6. Built a basic authentication timeline.

## Important Event IDs

| Event ID | Description |
|----------|-------------|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4672 | Special privileges assigned to new logon |

## Investigation Mindset

During investigation, I focused on:

- WHO performed the action?
- WHEN did it happen?
- WHAT happened?
- WHERE did it originate?
- WHAT happened next?

## Key Learning

Logs provide valuable evidence during security investigations.

A single failed login does not automatically indicate an attack.
SOC analysts need to analyze patterns, context, source information,
and related events before determining whether activity is malicious.

## Conclusion

Day 1 provided a foundation for understanding SOC operations and
introduced Windows Security Logs as a source of investigation evidence.
