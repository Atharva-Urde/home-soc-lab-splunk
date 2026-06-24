# Phase 1 - Splunk Installation Validation

## Objective

Verify that Splunk Enterprise is functioning correctly after installation.

## Validation Steps

### Query Used

```spl
index=_*
| stats count by index
```

### Results

The following built-in indexes were detected:

- _audit
- _configtracker
- _internal
- _introspection
- _telemetry

## Conclusion

Splunk Enterprise was successfully installed and validated.

Internal logging, indexing, and search functionality were confirmed operational.
