+++
title = 'Sensor Calibration Traceability'
description = 'Calibration standards, traceability chains, and documentation for subsea sensors'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Sensor Calibration Traceability

A measurement is only as good as the calibration of the sensor that produced it. Calibration traceability links every field measurement back to a national or international measurement standard through an unbroken chain of comparisons, each with documented uncertainty. Without traceability, measurements cannot be compared across systems, time periods, or organisations.

## Why This Exists

Subsea sensors measure pressure, temperature, salinity, acoustic distance, and many other quantities. Decisions — about dive safety, environmental impact, infrastructure integrity — depend on these measurements being accurate. Traceability ensures that "accurate" means something: that measurements can be compared, replicated, and defended.

## Who This Is For

- Instrument technicians managing sensor calibration
- Data managers documenting measurement uncertainty
- Project managers specifying calibration requirements in contracts
- Regulators and auditors reviewing measurement data quality

## The Calibration Chain

### National and International Standards

At the top of the calibration hierarchy are primary standards maintained by national metrology institutes (NMIs):

- **NIST** (USA) — National Institute of Standards and Technology
- **NPL** (UK) — National Physical Laboratory
- **PTB** (Germany) — Physikalisch-Technische Bundesanstalt

These institutes maintain primary standards for physical quantities (length, mass, temperature, pressure). All traceable calibrations ultimately link back to these standards.

### Working Standards and Reference Instruments

Below NMI standards:

1. **Reference standards** — Calibrated directly against NMI standards; used in calibration laboratories
2. **Working standards** — Calibrated against reference standards; used for field instrument calibration
3. **Field instruments** — Calibrated against working standards before deployment

Each comparison in this chain must be documented with calibration certificates and uncertainty estimates.

## Calibration Documentation Requirements

A valid calibration record must include:

- **Instrument identifier** — Serial number, asset tag
- **Calibration date** — Date calibration was performed
- **Calibration laboratory** — Name and accreditation status of the performing laboratory
- **Standards used** — Identification and certificate numbers of reference standards
- **Measurement results** — As-found and as-left readings at each calibration point
- **Uncertainty** — Measurement uncertainty at each calibration point (k=2, 95% confidence)
- **Pass/fail determination** — Whether the instrument meets its specification
- **Next calibration due** — Date or interval for next calibration
- **Technician signature** — Identity of the person performing the calibration

## Calibration Intervals

Calibration intervals balance cost against the risk of operating with out-of-specification sensors:

- **High-risk sensors** — Shorter intervals (e.g., pressure sensors used for dive safety calculations)
- **Stable, low-risk sensors** — Longer intervals based on historical stability data
- **Event-triggered recalibration** — After physical shock, repair, unusual readings, or suspected damage

**Operational rule:** Instruments used beyond their calibration due date should be flagged and their data marked as potentially invalid until recalibration is completed.

## Common Subsea Sensor Types

### Pressure/Depth Sensors

- **Criticality:** High — used for dive depth monitoring, decompression calculations
- **Calibration requirements:** Traceable to primary pressure standards; calibrate at multiple points across the operating range
- **Common issues:** Zero drift, span drift after exposure to pressure cycling

### CTD (Conductivity, Temperature, Depth) Sensors

- **Criticality:** High for oceanographic data quality
- **Calibration requirements:** Temperature traceable to ITS-90; conductivity calibrated against standard seawater; pressure as above
- **Common issues:** Conductivity cell fouling, thermal lag

### Acoustic Sensors (USBL, DVL, ADCP)

- **Criticality:** Medium to high depending on application
- **Calibration requirements:** Sound speed corrections; alignment surveys for USBL
- **Common issues:** Sound speed profile errors, transducer fouling

### Dissolved Oxygen Sensors

- **Criticality:** Medium for environmental monitoring
- **Calibration requirements:** Two-point calibration (zero and saturated); temperature compensation
- **Common issues:** Membrane fouling, electrolyte depletion

## Measurement Uncertainty

Every measurement has uncertainty — a range within which the true value lies with specified probability. Uncertainty must be:

- **Quantified** — Not just "we calibrated it" but "uncertainty is ±0.1°C at k=2"
- **Propagated** — When measurements are combined or processed, uncertainties combine
- **Reported** — Data products must include uncertainty estimates

Ignoring uncertainty leads to false confidence in data quality. See [Raw vs Derived Data](/ocean-data/raw-derived/) for how uncertainty propagates through data processing.

## Related Topics

- [Data Provenance & Chain-of-Custody](/ocean-data/provenance/)
- [Raw vs Derived Data](/ocean-data/raw-derived/)
- [Timestamp Integrity](/ocean-data/timestamps/)
- [Geospatial Confidence & Uncertainty](/ocean-data/geospatial/)
