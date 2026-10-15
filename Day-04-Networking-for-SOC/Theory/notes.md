# Networking Fundamentals for SOC

## 1. IP Address
An IP address identifies a network interface so that devices can communicate over an IP network.

- IPv4 example: `192.168.1.10`
- IPv6 example: `2001:db8::1` (documentation example)

## 2. Private and Public IP Addresses
Private IPv4 ranges are used inside private networks:

- `10.0.0.0/8`
- `172.16.0.0/12`
- `192.168.0.0/16`

Public IP addresses are globally routable, subject to routing and filtering policies. A private address in a traceroute may belong to an internal router or an ISP's internal network.

## 3. Subnet Mask
A subnet mask indicates which part of an IPv4 address identifies the network and which part identifies the host.

Example: `255.255.255.0`, equivalent to `/24`.

## 4. Default Gateway
The default gateway is the router or routing device a host uses to reach destinations outside its local subnet.

## 5. TCP and UDP
- TCP provides a connection-oriented transport service.
- UDP provides a connectionless transport service.

Common examples:
- HTTPS commonly uses TCP port 443.
- DNS commonly uses UDP port 53; TCP port 53 is also used in cases such as zone transfers and responses requiring TCP.
- DHCP commonly uses UDP ports 67 and 68.
- SSH commonly uses TCP port 22.

Modern HTTP/3 uses QUIC over UDP, usually on port 443.

## 6. DNS
The Domain Name System resolves domain names to records such as IP addresses.

Command:
`nslookup google.com`

SOC relevance: investigate DNS failures, unexpected domains, suspicious DNS patterns, and unusual destinations alongside other evidence.

## 7. ICMP and Ping
ICMP carries network control and diagnostic messages. `ping` commonly uses ICMP Echo Request and Echo Reply messages to test reachability.

A failed ping does not prove a host is down because ICMP may be filtered.

## 8. Netstat
`netstat -ano` displays network connections and listening endpoints, numeric addresses and ports, and associated process IDs where applicable.

- `ESTABLISHED`: a TCP connection is established.
- `LISTENING`: a TCP endpoint is waiting for incoming connections.
- PID: process identifier that can be correlated with process information.

UDP does not use TCP connection states.

## 9. Traceroute
On Windows, `tracert` helps reveal responding hops toward a destination.

- Each hop is a responding routing point.
- The displayed times are round-trip times for probes.
- `* * *` means probes did not receive responses within the timeout.
- `tracert -d` skips reverse DNS lookups for intermediate hops.

A timeout at one hop does not necessarily indicate a broken route if later hops respond.

## 10. SOC Investigation Method
1. Identify the source endpoint and destination.
2. Check the IP address, port, protocol, and time.
3. Verify DNS resolution and basic connectivity.
4. Review the process associated with a connection where possible.
5. Correlate findings with firewall, DNS, endpoint, or SIEM logs.
6. Record observations separately from assumptions.
7. Do not declare an incident based on one command alone.
