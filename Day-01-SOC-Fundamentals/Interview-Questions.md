# Day 01 — SOC Analyst Interview Questions

## 1. What is a SOC?

A Security Operations Center (SOC) is a team or function responsible
for monitoring, detecting, investigating, and responding to security
threats.

## 2. What does a SOC Analyst do?

A SOC Analyst monitors security alerts, analyzes logs, investigates
suspicious activity, identifies potential threats, and escalates
confirmed incidents.

## 3. What is a security event?

A security event is a recorded activity that may be relevant to
security monitoring.

Example:

A user successfully logs into a Windows system.

## 4. What is a security alert?

An alert is generated when a security tool identifies activity that
may require investigation.

Example:

Multiple failed login attempts from the same source.

## 5. What is a security incident?

A security incident is a confirmed or suspected security event that
may affect the confidentiality, integrity, or availability of systems
or data and requires response.

## 6. What is Event ID 4624?

Event ID 4624 represents a successful Windows logon.

## 7. What is Event ID 4625?

Event ID 4625 represents a failed Windows logon.

## 8. Does one 4625 event mean a brute-force attack?

No.

A single failed login can be caused by a user entering the wrong
password.

A SOC analyst should examine the frequency, source, account,
timestamps, and related events before determining whether the activity
is suspicious.

## 9. What is the difference between an event and an alert?

An event is a recorded activity.

An alert is generated when a security tool or detection mechanism
identifies activity that may require investigation.

## 10. How would you investigate repeated failed logins?

I would examine:

1. Number of failed attempts
2. Username/account
3. Source IP or workstation
4. Timestamps
5. Logon type
6. Authentication details
7. Whether a successful login followed
8. Other activity after the successful login

Then I would correlate the events and determine whether the activity
appears legitimate or suspicious.

## 11. What is the basic SOC investigation methodology?

A simple approach is:

WHO → WHEN → WHAT → WHERE FROM → WHAT NEXT

## 12. Why are logs important to a SOC Analyst?

Logs provide evidence of system, authentication, network, and application
activity. They allow analysts to investigate suspicious behavior and
build an incident timeline.
