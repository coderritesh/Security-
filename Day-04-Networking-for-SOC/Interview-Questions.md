# Day 04 — Networking for SOC Interview Questions

## Basic Networking

### 1. What is an IP address?
An IP address identifies a network interface so devices can communicate over an IP network.

### 2. What is the difference between a private and public IP address?
Private IPs are used within private networks and are not directly globally routable. Public IPs are globally routable, subject to routing and security controls.

### 3. What is a default gateway?
It is the routing device a host uses to reach destinations outside its local subnet.

### 4. What is the difference between TCP and UDP?
TCP provides a connection-oriented transport service. UDP provides a connectionless transport service.

### 5. What is DNS?
DNS translates domain names into records such as IP addresses. Analysts investigate DNS when domains fail to resolve or when suspicious domain activity is observed.

### 6. What is ICMP?
ICMP is a network-layer control and diagnostic protocol. Ping commonly uses ICMP Echo Request and Echo Reply messages.

## Network Troubleshooting

### 7. What does `ipconfig` do?
It displays Windows IP configuration, including adapter addresses, subnet masks, and gateways.

### 8. What does `ping` do?
It tests reachability using ICMP Echo messages. A failed ping does not necessarily mean the destination is down.

### 9. What does `nslookup` do?
It queries DNS to obtain records for a domain name and shows information about the responding DNS server.

### 10. What does `netstat -ano` show?
It displays network connections and listening endpoints, numeric addresses and ports, and associated process IDs where available.

### 11. What is the difference between `tracert` and `ping`?
Ping tests reachability using ICMP Echo messages. Tracert helps identify responding hops along a route toward a destination.

### 12. What does `tracert -d` do?
It skips reverse DNS lookups for intermediate hops and displays numeric addresses.

### 13. What does `* * * Request timed out` mean in tracert?
No response was received for those probes within the timeout. A router may filter or rate-limit probes while still forwarding traffic.

## SOC Investigation

### 14. What would you investigate if a website did not open?
I would check the user's symptoms, IP configuration, DNS resolution, connectivity, application errors, proxy settings, and relevant firewall or endpoint logs.

### 15. What would you do if pinging a public IP worked but a domain failed?
I would investigate DNS configuration and resolution, while checking for other possible causes. I would not assume DNS is the only possible issue without more evidence.

### 16. How would you investigate an unfamiliar network connection?
I would identify the local process and PID, destination IP, port, protocol, timestamp, and expected application behavior. I would correlate the result with endpoint and network logs.

### 17. Does an unusual port prove that a connection is malicious?
No. I would investigate the process, destination, application, and surrounding activity before making a judgment.

### 18. In your lab, why did hop 5 time out while the destination was reached?
The intermediate device may not have responded to the traceroute probes. Later hops responded and the destination was reached, so the timeout alone did not indicate a broken route.

### 19. Why were there different hop counts for the two traceroute commands?
They targeted different destinations. Different destinations may follow different routes and require different numbers of responding hops.

### 20. What is the SOC analyst's approach to network investigation?
Identify the event, collect evidence, validate the context, correlate relevant logs, assess impact, document findings, and reach a conclusion supported by evidence.

## Revision Principle

**A single command gives a clue, not a complete security verdict. Correlate evidence before concluding.**
