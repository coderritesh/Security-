# Day 3 — SOC Analyst Interview Questions

## Q1. What is Event ID 4625?
It records a failed logon attempt in Windows Security Logs.

## Q2. What is Event ID 4624?
It records a successful logon.

## Q3. What is a brute-force attack?
An attack in which repeated password guesses are made against an account or authentication service.

## Q4. What is password spraying?
Trying a small number of common passwords against multiple accounts.

## Q5. What is credential stuffing?
Testing username and password combinations obtained from previous data breaches against another service.

## Q6. Do multiple failed logons always indicate brute force?
No. They may result from mistyped passwords or legitimate automated activity. The analyst must correlate the events and review the context.

## Q7. What does Logon Type 2 mean?
It indicates an interactive logon, typically at the local computer.

## Q8. What does Logon Type 3 mean?
It indicates a network logon.

## Q9. What does Logon Type 10 mean?
It indicates a RemoteInteractive logon, commonly associated with Remote Desktop.

## Q10. What does 127.0.0.1 mean?
It is the IPv4 loopback address, which refers to the local machine.

## Q11. What does Status 0xC000006D mean?
It indicates a general logon failure.

## Q12. What does SubStatus 0xC000006A mean?
It indicates an incorrect password.

## Q13. What would you investigate if several 4625 events were followed by a 4624?
I would compare timestamps, account names, source addresses, logon types, and subsequent activity. I would not classify the pattern as an attack without supporting evidence.

## Q14. What if the account owner denies the successful login?
I would treat the activity as highly suspicious, preserve the evidence, investigate related events, and escalate according to the incident-response procedure.

## Q15. What is the difference between suspicious activity and a confirmed incident?
Suspicious activity requires investigation. A confirmed incident requires sufficient evidence to establish that a security event occurred.

## Q16. Where are Windows Event Logs stored?
Windows event log files are commonly stored in `C:\Windows\System32\winevt\Logs\`.

## Q17. What is the role of a SOC Analyst during authentication investigations?
The analyst reviews logs, correlates events, evaluates risk, documents findings, and escalates suspected incidents according to established procedures.

## Key Interview Principle
**Correlate the evidence, investigate the context, and avoid unsupported conclusions.**
