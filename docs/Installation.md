# Splunk Installation

## Installation Date

24 June 2026

## Software

* Splunk Enterprise
* Windows 11 Home
* 64-bit MSI Installer

## Objective

Deploy Splunk Enterprise as the central SIEM platform for the Home SOC Lab.

## Status

- [x] Splunk installer downloaded
- [ ] Splunk installed
- [ ] Web interface verified
- [ ] Windows logs ingested
- [ ] Sysmon integrated

## Notes

Downloaded the official Splunk Enterprise installer from Splunk's website for deployment on the Windows host system.

## Installation Verification

### Result

Splunk Enterprise was successfully installed on the Windows 11 host machine.

### Verification Steps

* Confirmed successful installation through the installer completion screen.
* Verified access to the Splunk web interface at:
  http://localhost:8000
* Successfully authenticated using administrator credentials.

### Outcome

The Splunk Enterprise instance is operational and ready for log ingestion and SOC monitoring activities.

## Internal Log Verification

### Test Query

index=_*

### Result

Successfully retrieved internal Splunk events from built-in indexes.

### Observations

* Splunk audit logs were present.
* Search functionality was operational.
* Internal indexing services were functioning correctly.

### Conclusion

The Splunk instance was verified as healthy and capable of ingesting and indexing data.


