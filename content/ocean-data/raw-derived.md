+++
title = 'Raw vs Derived Data'
description = 'Distinctions between raw sensor data and derived data products, and why preserving the original matters'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Raw vs Derived Data

Raw data is what sensors record directly. Derived data is what you get after processing, filtering, correcting, or combining raw data. The distinction matters for data integrity, auditability, and reproducibility: anyone must be able to re-derive your derived products from the raw data and get the same result.

## Why This Exists

Processing transforms data. A temperature measurement corrected for sensor bias, smoothed over a time window, and converted to potential temperature is very different from the original thermistor voltage reading. If only the derived product is archived, you cannot go back to check whether the processing was correct, apply a new correction, or reproduce the result with different parameters. Raw data preservation is the foundation of reproducible science and auditable operations.

## Who This Is For

- Data managers designing data storage and archiving pipelines
- Engineers and scientists processing sensor data
- Auditors reviewing data quality and processing lineage
- Project managers specifying data deliverable requirements

## Definitions

### Raw Data

Raw data is the unmodified output of a sensor or measurement system:

- **Voltage readings** from a thermistor before temperature conversion
- **Acoustic travel times** from a ranging system before position calculation
- **Raw ADC counts** from a sonar system before processing
- **Video frames** from a camera before compression or enhancement

Raw data should be archived exactly as received, with timestamps and calibration metadata.

### Calibrated Data

Calibrated data is raw data with calibration corrections applied:

- Sensor offsets and gains applied
- Temperature compensation applied
- Factory calibration coefficients applied

Calibrated data is still close to the measurement; it should be reproducible from raw data plus the calibration coefficients.

### Processed Data

Processed data has undergone further transformation:

- **Filtering** — Smoothing, outlier removal
- **Gridding** — Interpolating point data to a regular grid
- **Fusion** — Combining data from multiple sensors
- **Derived quantities** — Computing salinity from conductivity, temperature, and pressure

### Data Products

Data products are the final outputs delivered to end users:

- Bathymetric maps
- Current profiles
- Anomaly detection reports
- Inspection reports

## The Preservation Imperative

### What Must Be Preserved

At minimum, archive:

1. **Raw data** — Original sensor outputs, exactly as received
2. **Calibration records** — Coefficients used to convert raw data
3. **Processing code and version** — The software used, with version numbers
4. **Processing parameters** — Configuration files, filter settings, parameter choices
5. **Processing logs** — Records of what was done, when, and by whom

### Why You Cannot Rely on Derived Products Alone

If only the derived product is kept:

- **Errors cannot be corrected** — A discovered calibration error requires re-processing from raw data
- **Replication is impossible** — Third parties cannot verify your results
- **Regulatory defence is weakened** — Cannot demonstrate that data was not manipulated
- **Scientific value is reduced** — Future reprocessing with improved methods is impossible

## Processing Pipelines

### Version Control for Processing Code

Processing software must be version-controlled:

- Every version that was used to process data must be preserved
- Processing outputs must reference the software version that produced them
- Changes to processing software must be documented and reviewed

### Reproducibility Requirements

A processing pipeline is reproducible if:

1. Starting from the same raw data
2. Using the same processing code (same version)
3. Using the same processing parameters

You get bit-for-bit identical output. Non-deterministic processing (random seeds, floating-point non-determinism) must be documented and managed.

## Flagging and Quality Control

### Quality Flags on Raw Data

Individual raw data records should carry quality flags:

- **0 — Good** — Data passed all quality checks
- **1 — Probably good** — Data passed automated checks but not manually reviewed
- **2 — Suspect** — Automated checks raised a flag; manual review required
- **3 — Bad** — Data failed quality checks; do not use
- **9 — Missing** — No data available

These flags must propagate through processing: derived products should carry the worst quality flag of any contributing raw data.

### Gap Handling

Data gaps must be documented:

- Gap start and end times
- Reason for gap (sensor failure, communication loss, maintenance)
- Whether gaps are filled (interpolated) and if so, how

Filled or interpolated values must be flagged as such and never presented as measured data.

## Related Topics

- [Data Provenance & Chain-of-Custody](/ocean-data/provenance/)
- [Sensor Calibration Traceability](/ocean-data/calibration/)
- [Audit Logs & Immutability](/ocean-data/audit-logs/)
- [Timestamp Integrity](/ocean-data/timestamps/)
