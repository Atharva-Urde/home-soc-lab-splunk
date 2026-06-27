# Splunk Enterprise Installation and Configuration

## Objective

The objective of this phase was to deploy Splunk Enterprise, configure it as the central SIEM platform, install the Splunk Universal Forwarder, and successfully ingest Windows Event Logs for security monitoring.

---

# Environment

| Component | Details |
|-----------|---------|
| Host Operating System | Windows 11 Home |
| CPU | Intel Core i5-1035G1 |
| RAM | 8 GB |
| SIEM Platform | Splunk Enterprise |
| Log Collector | Splunk Universal Forwarder |
| Network | Localhost (127.0.0.1) |

---

# Step 1 — Install Splunk Enterprise

## Purpose

Splunk Enterprise acts as the Security Information and Event Management (SIEM) platform responsible for receiving, indexing, storing, and analyzing security telemetry.

## Validation

Successfully accessed:

http://localhost:8000

Screenshot:

01-splunk-installation-success.png

---

# Step 2 — Initial Login

## Purpose

Verify that Splunk Enterprise was installed successfully and the web interface is operational.

## Validation

Successfully authenticated into the Splunk Web interface.

Screenshot:

02-splunk-login-dashboard.png

---

# Step 3 — Access Search & Reporting

## Purpose

The Search & Reporting application provides the interface for searching, analyzing, and investigating security logs.

## Validation

Successfully opened the Search & Reporting application.

Screenshot:

03-search-reporting-app.png

---

# Step 4 — Configure Receiving Port

## Purpose

Configured Splunk Enterprise to receive data from Universal Forwarders over TCP port 9997.

Receiving Port:

9997

Screenshot:

04-receiving-port-9997-enabled.png

---

# Step 5 — Install Universal Forwarder

## Purpose

The Splunk Universal Forwarder collects Windows Event Logs and securely forwards them to Splunk Enterprise.

Screenshot:

05-universal-forwarder-installation-success.png

---

# Step 6 — Configure outputs.conf

## Purpose

Configured the Universal Forwarder to forward collected telemetry to Splunk Enterprise.

Configuration:

server = 127.0.0.1:9997

Screenshot:

06-outputs-conf.png

---

# Step 7 — Configure Windows Event Log Collection

## Purpose

Configured the Universal Forwarder to monitor:

- Security Logs
- System Logs
- Application Logs

Validation Command

splunk list inputstatus

Screenshot:

07-win-eventlog-inputs.png

---

# Step 8 — Verify Log Ingestion

## SPL Query

index=main

Validation

Confirmed Windows logs were successfully ingested into Splunk Enterprise.

Screenshot:

08-index-main-events.png

---

# Step 9 — Verify Security Log Collection

## SPL Query

index=main sourcetype=WinEventLog:Security EventCode=4624

Validation

Successfully identified Windows successful logon events.

Screenshot:

09-security-logon-events.png

---

# Result

Successfully deployed a functional Splunk-based SIEM capable of collecting and searching Windows Security, System, and Application Event Logs.

The environment is now ready for additional telemetry sources including Sysmon and PowerShell logging.

---

# Key Takeaways

- Installed Splunk Enterprise
- Configured data receiving
- Installed Universal Forwarder
- Forwarded Windows Event Logs
- Validated Security Event ingestion
- Successfully executed initial SPL queries

---

# Interview Questions

### Why is Splunk Enterprise required?

### What is the purpose of TCP port 9997?

### Why do we use a Universal Forwarder instead of installing Splunk Enterprise on every endpoint?

### Why are Windows Event Logs valuable during incident investigations?
