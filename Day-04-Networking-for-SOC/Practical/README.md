# Practical Lab — Windows Network Investigation

## Objective
Practice basic network troubleshooting commands and understand their relevance to SOC investigations.

## Environment
- Operating system: Windows
- Tool: Command Prompt (CMD)
- Lab type: Local endpoint network diagnostics

## Commands Performed

### 1. Inspect network configuration
```cmd
ipconfig
```
Purpose: Identify the active adapter, IPv4 address, subnet mask, and default gateway.

### 2. Test connectivity
```cmd
ping 127.0.0.1
ping 8.8.8.8
ping google.com
```
Purpose: Test loopback connectivity, attempt reachability to a public IP, and check domain resolution alongside reachability.

### 3. Test DNS resolution
```cmd
nslookup google.com
nslookup microsoft.com
```
Purpose: Check whether the configured DNS resolver returns IP addresses for the requested domains.

### 4. Inspect network connections
```cmd
netstat -ano
netstat -abno
netstat -e
```
Purpose: Inspect connections, listening endpoints, associated PIDs, executable information where permitted, and interface statistics.

Note: Run `netstat -abno` from an elevated Command Prompt if executable details are required.

### 5. Trace a route to Google
```cmd
tracert google.com
```

### 6. Trace a route to a public DNS address
```cmd
tracert -d 8.8.8.8
```

## Evidence
See the `Screenshots/` folder for captured command outputs.

## Safety and Privacy
- Only test normal connectivity to public services.
- Do not publish credentials, public IP details, or unnecessary device information.
- Treat unfamiliar connections as investigation leads, not proof of compromise.

## Outcome
The commands provided practice in network configuration review, connectivity testing, DNS troubleshooting, connection inspection, and route analysis.
