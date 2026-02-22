+++
title = 'Multi-Vehicle Coordination'
description = 'Coordination strategies for multi-AUV and multi-ROV subsea operations'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Multi-Vehicle Coordination

Multi-vehicle systems achieve objectives that single vehicles cannot — larger area coverage, redundant sensing, cooperative tasks requiring multiple simultaneous positions. But coordination introduces new failure modes and operational complexity. This page covers coordination strategies and the safety considerations specific to multi-vehicle subsea operations.

## Why This Exists

Multi-vehicle operations are becoming practical as AUVs become more capable and affordable. But deploying multiple vehicles without a coherent coordination strategy creates collision risk, duplicated effort, and unpredictable system behaviour. Understanding coordination approaches helps operators design safe and effective multi-vehicle missions.

## Who This Is For

- Engineers designing multi-vehicle systems
- Mission planners coordinating multiple subsea vehicles
- Safety officers assessing multi-vehicle operational risk
- Operations managers evaluating multi-vehicle systems

## Why Multi-Vehicle Operations

### Expanded Area Coverage

A fleet of N vehicles can survey N times the area in a given time window, enabling:

- Completion of large surveys within narrow weather windows
- Real-time monitoring of large geographic areas
- Redundant coverage for quality assurance

### Cooperative Sensing

Multiple vehicles can observe the same target simultaneously from different angles or with complementary sensors:

- Acoustic ranging between vehicles (cooperative navigation)
- Simultaneous multi-aspect sonar imaging
- Triangulated position fixing using multiple observers

### Redundancy

If one vehicle in a fleet fails, others can continue:

- Mission completion despite individual vehicle failures
- Critical sensor or sampling can continue at reduced pace
- Recovery vehicle capability without ending the mission

## Coordination Architectures

### Centralised Coordination

A single coordinator (surface system or lead vehicle) maintains the mission plan for all vehicles and issues commands:

- **Advantages:** Globally optimal planning; single point for state awareness
- **Disadvantages:** Single point of failure; requires communication with all vehicles; high communication load
- **Suitable for:** Small fleets with reliable communication links

### Decentralised Coordination

Each vehicle makes its own decisions based on local information and limited peer communication:

- **Advantages:** Robust to communication loss; scales to large fleets
- **Disadvantages:** Sub-optimal globally; potential for conflicting decisions; harder to verify
- **Suitable for:** Large fleets; operations with unreliable communication

### Market-Based / Task Allocation

Vehicles bid on tasks based on their position, remaining energy, and capability:

- Tasks are allocated to the vehicle best placed to execute them
- Reallocation occurs when a vehicle fails or conditions change
- **Advantages:** Adaptive; handles vehicle failures gracefully
- **Disadvantages:** Requires communication for bidding; may not find optimal allocation

### Pre-Planned Deconflicted Missions

In simple cases, each vehicle is assigned a fixed, independent sub-mission that does not require inter-vehicle coordination during execution:

- Separate survey lanes with sufficient spacing
- Separate time windows for shared areas
- **Advantages:** No communication required during mission; simple to plan and verify
- **Disadvantages:** Not adaptive to vehicle failures; no cooperative sensing capability

## Collision Avoidance

### Deconfliction by Design

The safest approach is to plan missions that physically separate vehicles at all times:

- Assign separate survey lanes with sufficient lateral separation
- Assign separate depth layers for vehicles operating in the same horizontal area
- Assign time-separated access to overlapping areas

### Reactive Collision Avoidance

For systems that must operate in shared space:

- Each vehicle monitors the positions of other vehicles
- When separation falls below a threshold, vehicles execute avoidance manoeuvres
- Avoidance protocols must be agreed and consistent across all vehicles — conflicting avoidance manoeuvres can cause collisions

**Communication requirement:** Reactive collision avoidance requires vehicles to share position information. This requires a reliable communication link, which is not guaranteed for acoustic modems at range.

## Communication in Multi-Vehicle Systems

### Bandwidth Limitations

Acoustic modems typically provide <10 kbps total bandwidth for a network of vehicles. With multiple vehicles sharing a channel:

- Each vehicle gets a fraction of total bandwidth
- Message collision must be managed (time-division or CDMA)
- High-rate data cannot be shared in real time

### Communication Protocols

Multi-vehicle systems use protocols to manage shared communication channels:

- **Time-division multiple access (TDMA)** — Each vehicle has a time slot to transmit; predictable but wastes capacity when vehicles have nothing to say
- **CSMA** — Vehicles listen before transmitting; efficient but collision-prone in high-traffic conditions
- **OFDM** — Orthogonal frequency division; higher bandwidth but complex

### Minimum Required Communication

A well-designed multi-vehicle system should function safely even with only a fraction of planned communications succeeding. Safety-critical coordination (collision avoidance, abort commands) must use the most reliable communication mode available.

## Safety Separation Standards

No universal standard exists for minimum separation between subsea vehicles. Project-specific analysis should consider:

- Vehicle speeds and turning radii
- Position uncertainty of each vehicle
- Time delay between position measurement and response
- Communication reliability

**Practical minimum:** Separation should be sufficient that, even if both vehicles' positions are at the extremes of their uncertainty ellipses, they remain separated. Add a factor for response time.

## Related Topics

- [Communication Systems](/swarm-systems/communications/)
- [Loss-of-Comms Behavior](/swarm-systems/loss-of-comms/)
- [Latency & Bandwidth Tradeoffs](/swarm-systems/latency-bandwidth/)
- [Graceful Degradation](/swarm-systems/degradation/)
- [AUV Platforms Overview](/subsea-robotics/auv-platforms/)
- [Control Frameworks](/subsea-robotics/control-frameworks/)
