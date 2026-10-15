# Day 3 — Windows Authentication Attack Detection Practical

## 1. Objective

Investigate Windows authentication events and learn how to identify patterns that may indicate suspicious login activity.

## 2. Lab Environment

- Operating System: Windows
- Tool: Windows Event Viewer
- Log source: Windows Logs → Security
- Event IDs: 4624 and 4625

## 3. Practical Procedure

### Step 1: Open Event Viewer

1. Press `Win + R`.
2. Enter `eventvwr.msc`.
3. Press Enter.

### Step 2: Open Security Logs

Navigate to:

`Event Viewer → Windows Logs → Security`

### Step 3: Filter Authentication Events

1. Select **Filter Current Log**.
2. Enter `4624,4625` in the Event IDs field.
3. Click **OK**.

### Step 4: Investigate a Failed Logon

Open an Event ID 4625 entry and examine its General and Details tabs.

Fields observed during this lab:

| Field | Observed value | Interpretation |
|---|---|---|
| TargetUserName | ASUS | Account associated with the failed logon |
| Logon Type | 2 | Interactive logon |
| Source Network Address | 127.0.0.1 | Loopback address |
| Status | `0xC000006D` | General logon failure |
| SubStatus | `0xC000006A` | Incorrect password |

### Step 5: Review Successful Logons

Locate an Event ID 4624 that occurred after the observed failed attempts.

Review its timestamp, account, logon type, and source network address. Verify these fields independently before linking the successful event to the failed attempts.

## 4. Lab Findings

- Observed approximately 3–5 failed logon events in the reviewed period.
- Observed a successful logon after the failed attempts.
- Inspected a failed logon targeting `ASUS`.
- The examined failed event showed Logon Type 2 and source address `127.0.0.1`.
- The SubStatus indicated an incorrect password.

## 5. SOC Assessment

The observed pattern requires context and correlation. Multiple failed logons followed by a successful logon may be caused by legitimate password-entry mistakes or suspicious authentication activity.

The reviewed evidence does not independently confirm a brute-force attack or account compromise.

Additional investigation should compare the timestamps, account names, source addresses, logon types, and activity following the successful logon.

## 6. Evidence Checklist

Add your own screenshots to the `Screenshots` directory:

- [ ] `event-4625-failed-logon.png` — failed logon event.
- [ ] `event-4625-details.png` — account, logon type, status, and substatus.
- [ ] `event-4624-successful-logon.png` — successful logon event.



## 7. Key Learning

**Authentication events are evidence, not conclusions.** A SOC Analyst correlates the events and investigates the surrounding context before determining whether an incident occurred.

## 8. Conclusion

This practical provided experience using Windows Event Viewer to examine authentication events, interpret failure codes, and assess suspicious login patterns.
