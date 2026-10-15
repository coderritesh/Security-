# Network Investigation Report — Day 04

## 1. Investigation Summary

**Objective:** Perform basic network diagnostics on a Windows endpoint and interpret DNS resolution, connectivity, active connections, and routing behavior.

**System:** Windows endpoint  
**Tools:** CMD, `ipconfig`, `ping`, `nslookup`, `netstat`, `tracert`  
**Activity type:** Authorized basic network troubleshooting

## 2. Tests Performed

| Test | Command | Observation |
|---|---|---|
| Network configuration | `ipconfig` | Reviewed active adapter configuration and network addressing. |
| Connectivity | `ping` | Ran loopback, public-IP, and domain-based ping tests. |
| DNS resolution | `nslookup` | IP addresses were displayed for the queried domains. |
| Connections | `netstat -ano` | Inspected the connection and listening-endpoint output. |
| Route to Google | `tracert google.com` | Destination reached in 8 displayed hops. |
| Route to public DNS | `tracert -d 8.8.8.8` | Destination reached in 10 displayed hops. |

## 3. Traceroute Findings

### Test A: Google domain

Command:
`tracert google.com`

Resolved destination:
`192.178.173.138`

Observed route:
- Hop 1: `192.168.0.1`
- Hop 2: `192.168.1.1`
- Hop 3: `103.93.199.5`
- Hop 4: `103.93.196.9`
- Hop 5: Request timed out
- Hop 6: `10.108.108.2` responded to one of three probes
- Hop 7: `72.14.196.76`
- Hop 8: `192.178.173.138` — destination reached

### Test B: Public DNS IP

Command:
`tracert -d 8.8.8.8`

Destination:
`8.8.8.8`

Observed route:
- Hop 1: `192.168.0.1`
- Hop 2: `192.168.1.1`
- Hop 3: `103.93.199.5`
- Hop 4: `103.93.196.9`
- Hop 5: Request timed out
- Hop 6: `10.108.108.2` responded to one of three probes
- Hop 7: `72.14.196.76`
- Hop 8: `142.251.49.177`
- Hop 9: `209.85.248.61`
- Hop 10: `8.8.8.8` — destination reached

## 4. Analysis

### Intermediate timeout
Hop 5 did not respond to the probes within the timeout. Subsequent hops responded, and both traces reached their destinations. The timeout may reflect filtering, rate limiting, or non-response to traceroute probes. It does not by itself establish a connectivity failure.

### Private IP addresses
The route includes `192.168.0.1`, `192.168.1.1`, and `10.108.108.2`. These are private IPv4 addresses. They may represent local routing devices or internal network infrastructure. The precise topology cannot be confirmed from traceroute output alone.

### Different hop counts
The first test targeted the IP returned for `google.com`; the second targeted `8.8.8.8`. Different destinations can have different routes and hop counts. The `-d` option skips reverse DNS lookups for intermediate hops.

### Latency
The displayed values are round-trip times for individual probes. Variations can occur because of network conditions and how devices handle diagnostic traffic. A single high value does not establish a performance issue.

## 5. SOC Assessment

**Assessment:** Both destinations were reached during the recorded route tests. Some intermediate probes were non-responsive.

**Security conclusion:** No evidence in these results alone establishes malicious activity, compromise, or a network attack.

**Limitations:** The results are a snapshot from one endpoint. They do not identify the exact physical topology or prove that every application or service is working correctly.

## 6. Recommended Follow-up

If a user reports an actual connectivity issue:
1. Confirm the user's symptom and the affected application.
2. Compare DNS resolution with direct-IP connectivity where appropriate.
3. Inspect relevant local processes and connections.
4. Review firewall, DNS, router, and endpoint logs.
5. Correlate timestamps and destinations before reaching a conclusion.

## 7. Evidence

- `01-ipconfig.png`
- `02-ping-tests.png`
- `03-nslookup.png`
- `04-netstat.png`
- `05-tracert-google.png`
- `06-tracert-dns.png`

## Final Result
The lab demonstrated basic Windows network troubleshooting and the correct interpretation of traceroute responses, including intermediate timeouts. All conclusions are limited to the recorded evidence.
