+++
title = 'Vehicle Classes & Capabilities'
description = 'Classification of subsea vehicles by capability, role, and operating depth'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Vehicle Classes & Capabilities

Subsea vehicles are classified by their operational role, level of autonomy, depth rating, and intervention capability. Understanding the classification helps in matching the right vehicle type to a specific mission requirement and understanding the operational constraints that apply.

## Why This Exists

"Subsea vehicle" covers everything from a shallow-water inspection drone to a full-ocean-depth survey AUV. The operational, safety, and regulatory requirements differ dramatically across these categories. Clear classification prevents misapplication of capability or operating requirements.

## Who This Is For

- Project managers specifying vehicle requirements for operations
- Engineers selecting or designing vehicles for specific missions
- Safety officers understanding the risk profile of different vehicle types
- Regulators and auditors assessing operational compliance

## Classification by Level of Autonomy

### Remotely Operated Vehicles (ROVs)

Tethered, operator-controlled vehicles:

- **Control:** Continuous real-time operator control via umbilical
- **Communication:** High-bandwidth copper or fibre umbilical (video, commands, telemetry)
- **Endurance:** Unlimited while tethered; limited by consumables and personnel rotation
- **Safety:** Tether provides physical recovery mechanism; immediate operator response to anomalies

### Semi-Autonomous Underwater Vehicles (SAUVs)

Vehicles with both tethered and autonomous modes, or with significant autonomous stabilisation and task execution:

- **Control:** Operator provides high-level commands; vehicle executes autonomously
- **Communication:** Tethered or acoustic (for extended range)
- **Applications:** Hover-capable AUVs that can be remotely supervised when acoustic comms are available

### Autonomous Underwater Vehicles (AUVs)

Untethered, self-navigating vehicles executing pre-programmed missions:

- **Control:** Operator-defined before deployment; autonomous during mission
- **Communication:** Acoustic (low bandwidth, high latency) or none during mission
- **Endurance:** Limited by battery; typically hours to days
- **Safety:** No immediate intervention capability; must have built-in fail-safe behaviours

See [AUV Platforms Overview](/subsea-robotics/auv-platforms/) for AUV categories.

## Classification by Operational Role

### Observation-Class ROVs

Light vehicles for observation and inspection:

- **Depth rating:** Typically 100–1000m
- **Payload:** Cameras, basic sensors; limited or no manipulators
- **Launch system:** Can be deployed from small vessels; some man-portable
- **Applications:** Shallow inspection, scientific observation, aquaculture monitoring

### Work-Class ROVs

Heavy vehicles with significant intervention capability:

- **Depth rating:** Typically 2000–4000m; some rated to 6000m
- **Payload:** Multiple cameras, manipulators (2×), heavy tooling, large sensor payloads
- **Launch system:** Requires dedicated handling system (LARS) and large support vessel
- **Thrust:** 100–400+ kg bollard pull
- **Applications:** Offshore construction and installation, subsea infrastructure maintenance, pipeline intervention

### Survey AUVs

AUVs optimised for large-area mapping:

- **Form factor:** Torpedo/streamlined
- **Depth rating:** Shallow (100m) to full ocean depth (6000m+)
- **Payload:** MBES, SSS, SBP, CTD
- **Applications:** Route surveys, environmental baseline, geohazard assessment

### Inspection AUVs

AUVs optimised for detailed inspection of specific targets:

- **Form factor:** Hovering/multi-thruster
- **Depth rating:** Mission-specific
- **Payload:** Cameras, laser scanners, NDT sensors
- **Applications:** Pipeline and riser inspection, structure inspection

### Gliders

Low-power, long-endurance oceanographic platforms:

- **Form factor:** Winged, buoyancy-driven
- **Depth rating:** 200–1000m typically
- **Payload:** Oceanographic sensors (CTD, ADCP, fluorometer)
- **Endurance:** Weeks to months
- **Applications:** Sustained oceanographic monitoring

## Classification by Depth Rating

Depth rating is a fundamental vehicle characteristic that limits where it can operate:

| Class | Depth Rating | Typical Applications |
|-------|-------------|---------------------|
| Shallow | <100m | Harbour, aquaculture, diver support |
| Mid-water | 100–1000m | Continental shelf inspection |
| Deep | 1000–3000m | Deep shelf and upper slope |
| Deep-water | 3000–4000m | Standard offshore deepwater |
| Ultra-deep | 4000–6000m | Deepwater oil and gas |
| Full ocean | 6000m+ | Scientific research, deep trench |

**Operational rule:** Never deploy a vehicle beyond its rated depth. Safety factors for pressure housings do not accommodate arbitrary additional depth.

## Inspection Qualification Standards

Work-class ROVs and inspection AUVs used for safety-critical inspections (structural, pipeline integrity) may require certification:

- **Class society acceptance** — DNV, Bureau Veritas, Lloyd's Register inspection and documentation
- **Client qualification** — Asset operators may have specific qualification requirements
- **National regulations** — Some jurisdictions require approved vehicle types for specific applications

## Related Topics

- [ROV Systems Overview](/subsea-robotics/rov-systems/)
- [AUV Platforms Overview](/subsea-robotics/auv-platforms/)
- [Sensor Payloads](/subsea-robotics/sensor-payloads/)
- [Power Systems & Endurance](/subsea-robotics/power-systems/)
- [Failure Modes & Recovery](/subsea-robotics/failure-modes/)
