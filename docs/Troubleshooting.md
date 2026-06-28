# Troubleshooting Guide

**Project Phase:** Phase 1 – SIEM Deployment

**Status:** ✅ Completed

**Last Updated:** July 2026

**Author:** Atharva Urde

---

# Objective

This document captures the issues encountered during the deployment of the Home SOC Lab and documents the investigation process, root cause, resolution, and lessons learned. The purpose is to provide a reusable knowledge base for future deployments and to demonstrate systematic troubleshooting during SIEM implementation.

---

# Issue 001 – Windows Event Logs Not Appearing in Splunk

## Phase

Universal Forwarder Configuration

## Symptoms

- Windows Event Logs were not visible in Splunk.
- `index=main` returned no events.
- Internal Splunk logs (`index=_internal`) were present.

## Investigation

Verified that:

- Splunk Enterprise was operational.
- Receiving port **9997** was enabled.
- The Universal Forwarder was configured with `outputs.conf`.
- The forwarder was successfully communicating with Splunk.

Since forwarding appeared functional but no Windows Event Logs were present, attention shifted to the data collection configuration.

## Root Cause

The Universal Forwarder was configured to forward data (`outputs.conf`) but had no `inputs.conf` configuration specifying which Windows Event Logs should be collected.

Without input definitions, the forwarder had nothing to send.

## Resolution

Created `inputs.conf` containing the following WinEventLog stanzas:

- Application
- System
- Security

Restarted the Universal Forwarder.

## Verification

Executed:

```cmd
splunk list inputstatus
```

Confirmed active monitoring of:

- WinEventLog://Security
- WinEventLog://System
- WinEventLog://Application

Successfully validated data ingestion using:

```spl
index=main
```

## Lessons Learned

Forwarding configuration alone does not enable data collection. Both `outputs.conf` and `inputs.conf` are required for successful log ingestion.

---

# Issue 002 – Difference Between Internal and User Indexes

## Phase

Deployment Validation

## Symptoms

Searches against:

```spl
index=*
```

returned no events.

However,

```spl
index=_internal
```

returned millions of events.

This initially suggested that Splunk was functioning while Windows telemetry was missing.

## Investigation

Reviewed the distinction between internal Splunk indexes and user-created indexes.

Verified that `_internal` stores Splunk operational logs rather than Windows Event Logs.

## Root Cause

A misunderstanding of Splunk index types led to confusion during validation.

Internal indexes confirmed that Splunk itself was operational but did not indicate successful Windows log ingestion.

## Resolution

Focused validation on:

```spl
index=main
```

After correcting the Universal Forwarder configuration, Windows Event Logs became available.

## Verification

Successfully retrieved Windows Event Logs using:

```spl
index=main
```

## Lessons Learned

Operational health of Splunk should be validated separately from successful telemetry ingestion.

---

# Issue 003 – Confirming Windows Event Log Collection

## Phase

Deployment Validation

## Symptoms

Although events were visible, it was necessary to verify exactly which Windows Event Logs were being monitored.

## Investigation

Executed:

```cmd
splunk list inputstatus
```

Confirmed that the Universal Forwarder was actively monitoring:

- Security
- System
- Application

## Root Cause

No configuration issue was present. This validation was performed to confirm that the expected telemetry sources were enabled.

## Resolution

Verified active monitoring of all required Windows Event Logs.

## Verification

Successfully queried Security Event ID 4624:

```spl
index=main sourcetype=WinEventLog:Security EventCode=4624
```

Successful Windows logon events were returned.

## Lessons Learned

Validation should confirm both data ingestion and the completeness of telemetry sources.

---

# Key Takeaways

- Troubleshooting should follow a structured investigation process.
- Separate infrastructure health from telemetry validation.
- Verify configurations before assuming service failures.
- Always validate changes after modifying configuration files.

---

# Engineering Notes

## Design Decision

Each issue is documented using a structured incident format to mirror professional engineering knowledge bases and simplify future troubleshooting.

## Future Improvement

As the lab grows with Sysmon, PowerShell logging, and attack simulations, this document will be expanded with additional deployment and detection-related issues.

---

# Interview Questions

1. What is the difference between `outputs.conf` and `inputs.conf`?
2. Why might `index=_internal` contain events while `index=main` does not?
3. How would you verify that a Universal Forwarder is actively collecting Windows Event Logs?
4. What steps would you follow if Windows Security events stopped appearing in Splunk?
