+++
title = 'Power Systems & Endurance'
description = 'Battery systems, power management, and endurance planning for subsea vehicles'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Power Systems & Endurance

Subsea vehicles carry their energy with them. Unlike surface vehicles that can refuel easily, an AUV or ROV (on battery backup) must complete its mission on the energy available at deployment. Power system design and endurance planning directly affect operational safety: a vehicle that runs out of power at depth is either lost or requires emergency response.

## Why This Exists

Power limitations constrain mission planning. Understanding battery capacity, consumption rates, and endurance margins is essential for planning missions that vehicles can complete safely with adequate reserve.

## Who This Is For

- AUV pilots and mission planners calculating endurance budgets
- Engineers designing vehicle power systems
- Operations managers planning multi-day deployments
- Safety engineers assessing mission risk

## Battery Technologies

### Lithium-Ion (Li-Ion)

The dominant technology for high-performance subsea vehicles:

- **Energy density:** 150–250 Wh/kg (mass); 300–700 Wh/L (volume)
- **Discharge characteristics:** Relatively flat discharge curve; capacity drops significantly at low temperatures
- **Safety:** Risk of thermal runaway if overcharged, overdischarged, or physically damaged
- **Cycle life:** 300–1000 cycles to 80% capacity retention

**Operational considerations:**
- Temperature affects capacity significantly — cold water (4°C) can reduce effective capacity by 20–40%
- Never discharge below manufacturer minimum voltage; deep discharge causes permanent damage
- Charge state monitoring must account for temperature compensation

### Lithium-Ion Polymer (LiPo)

Similar chemistry to Li-Ion with flexible form factor:

- **Advantages:** Can be shaped to fill irregular spaces in vehicle hull
- **Disadvantages:** More vulnerable to puncture damage; similar safety concerns to Li-Ion

### Primary Lithium Batteries

Non-rechargeable lithium batteries (lithium thionyl chloride, lithium manganese):

- **Energy density:** Significantly higher than rechargeable cells (up to 500 Wh/kg)
- **Shelf life:** Very long (10+ years)
- **Applications:** Long-endurance gliders, one-time-use autonomous vehicles
- **Disadvantages:** Cannot be recharged; disposal requirements

### Fuel Cells

Hydrogen-oxygen fuel cells offer higher energy density than batteries:

- **Energy density:** 1000+ Wh/kg of hydrogen (stored as metal hydride)
- **Applications:** Long-endurance AUVs where battery swaps are impractical
- **Disadvantages:** Complex hydrogen storage; safety considerations; limited commercial availability for subsea

### Tethered Power (ROVs)

Work-class ROVs receive power through the umbilical from the surface vessel:

- **Advantage:** No energy limitation; can operate indefinitely
- **Disadvantage:** Tether drag limits speed and range; umbilical failure cuts power immediately

## Power Consumption Modelling

### Propulsion

Thruster power is the dominant consumer for most vehicles:

- **Thrust vs. power:** Thrust increases roughly as power^(2/3) — doubling thrust requires ~2.5× power
- **Current effects:** Fighting a 1-knot current while making 2 knots SOG costs significantly more power than making 2 knots in still water
- **Practical implication:** Reduce speed to extend endurance; route missions to minimise counter-current transits

### Hotel Loads

Persistent power draws from navigation, communication, and payload systems:

- **Navigation sensors** (INS, DVL, USBL): 10–50W typically
- **Communication** (acoustic modems, satellite when surfaced): 1–100W depending on mode
- **Payload sensors** (sonar, camera): 10–500W depending on type

### Payload Power Budget

Sensor payloads can consume as much or more power than propulsion:

- Multibeam sonars: 50–200W
- Sub-bottom profilers: 100–1000W
- Cameras and lighting: 50–500W

Mission endurance cannot be calculated without accounting for payload power.

## Endurance Planning

### Energy Budget

For each mission:

1. **Calculate propulsion energy** — Distance ÷ speed × propulsion power at that speed
2. **Calculate hotel load energy** — Mission duration × hotel load power
3. **Calculate payload energy** — Payload-on time × payload power
4. **Sum total energy** — Propulsion + hotel + payload
5. **Apply reserve margin** — Total energy × (1 + reserve factor)
6. **Compare to available capacity** — Total with reserve must not exceed battery capacity at expected temperature

**Reserve margin:** A minimum 20% reserve is common practice; higher for longer or riskier missions. The reserve must account for unexpected events: longer transit due to unexpected currents, extended mission due to task complexity, contingency power for emergency surfacing.

### Abort Thresholds

Define explicit battery level thresholds that trigger mission abort:

- **Warning threshold** — Alert at 40% remaining; complete current task and return
- **Abort threshold** — Abort at 25% remaining; return to surface immediately
- **Emergency threshold** — Emergency surface at 15% remaining (sufficient for emergency ascent and surface positioning)

These thresholds must be implemented in the vehicle's control system, not just in the mission plan.

## Related Topics

- [AUV Platforms Overview](/subsea-robotics/auv-platforms/)
- [ROV Systems Overview](/subsea-robotics/rov-systems/)
- [Failure Modes & Recovery](/subsea-robotics/failure-modes/)
- [Control Frameworks](/subsea-robotics/control-frameworks/)
- [Loss-of-Comms Behavior](/swarm-systems/loss-of-comms/)
