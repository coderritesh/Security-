# Day 04 — Networking for SOC

## Objective
Understand essential networking concepts and practice Windows commands used by SOC analysts for network troubleshooting and initial investigation.

## Topics Covered
- IPv4 addresses, subnet masks, and default gateways
- Private and public IP addresses
- TCP and UDP
- Common ports and protocols
- DNS resolution
- ICMP and ping
- Active network connections and listening ports
- Network route analysis using tracert

## Practical Tasks
1. Inspect network configuration using `ipconfig`.
2. Test connectivity using `ping`.
3. Resolve domain names using `nslookup`.
4. Inspect connections and ports using `netstat`.
5. Trace the route to Google using `tracert google.com`.
6. Trace the route to Google's public DNS using `tracert -d 8.8.8.8`.

## Key Findings
- Both traceroute tests reached their respective destinations.
- Some intermediate probes timed out, but later hops responded.
- A traceroute timeout alone does not establish a network failure.
- DNS resolution, connectivity tests, and connection information provide different pieces of evidence.

## SOC Relevance
These commands help analysts perform initial network troubleshooting, understand endpoint connectivity, identify relevant connection details, and collect evidence for further investigation.

## Evidence
Practical outputs and investigation notes are stored in the `Practical/` directory.

## Important Note
This is a beginner-level lab performed on a Windows endpoint. Findings are limited to the commands and outputs observed. No malicious activity was established by these tests.

## Status
Completed — practical exercises and documentation.
