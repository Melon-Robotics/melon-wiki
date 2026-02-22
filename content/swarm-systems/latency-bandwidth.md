+++
title = 'Latency & Bandwidth Tradeoffs'
description = 'Communication latency and bandwidth constraints in subsea and swarm operations'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Latency & Bandwidth Tradeoffs

Subsea communication is constrained by physics: acoustic waves travel at ~1500 m/s through water, and the available bandwidth for acoustic modems is severely limited compared to terrestrial or satellite links. These constraints fundamentally shape how subsea systems can be designed and operated. Understanding them is essential for designing coordination systems that work within physical limits.

## Why This Exists

Systems designed without understanding communication constraints fail in the field. A coordination algorithm that requires 10 round-trip communications per second will not function on an acoustic link that takes 2 seconds for each exchange. Understanding latency and bandwidth drives realistic system design.

## Who This Is For

- Engineers designing subsea communication systems
- Architects designing multi-vehicle coordination protocols
- Operations managers setting realistic expectations for remote monitoring
- Mission planners designing communication schedules

## Acoustic Communication Fundamentals

### Propagation Speed

Sound travels at approximately 1500 m/s in seawater (varying with temperature, salinity, and pressure). At 1500m range:

- **One-way latency:** ~1 second
- **Round-trip latency:** ~2 seconds (minimum, without processing delays)

At longer ranges:

- 3000m → 2s one-way, 4s round-trip
- 10km → 6.7s one-way, 13.3s round-trip

**Implication:** Real-time control at range is impossible. Any control loop that relies on acoustic feedback will have response delays measured in seconds to tens of seconds.

### Bandwidth

Acoustic modems in typical subsea configurations provide:

- **Short range (<1km):** Up to 50 kbps
- **Medium range (1–5km):** 1–10 kbps
- **Long range (>5km):** <1 kbps

Compare to terrestrial WiFi (>100 Mbps) or satellite (1–100 Mbps): acoustic bandwidth is 3–8 orders of magnitude lower.

**Implication:** Video streaming, large file transfers, and any high-volume data exchange are not possible acoustically at operational ranges. Only compact, compressed messages are feasible.

### Bandwidth-Latency Product

The bandwidth-delay product (BDP) determines the amount of data that can be "in flight" at any time. With high latency and low bandwidth, windowing protocols become critical, and protocol overhead can dominate useful payload.

**Example:** At 1 kbps bandwidth and 4s round-trip time, the BDP is 4000 bits (500 bytes). A 50-byte message header represents 10% protocol overhead.

## Effects on System Design

### Control Loop Design

Control systems must be designed for the available round-trip time:

- **Closed-loop control** requiring fast feedback cannot run over acoustic links at range
- **Supervisory control** with slow feedback (seconds to minutes) is feasible
- **Pre-programmed missions** with no feedback loop are the most robust approach

For a vehicle at 1km range (2s RTT), any control loop with a bandwidth above 0.25 Hz is limited by communication, not vehicle dynamics.

### State Synchronisation

Multi-vehicle systems that share state (position, task assignments, sensor data) must manage state synchronisation with high-latency, low-bandwidth links:

- **Event-driven updates** — Send updates only when state changes significantly
- **Dead-reckoning** — Interpolate state between updates using physical models
- **Eventual consistency** — Accept that different vehicles have temporarily inconsistent views of shared state
- **Conflict resolution** — Define clear rules for resolving conflicting state updates when they arrive

### Message Prioritisation

Given limited bandwidth, messages must be prioritised:

1. **Safety-critical:** Abort commands, emergency position reports
2. **Navigation-critical:** Position fixes, collision avoidance
3. **Mission-critical:** Task updates, sensor alerts
4. **Monitoring:** Status, telemetry
5. **Housekeeping:** Logs, diagnostics

Lower-priority messages should be queued and delayed (or dropped) when the channel is congested.

## Bandwidth Budgeting

### Calculating a Communication Budget

For each vehicle in a multi-vehicle system:

1. **Identify all required messages** — What must be exchanged for the mission to succeed?
2. **Estimate message sizes** — How many bytes per message?
3. **Estimate message rates** — How often must each message be sent?
4. **Calculate total bandwidth** — Sum of (size × rate) for all messages
5. **Compare to available bandwidth** — Must be less than available bandwidth with margin for retransmission

**Retransmission overhead:** Acoustic links have high packet loss rates (10–30% in challenging conditions). ARQ (automatic repeat request) protocols can multiply effective bandwidth requirement by 1.3–2×.

### Per-Vehicle Allocation in Multi-Vehicle Systems

Total acoustic bandwidth must be shared among all vehicles. With N vehicles:

- Average per-vehicle bandwidth ≈ total bandwidth / N
- Critical vehicles (lead, emergency) may be allocated higher priority

## Optical Communication Tradeoffs

Optical modems provide high bandwidth (100 Mbps+) but only at very short ranges (<100m in clear water, much less in turbid water):

- **Suitable for:** Docking stations, short-range vehicle-to-vehicle, AUV-to-lander
- **Not suitable for:** Long-range coordination, operational-scale multi-vehicle systems

The latency of optical links is negligible — light travels 2×10⁸ m/s in water, giving <1 μs RTT at 100m range.

## Satellite and Radio Links (Surface)

For vehicles that can surface:

- **Iridium satellite:** Global coverage; ~2.4 kbps data (SBD messages) to 1 Mbps (Iridium NEXT terminals); latency ~1s
- **WiFi/4G/5G:** When in range; latency <100ms; bandwidth 1–1000 Mbps
- **VHF/UHF radio:** Short range (line-of-sight); low bandwidth; negligible latency

Surfacing to communicate (scheduled or triggered) is a valid design pattern for AUVs when acoustic bandwidth is insufficient.

## Related Topics

- [Communication Systems](/swarm-systems/communications/)
- [Multi-Vehicle Coordination](/swarm-systems/coordination/)
- [Loss-of-Comms Behavior](/swarm-systems/loss-of-comms/)
- [Graceful Degradation](/swarm-systems/degradation/)
- [Control Frameworks](/subsea-robotics/control-frameworks/)
