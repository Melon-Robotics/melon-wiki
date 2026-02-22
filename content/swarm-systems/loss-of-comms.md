+++
title = 'Loss-of-Comms Behavior'
description = 'Safe behavior protocols for autonomous vehicles when communication with the surface is lost'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Loss-of-Comms Behavior

Loss of communication between a subsea vehicle and its operators is not an edge case — it is an expected operational condition. Acoustic communication links fail due to multipath, range, biological noise, and interference. Every autonomous vehicle must have a defined, tested, and reliable loss-of-comms (LOC) behavior that keeps the vehicle and its environment safe without operator input.

## Why This Exists

A vehicle without a defined LOC behavior is unpredictable. Operators cannot rely on the vehicle to behave safely if they lose contact. Regulators increasingly require explicit LOC behavior definitions for autonomous vehicles. Without it, vehicles should not be deployed.

## Who This Is For

- Engineers designing AUV and autonomous system control software
- Mission planners defining operational parameters and abort criteria
- Safety engineers reviewing autonomous system safety cases
- Operations managers approving autonomous vehicle deployments

## When Loss of Comms Occurs

### Detection

The vehicle must detect communication loss reliably and promptly:

- **Heartbeat monitoring** — Surface system sends periodic heartbeat messages; vehicle enters LOC state if no heartbeat received within the timeout window
- **Acoustic ping monitoring** — Vehicle listens for scheduled acoustic pings; absence triggers LOC state
- **Timeout threshold** — The timeout should be long enough to avoid false triggers from temporary acoustic shadowing, but short enough to respond promptly

**Typical timeouts:** 60–300 seconds for long-range AUVs; shorter for operations near infrastructure.

### Distinguishing Scenarios

Communication loss can occur because:

1. **Vehicle is in acoustic shadow** — Terrain blocks the acoustic path; may clear as vehicle moves
2. **Modem failure** — Hardware or software failure in acoustic modem
3. **Surface system failure** — Surface operator station or topside modem has failed
4. **Vehicle is in an unexpected location** — Outside planned communication range
5. **Environmental interference** — Shipping noise, biological noise, multipath

The LOC behavior cannot know which scenario it is in. It must be safe in all of them.

## LOC Behavior Design

### Core Principles

1. **Safety first** — LOC behavior must prioritise avoiding harm over mission completion
2. **Conservative** — In uncertainty, choose the more conservative action
3. **Deterministic** — LOC behavior must be predictable and testable
4. **Independent** — LOC behavior must not depend on communication to execute
5. **Tested** — LOC behavior must be explicitly tested before operational deployment

### Common LOC Behavior Patterns

#### Immediate Surface

Vehicle aborts current task and ascends to the surface immediately:

- **Advantages:** Simple; brings vehicle to where it can be found and recovered; enables satellite/RF communication
- **Disadvantages:** May interrupt a time-critical task; may surface in an unsafe location (vessel traffic, installation)
- **Suitable for:** Operations where surfacing is always safe; short-mission AUVs with low endurance

#### Hold Position (Hover)

Vehicle stops and holds position for a defined timeout:

- **Advantages:** Gives temporary communication loss time to clear; does not interrupt mission
- **Disadvantages:** Expends battery holding station; requires hovering capability; if communication does not clear, must transition to another LOC behavior
- **Suitable for:** Hover-capable vehicles; short expected LOC durations

#### Continue Mission with Scheduled Surface

Vehicle continues executing its pre-planned mission and surfaces at a scheduled time or position to re-establish communication:

- **Advantages:** Mission continues; communication recovery point is planned and known
- **Disadvantages:** Vehicle continues without oversight for an extended period; mission must be safe to execute autonomously
- **Suitable for:** Survey AUVs with collision-free pre-planned lanes; well-characterised environments

#### Abort and Return to Datum

Vehicle aborts the current mission and navigates to a pre-defined datum point (surface or subsurface):

- **Advantages:** Vehicle returns to a known, planned location; recovery is straightforward
- **Disadvantages:** Mission is lost; return navigation requires reliable positioning
- **Suitable for:** When mission continuation without communication is unacceptably risky

### LOC Behavior State Machine

LOC behavior should be implemented as an explicit state machine:

```
[COMMS OK] → [COMMS LOST (t < warn_timeout)] → [COMMS LOST (t < abort_timeout)]
           → [LOC BEHAVIOR ACTIVE] → [COMMS RESTORED] → [COMMS OK]
                                   → [MISSION COMPLETE] → [SURFACE/RECOVERY]
```

Each state has defined entry conditions, actions, and exit conditions.

## Hazard-Specific LOC Behaviors

### LOC Near Infrastructure

Near offshore installations, pipelines, or other vehicles:

- Immediate surface or hold position — do not continue moving near infrastructure without oversight
- Maximum safe hold time may be short (battery, current drift)

### LOC During Intervention Tasks

If the vehicle is performing a contact task (holding against a structure, operating a tool):

- Immediately release contact and back away
- Then apply standard LOC behavior
- Never hold contact position without operator oversight

### LOC for Multi-Vehicle Systems

In a multi-vehicle fleet where each vehicle can communicate with peers:

- Peer vehicles can relay abort commands from the surface
- Peer awareness of LOC state allows coordinated response
- Each vehicle must still have an independent LOC behavior if peer communication also fails

## Operator Interface for LOC

### Pre-Mission LOC Configuration

Operators must explicitly configure and confirm LOC behavior before each mission:

- LOC behavior type
- Communication timeout
- Abort datum (if applicable)
- Maximum hold time before surfacing

### LOC Event Notification

When LOC is detected by the surface system:

- Immediate alert to operators
- Clear indication of last known vehicle position and state
- LOC timer displayed so operators know how long until LOC behavior activates
- Recovery guidance based on vehicle LOC configuration

### Post-LOC Debriefing

After any LOC event (whether the vehicle recovered communication or executed LOC behavior):

- Log review: what was the vehicle doing when communication was lost?
- Root cause investigation: why did communication fail?
- LOC behavior review: did the vehicle execute LOC behavior correctly?
- Procedure update if LOC was caused by a systematic issue

## Testing LOC Behavior

LOC behavior that has never been tested is not LOC behavior — it is untested software that may or may not work when needed.

**Required testing:**
- Bench test: simulate communication loss and verify state machine transitions
- Pool test: verify LOC behavior in a controlled environment
- Field test (shallow): verify LOC behavior in realistic acoustic conditions before deep deployment

**Test each scenario:** Complete communication loss, gradual degradation, intermittent communication, communication loss during intervention tasks.

## Related Topics

- [Communication Systems](/swarm-systems/communications/)
- [Multi-Vehicle Coordination](/swarm-systems/coordination/)
- [Latency & Bandwidth Tradeoffs](/swarm-systems/latency-bandwidth/)
- [Graceful Degradation](/swarm-systems/degradation/)
- [Failure Modes & Recovery](/subsea-robotics/failure-modes/)
- [Autonomy Challenges & Legacy Assumptions](/open-standards/autonomy-challenges/)
