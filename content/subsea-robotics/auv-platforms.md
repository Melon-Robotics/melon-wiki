+++
title = 'AUV Platforms Overview'
description = 'Autonomous underwater vehicle types, capabilities, and operational characteristics'
date = 2024-01-01T00:00:00Z
draft = false
+++

# AUV Platforms Overview

Autonomous underwater vehicles (AUVs) operate without tethers and without continuous operator control. They execute pre-programmed missions, collecting data and performing tasks while navigating independently. This page covers the major AUV platform categories, their capabilities, and the operational considerations specific to each.

## Why This Exists

AUVs are becoming central to subsea inspection, survey, and monitoring operations. Understanding the platform options, their capabilities, and their limitations is essential for selecting the right vehicle for a given mission and for planning operations that use AUVs effectively and safely.

## Who This Is For

- Engineers and project managers selecting AUV platforms
- ROV pilots and operators transitioning to AUV operations
- Operations managers planning AUV deployments
- Safety officers assessing AUV operational risks

## AUV Categories by Form Factor

### Torpedo/Streamlined AUVs

The most common form factor: an elongated, hydrodynamically optimised body with a propeller aft and control surfaces.

**Characteristics:**
- **Speed:** 1.5–4 knots transit; optimised for efficient forward flight
- **Range:** 10–100+ km depending on battery capacity and speed
- **Depth:** From shallow (<100m) to full ocean depth (6000m+) depending on model
- **Manoeuvrability:** Low — cannot hover or work in confined spaces

**Typical applications:**
- Wide-area bathymetric survey
- Pipeline and cable route survey
- Environmental monitoring transects
- Mine countermeasures (military)

**Examples:** Kongsberg Hugin, Teledyne REMUS, L3 OceanServer Iver

### Hovering/Work-Class AUVs

Multi-thruster vehicles designed for station-keeping and precision manoeuvre, similar to ROVs but without a tether.

**Characteristics:**
- **Speed:** Slow — typically <1 knot transit, hovering capability
- **Range:** Limited by battery capacity; typically <10 km
- **Depth:** Mission-specific, typically 3000–6000m for work-class variants
- **Manoeuvrability:** High — can work in confined spaces, maintain precise positioning

**Typical applications:**
- Subsea infrastructure inspection
- Intervention tasks (with manipulator arms)
- Precision survey of specific targets

**Examples:** Saab Sabertooth, ECA H800

### Gliders

Buoyancy-driven vehicles that move by changing buoyancy and use wings to convert vertical motion into horizontal motion.

**Characteristics:**
- **Speed:** Very slow — typically <0.5 knots
- **Range:** Very long — weeks to months of operation
- **Depth:** From surface to 1000m+ depending on model
- **Manoeuvrability:** Very low — long turning radius, cannot hold station
- **Power:** Extremely low power consumption; very long endurance

**Typical applications:**
- Sustained oceanographic monitoring
- Climate and environmental research
- Persistent surveillance

**Examples:** Teledyne Webb Slocum, Kongsberg Seaglider, iRobot Ocean Aura

### Hybrid AUV/ROVs (Hybrid Vehicles)

Vehicles designed to operate both as AUVs and as ROVs (tethered from a depressor or buoy rather than a surface vessel).

**Applications:** Combining AUV survey capability with ROV intervention capability in a single deployment.

## AUV vs. ROV Selection Criteria

| Criterion | AUV Advantage | ROV Advantage |
|-----------|---------------|---------------|
| Large area coverage | Yes — no tether drag, efficient transit | No — tether limits range |
| Continuous monitoring | Yes — long endurance possible | No — vessel must remain on station |
| Real-time observation | No — delayed data recovery | Yes — live video and control |
| Intervention tasks | No — limited without manipulators | Yes — purpose-built for intervention |
| Communication during mission | No — typically none underwater | Yes — through tether |
| Emergency recovery | Slower — must wait for vehicle return | Faster — pull on tether |

## Launch and Recovery

### Surface Launch and Recovery

Most AUVs are launched and recovered from a surface vessel:

- **A-frame or crane** — For large vehicles or rough sea states
- **Stern ramp** — For smaller vehicles in benign conditions
- **ROV-assisted** — In deepwater operations, an ROV may be used to release/recover the AUV at depth

**Sea state limits:** AUV launch and recovery is more weather-sensitive than ROV operations because the vehicle has no tether for control during deployment.

### Subsea Docking

Some AUV systems use subsea docking stations for deployment, recharging, and data upload:

- Enables persistent monitoring without repeated surface vessel visits
- Requires accurate AUV homing capability
- Introduces single points of failure (dock power, dock communication)

## Related Topics

- [ROV Systems Overview](/subsea-robotics/rov-systems/)
- [Vehicle Classes & Capabilities](/subsea-robotics/vehicle-classes/)
- [Sensor Payloads](/subsea-robotics/sensor-payloads/)
- [Control Frameworks](/subsea-robotics/control-frameworks/)
- [Failure Modes & Recovery](/subsea-robotics/failure-modes/)
- [Loss-of-Comms Behavior](/swarm-systems/loss-of-comms/)
