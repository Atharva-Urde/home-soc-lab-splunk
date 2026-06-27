# 🛡️ Home SOC Lab using Splunk

## Overview

This project documents the design and implementation of a Home Security Operations Center (SOC) Lab using Splunk Enterprise. The objective is to simulate a real-world SOC environment by collecting, monitoring, and analyzing Windows security telemetry while building practical detection engineering and threat hunting skills.

Unlike a basic installation guide, this repository follows a structured engineering approach by documenting the complete deployment process, configuration files, troubleshooting steps, validation procedures, and future enhancements.

---

## Project Objectives

* Deploy Splunk Enterprise as the SIEM platform
* Configure Splunk Universal Forwarder for log collection
* Ingest Windows Event Logs
* Integrate Sysmon for enhanced endpoint telemetry
* Develop detection rules using SPL
* Build SOC dashboards
* Simulate attacks from a Kali Linux machine
* Map detections to the MITRE ATT&CK Framework
* Document the complete deployment process

---

## Current Project Status

### Completed

* Splunk Enterprise Installation
* Splunk Web Configuration
* Universal Forwarder Deployment
* Windows Event Log Collection
* Successful Security Event Ingestion

### In Progress

* Repository Documentation
* Architecture Documentation

### Planned

* Sysmon Integration
* Detection Engineering
* Dashboard Development
* Attack Simulation
* Incident Investigations

---

## Repository Structure

```text
docs/
configs/
detections/
dashboards/
screenshots/
README.md
```

---

## Documentation

| Document           | Description                        |
| ------------------ | ---------------------------------- |
| Architecture.md    | Lab architecture and data flow     |
| Installation.md    | Complete installation procedure    |
| Validation.md      | Validation steps and screenshots   |
| Troubleshooting.md | Issues encountered and resolutions |

---

## Technologies Used

* Splunk Enterprise
* Splunk Universal Forwarder
* Windows 11
* Kali Linux (VirtualBox)
* SPL (Search Processing Language)

---

## Author

**Atharva Urde**

This project is being developed as a practical cybersecurity portfolio focused on SOC operations, SIEM deployment, detection engineering, and threat hunting.
