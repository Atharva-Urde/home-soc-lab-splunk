# Home SOC Lab Architecture

# Purpose

The objective of this lab is to simulate a real-world Security Operations Center (SOC) environment using Splunk Enterprise as the Security Information and Event Management (SIEM) platform.

The architecture follows a simplified enterprise deployment where Windows Event Logs are collected by a Splunk Universal Forwarder and securely transmitted to Splunk Enterprise for indexing, searching, monitoring, and future detection engineering.

---

# Architecture Overview

```
                   Home SOC Lab

                Windows 11 Endpoint
        ┌────────────────────────────┐
        │                            │
        │  Windows Event Logs        │
        │  • Security                │
        │  • System                  │
        │  • Application             │
        │                            │
        └──────────────┬─────────────┘
                       │
                       │
             Splunk Universal Forwarder
                       │
                 TCP Port 9997
                       │
                       ▼
        ┌────────────────────────────┐
        │                            │
        │     Splunk Enterprise      │
        │                            │
        │  • Data Indexing           │
        │  • Search & Reporting      │
        │  • Dashboards              │
        │  • Detection Rules         │
        │                            │
        └────────────────────────────┘
```

---

# Components

## Windows 11 Endpoint

The Windows host generates telemetry through native Windows Event Logs.

Currently collected logs include:

* Security
* System
* Application

Future telemetry sources:

* Sysmon
* PowerShell Operational Logs
* Windows Defender
* Task Scheduler
* Registry Auditing

---

## Splunk Universal Forwarder

The Universal Forwarder is a lightweight data collection agent responsible for collecting Windows Event Logs and forwarding them to Splunk Enterprise.

Responsibilities:

* Collect Windows Event Logs
* Compress and securely forward telemetry
* Minimize system resource usage
* Maintain persistent communication with the indexer

---

## Splunk Enterprise

Splunk Enterprise serves as the SIEM platform.

Responsibilities:

* Receive telemetry
* Parse incoming events
* Index log data
* Execute SPL queries
* Generate dashboards
* Support threat hunting
* Enable incident investigations

---

# Current Data Flow

```
Windows Event Logs
        │
        ▼
Universal Forwarder
        │
        ▼
    TCP 9997
        │
        ▼
Splunk Enterprise
        │
        ▼
    main Index
        │
        ▼
Search & Reporting
```

---

# Future Architecture

As the project evolves, additional telemetry sources and security tooling will be integrated.

```
Windows Logs
Sysmon
PowerShell Logs
Windows Defender
        │
        ▼
Universal Forwarder
        │
        ▼
Splunk Enterprise
        │
        ▼
Dedicated Indexes
        │
        ▼
Detection Rules
Dashboards
MITRE ATT&CK Mapping
Incident Investigations
```

---

# Learning Outcomes

Through this architecture, the project demonstrates:

* SIEM deployment
* Log collection
* Endpoint telemetry ingestion
* Data forwarding
* Security monitoring
* Detection engineering fundamentals
* SOC workflow understanding

