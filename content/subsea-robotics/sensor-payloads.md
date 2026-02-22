+++
title = 'Sensor Payloads'
description = 'Sensor systems for subsea vehicles: sonar, cameras, and oceanographic instruments'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Sensor Payloads

The sensor payload defines what a subsea vehicle can observe and measure. Payload selection drives mission capability, power consumption, data volume, and vehicle configuration. Understanding sensor types, their capabilities, and their limitations is essential for mission planning and data quality assessment.

## Why This Exists

Sensors are how subsea vehicles perceive and record their environment. The right sensor for a job depends on the target, the environment, the required resolution and accuracy, and the vehicle's power and space budget. A mismatch between sensor capability and mission requirement produces poor data and wasted effort.

## Who This Is For

- Mission planners selecting sensor configurations for specific tasks
- Data managers understanding the characteristics of sensor data products
- Engineers integrating sensors into vehicle systems
- Scientists and engineers using sensor data for decision-making

## Acoustic Sensors

### Multibeam Echosounder (MBES)

MBES emits acoustic pulses in a fan pattern across-track and measures depth across a swath:

- **Swath width:** Typically 2–5× water depth (altitude above seabed)
- **Resolution:** Function of beam width, frequency, and altitude
- **Frequency range:** 200 kHz (shallow, high resolution) to 12 kHz (deep, lower resolution)
- **Applications:** Bathymetric survey, seabed mapping, pipeline route survey

**Data products:** Bathymetric grids, water column data (backscatter, biology)

### Side-Scan Sonar (SSS)

SSS emits acoustic pulses to each side and measures the backscattered intensity:

- **Range:** Each side typically 10–200m depending on frequency
- **Resolution:** Finer than MBES at equivalent range; no depth data
- **Frequency range:** 100–1000 kHz
- **Applications:** Object detection, seabed characterisation, pipeline and cable inspection

**Data products:** Sonar mosaic images; target detection reports

### Sub-Bottom Profiler (SBP)

SBP penetrates the seabed with low-frequency acoustic energy to image sub-seabed structure:

- **Penetration:** Typically 10–50m depending on sediment type and frequency
- **Resolution:** Decimetres vertically
- **Applications:** Buried pipeline detection, sediment characterisation, geohazard assessment

### Acoustic Doppler Current Profiler (ADCP)

ADCP measures current velocity profiles through the water column using Doppler shift of backscattered sound:

- **Range:** Typically 10–300m depending on frequency
- **Applications:** Current measurement, water column monitoring, vehicle navigation (as DVL)

### Doppler Velocity Log (DVL)

DVL uses Doppler shift to measure vehicle velocity relative to the seabed (or water column):

- **Critical for navigation** — DVL aiding of INS is the primary method for accurate AUV navigation
- **Altitude limit** — DVL loses bottom-track when vehicle is too far above the seabed
- **Applications:** Vehicle navigation, aided INS

## Optical Sensors

### Cameras (Video and Still)

Optical imaging requires light:

- **Visibility limit:** Typically <30m in coastal waters; further in clear oceanic water
- **Resolution:** From standard definition to 4K and beyond
- **Lighting:** LED arrays required; colour rendering affects image quality
- **Applications:** Visual inspection, biological observation, documentation

### Laser Scanners

Line-scanning lasers provide high-resolution 3D point clouds:

- **Range:** Typically <5m
- **Resolution:** Sub-millimetre
- **Applications:** Precision metrology, corrosion mapping, anode measurement

## Oceanographic Sensors

### CTD (Conductivity, Temperature, Depth)

Measures the fundamental oceanographic state variables:

- **Required for:** Correcting acoustic sensor performance (sound speed is a function of CTD)
- **Applications:** Oceanographic profiling, water mass characterisation

### Dissolved Oxygen

Measures oxygen concentration, an indicator of biological productivity and water mass age.

### Fluorometers

Measure chlorophyll fluorescence as a proxy for phytoplankton biomass.

### Turbidity Sensors

Measure suspended particle concentration — important for acoustic sensor performance and sediment transport monitoring.

## Payload Integration Considerations

### Power Budget

Each sensor adds to the vehicle's power demand. See [Power Systems & Endurance](/subsea-robotics/power-systems/) for calculating the combined power budget and its effect on mission endurance.

### Data Volume

High-resolution sensors generate large data volumes:

- MBES at 400 kHz: ~1 GB/hour of raw data
- 4K video: 10–100 GB/hour depending on compression
- CTD: negligible

AUV storage capacity and data transfer time at the end of the mission must be planned.

### Acoustic Interference

Multiple acoustic sensors operating simultaneously can interfere. Multibeam sonar, DVL, USBL, and acoustic modems may use overlapping frequency bands. Careful frequency planning and time-division schemes are required.

## Calibration Requirements

All sensors must be calibrated before deployment. See [Sensor Calibration Traceability](/ocean-data/calibration/) for requirements. For acoustic sensors, in-situ calibration checks (sound velocity profile measurement, patch test for MBES) are required before data collection.

## Related Topics

- [ROV Systems Overview](/subsea-robotics/rov-systems/)
- [AUV Platforms Overview](/subsea-robotics/auv-platforms/)
- [Sensor Calibration Traceability](/ocean-data/calibration/)
- [Power Systems & Endurance](/subsea-robotics/power-systems/)
- [Geospatial Confidence & Uncertainty](/ocean-data/geospatial/)
