+++
title = 'Geospatial Confidence & Uncertainty'
description = 'Position accuracy, coordinate reference systems, and uncertainty in subsea geospatial data'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Geospatial Confidence & Uncertainty

Subsea geospatial data — position fixes, survey tracks, sonar maps, pipeline routes — is used for safety-critical decisions. Position errors of a few metres can place an ROV on the wrong side of a pipeline or mis-identify the location of a discovered anomaly. Understanding and communicating positional uncertainty is essential for anyone using or producing subsea geospatial data.

## Why This Exists

Subsea positioning systems do not have the luxury of GPS, which loses signal underwater. Acoustic positioning systems, inertial navigation units, and Doppler velocity loggers all accumulate error over time and distance. Knowing how much to trust a position — and under what conditions — is as important as knowing the position itself.

## Who This Is For

- Survey engineers designing positioning systems
- ROV pilots and AUV operators interpreting positional data
- Data managers publishing survey products
- Project engineers using subsea geospatial data for engineering decisions

## Coordinate Reference Systems

### Why CRS Matters

The same physical point has different numerical coordinates depending on the coordinate reference system (CRS) used. Mixing CRS without transformation causes positional errors that can be tens to hundreds of metres.

**Required practice:** All geospatial data must have an explicitly declared CRS. Datum and projection must be stated, not assumed.

### Common CRS for Subsea Operations

- **WGS84** — Global datum used by GPS; commonly used for vessel positions
- **ETRS89** — European reference frame; stable relative to the European plate
- **Local projections** — UTM zones or project-specific projections for survey products
- **Vertical datums** — Depth below mean sea level, chart datum, or ellipsoid height must be stated

### Datum Shifts

Transforming between datums introduces errors. The magnitude of the shift between WGS84 and older national datums can exceed 100m. Any transformation must use appropriate transformation parameters and the resulting uncertainty must be added to the positional uncertainty budget.

## Subsea Positioning Technologies

### Ultra-Short Baseline (USBL)

USBL measures the range and bearing from a surface transducer to an underwater transponder:

- **Accuracy** — Typically 0.5–1% of slant range; degrades with depth and range
- **Errors** — Vessel motion, transducer alignment, sound speed profile
- **Mitigation** — Gyro-stabilised transducers, accurate sound speed profiling, USBL calibration transponders

### Long Baseline (LBL)

LBL uses an array of seabed transponders to provide positioning independent of vessel motion:

- **Accuracy** — Typically 0.1–1m RMS in well-surveyed arrays
- **Errors** — Transponder position uncertainty, sound speed errors, acoustic multipath
- **Deployment requirement** — Transponder array must be surveyed before LBL can be used

### Inertial Navigation Systems (INS)

INS integrates accelerometer and gyroscope data to propagate a position forward from a known starting point:

- **Accuracy** — Excellent over short periods; error accumulates over time (dead reckoning drift)
- **Aiding** — DVL (Doppler velocity log) and periodic USBL/LBL fixes constrain INS drift
- **Reset** — Errors must be reset by tying to a known position

### Doppler Velocity Log (DVL)

DVL measures velocity over the seabed using acoustic Doppler:

- **Accuracy** — Velocity accuracy ~0.1–0.5% of speed; position error accumulates
- **Bottom tracking required** — DVL loses bottom-track in steep terrain or beyond range
- **Integration** — DVL is essential for INS aiding in subsea operations

## Uncertainty Quantification

### Sources of Positional Uncertainty

Every position estimate carries contributions from multiple sources:

1. **Sensor measurement uncertainty** — Acoustic range/bearing measurement errors
2. **Sound speed uncertainty** — Incorrect sound speed introduces systematic ranging errors
3. **Vessel position uncertainty** — GNSS error propagates to seabed positions
4. **Time latency** — Position timestamps may not align with observation timestamps
5. **Processing uncertainty** — Filtering, smoothing, and interpolation introduce additional uncertainty

### Total Propagated Uncertainty (TPU)

TPU combines all uncertainty sources into a single position uncertainty estimate, typically expressed as a 2D ellipse at a specified confidence level (e.g., 95%). Modern survey processing software calculates TPU automatically when given correct input uncertainties.

**Requirement:** Survey products must include TPU fields or uncertainty layers. Users must not assume position accuracy without checking TPU.

## Reporting Position Quality

### Minimum Requirements for Published Geospatial Data

All published geospatial data must include:

- Coordinate reference system (EPSG code or equivalent)
- Horizontal positional uncertainty (at stated confidence level)
- Vertical positional uncertainty
- Positioning system and method used
- Date and time of position observation (UTC)

### Quality Flags

Position fixes should carry quality flags indicating:

- Source system (USBL, LBL, INS, DVL-only)
- Data quality at time of observation (signal quality, vessel motion)
- Whether the position is measured or interpolated

## Related Topics

- [Data Provenance & Chain-of-Custody](/ocean-data/provenance/)
- [Sensor Calibration Traceability](/ocean-data/calibration/)
- [Timestamp Integrity](/ocean-data/timestamps/)
- [Raw vs Derived Data](/ocean-data/raw-derived/)
