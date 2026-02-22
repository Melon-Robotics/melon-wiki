+++
title = 'Graceful Degradation'
description = 'Designing subsea systems to degrade safely when components fail'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Graceful Degradation

Graceful degradation means that when components fail, the system continues to operate safely at reduced capability rather than failing completely or unsafely. For subsea systems — where recovery is expensive and immediate intervention is impossible — graceful degradation is not optional; it is a fundamental design requirement.

## Why This Exists

Subsea systems face harsh environments and operate far from support. Component failures are inevitable. The question is not whether failures will occur but whether the system degrades gracefully when they do. Ungraceful degradation — catastrophic failure, unsafe behaviour, or silent data corruption — is the alternative.

## Who This Is For

- Engineers designing subsea vehicle and system architectures
- Safety engineers assessing system failure modes
- Operations managers planning for contingency scenarios
- Mission planners setting abort criteria

## What Graceful Degradation Means

A system degrades gracefully when:

1. **Failures are detected** — The system knows a component has failed
2. **The failure mode is safe** — The system does not do anything dangerous when the component fails
3. **Capability is reduced, not lost** — The system continues operating at reduced performance
4. **Operators are informed** — The failure and its impact are communicated
5. **Recovery is possible** — The system can be recovered without total mission abort

The opposite of graceful degradation is brittle failure: the system works perfectly until a single component fails, at which point it fails entirely or dangerously.

## Degradation Hierarchy

Design a degradation hierarchy for each critical capability:

### Navigation Example

| Mode | Available Systems | Position Accuracy |
|------|-----------------|------------------|
| Full | INS + DVL + USBL | Decimetre |
| DVL lost | INS + USBL (periodic) | 1–5m |
| USBL lost | INS + DVL | Grows over time (drift) |
| DVL + USBL lost | INS only | Degrades rapidly (minutes) |
| INS degraded | Dead reckoning from last fix | Poor, time-limited |
| All lost | Abort: surface for GPS fix | — |

Each step down reduces capability but maintains safe operation within defined limits.

### Propulsion Example

| Mode | Available Thrusters | Capability |
|------|-------------------|-----------|
| Full | All thrusters | Full maneuverability |
| One thruster failed | Remaining thrusters | Reduced, may have asymmetry |
| Two thrusters failed | Remaining thrusters | Significantly reduced; may abort |
| Critical thrusters failed | — | Abort: surface |

## Design Principles for Graceful Degradation

### Fault Detection and Isolation (FDI)

The system cannot degrade gracefully if it cannot detect its own failures:

- **Built-in test** — Components self-test on startup and continuously during operation
- **Redundant sensors** — Cross-checking between sensors reveals failures
- **Plausibility checks** — System checks whether sensor readings are consistent with expectations
- **Watchdog timers** — Detect processor hangs and communication timeouts

A failure that goes undetected is more dangerous than a detected failure.

### Modular Architecture

Systems with modular, loosely coupled components fail more gracefully:

- A failed sensor does not crash the entire navigation system
- A failed communication module does not prevent thruster control
- Software failures in one module are contained and do not propagate

### Functional Priority

Not all functions are equally important. Assign priorities:

1. **Safety functions** (obstacle avoidance, emergency ascent) — Must work under all foreseeable conditions
2. **Mission-critical functions** (navigation, primary sensors) — Mission continues if these work; abort if they fail
3. **Mission-enhancing functions** (secondary sensors, optimisation) — Degrade gracefully without mission abort

When resources (power, processing) are constrained by a failure, lower-priority functions are shed first.

### Conservative Defaults

When a sensor or subsystem fails, default to the conservative interpretation:

- Unknown obstacle position → assume obstacle is present
- Unknown battery level → assume low battery
- Unknown communication state → assume communication lost

This is the "fail-safe" principle applied to uncertain state.

## Communication Degradation

### Acoustic Modem Partial Failure

Acoustic modems have multiple failure modes:

- **Complete loss** — No communication possible; trigger loss-of-comms procedure
- **Reduced range** — Communication works at short range only; adapt mission
- **High error rate** — Retransmission overhead reduces effective bandwidth; reduce communication rate

### Prioritised Message Queuing

When bandwidth is reduced, prioritise critical messages:

1. Safety-critical (abort, position, emergency)
2. Mission-critical (navigation aiding, task updates)
3. Telemetry (status, sensor data)
4. Housekeeping (logging, diagnostics)

Drop housekeeping and telemetry before dropping mission-critical messages.

## Monitoring Degradation State

### System Health Dashboard

Operators must know the current degradation state in real time:

- Which components are operating nominally
- Which are degraded (with details of the degradation)
- Which have failed
- Current capability given the degradation state

### Degradation Logging

All degradation events must be logged with:

- Timestamp
- Component affected
- Nature of the failure/degradation
- System response (fallback mode activated)

This supports post-mission incident analysis and predictive maintenance.

## Related Topics

- [Communication Systems](/swarm-systems/communications/)
- [Loss-of-Comms Behavior](/swarm-systems/loss-of-comms/)
- [Failure Modes & Recovery](/subsea-robotics/failure-modes/)
- [Control Frameworks](/subsea-robotics/control-frameworks/)
- [Multi-Vehicle Coordination](/swarm-systems/coordination/)
