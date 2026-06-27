# Deployment Validation

**Project Phase:** Phase 1 – SIEM Deployment

**Status:** ✅ Completed

**Last Updated:** July 2026

**Author:** Atharva Urde

---

# Objective

The purpose of this document is to validate that the Splunk Enterprise deployment and Universal Forwarder configuration are functioning correctly. Each validation step includes the objective, validation method, expected result, and supporting evidence.

---

# Validation 1 – Splunk Web Interface

## Objective

Verify that Splunk Enterprise is accessible through the web interface.

## Validation Method

Access:

http://localhost:8000

## Expected Result

The Splunk login page loads successfully, and authentication grants access to the Splunk dashboard.

## Evidence

Screenshot:

02-splunk-login-dashboard.png

---

# Validation 2 – Search & Reporting Application

## Objective

Confirm that the Search & Reporting application is available.

## Validation Method

Navigate to:

Apps → Search & Reporting

## Expected Result

The Search & Reporting interface loads successfully.

## Evidence

Screenshot:

03-search-reporting-app.png

---

# Validation 3 – Receiving Port

## Objective

Verify that Splunk Enterprise is configured to receive forwarded data.

## Validation Method

Navigate to:

Settings → Forwarding and Receiving → Receiving Data

## Expected Result

TCP Port 9997 is enabled.

## Evidence

Screenshot:

04-receiving-port-9997-enabled.png

---

# Validation 4 – Universal Forwarder Configuration

## Objective

Verify that the Universal Forwarder is configured to forward data to Splunk Enterprise.

## Validation Method

Review the outputs.conf configuration.

## Expected Result

The forwarding destination is configured as:

127.0.0.1:9997

## Evidence

Screenshot:

06-outputs-conf.png

---

# Validation 5 – Windows Event Log Inputs

## Objective

Verify that the Universal Forwarder is monitoring Windows Event Logs.

## Validation Method

Command:

splunk list inputstatus

## Expected Result

The following inputs are active:

- WinEventLog://Security
- WinEventLog://System
- WinEventLog://Application

## Evidence

Screenshot:

07-win-eventlog-inputs.png

---

# Validation 6 – Windows Event Log Ingestion

## Objective

Verify that Windows Event Logs are successfully indexed by Splunk.

## SPL Query

index=main

## Expected Result

Windows Event Logs are returned.

## Evidence

Screenshot:

08-index-main-events.png

---

# Validation 7 – Security Event Collection

## Objective

Verify that Windows Security Event Logs are searchable.

## SPL Query

index=main sourcetype=WinEventLog:Security EventCode=4624

## Expected Result

Successful Windows logon events are displayed.

## Evidence

Screenshot:

09-security-logon-events.png

---

# Validation Summary

| Component | Status |
|-----------|--------|
| Splunk Enterprise | ✅ Operational |
| Search & Reporting | ✅ Operational |
| Receiving Port 9997 | ✅ Operational |
| Universal Forwarder | ✅ Operational |
| Windows Event Logs | ✅ Operational |
| Security Log Collection | ✅ Operational |

---

# Key Takeaways

- Verified end-to-end log ingestion.
- Confirmed Windows Event Log monitoring.
- Validated successful communication between the Universal Forwarder and Splunk Enterprise.
- Established a baseline for future telemetry sources such as Sysmon.

---

# Interview Questions

1. How do you verify that a Universal Forwarder is successfully sending logs to Splunk?
2. Why is validation important after deploying a SIEM?
3. What would you check first if `index=main` returned no events?
