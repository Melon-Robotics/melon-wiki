+++
title = 'Control Frameworks'
description = 'Control architectures for ROVs and AUVs: deliberative, reactive, and hybrid approaches'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Control Frameworks

The control framework of an autonomous or remotely operated vehicle defines how it translates goals, sensor inputs, and operator commands into actuator outputs. Different architectures make different tradeoffs between responsiveness, planning capability, safety, and complexity.

## Why This Exists

Choosing an inappropriate control architecture can make a vehicle unsafe (too slow to react to hazards), ineffective (unable to plan complex missions), or unpredictable (brittle in unexpected situations). Understanding the options and their tradeoffs is essential for designing and operating subsea vehicles safely.

## Who This Is For

- Engineers designing vehicle control systems
- Operations managers evaluating AUV and ROV systems
- Pilots and operators understanding why vehicles behave as they do
- Safety engineers assessing autonomous system safety

## ROV Control Frameworks

### Manual Control

The baseline ROV mode: the pilot commands thrusters directly (or through a thin layer of rate control), and the vehicle responds. The pilot provides all sensing and decision-making.

- **Advantages:** Maximum operator flexibility; operator can respond to anything they observe
- **Disadvantages:** Highly skill-dependent; fatiguing in complex environments; no automatic safety functions

### Heading and Depth Hold

Auto-pilot functions that maintain a commanded heading and/or depth using feedback control:

- **Advantages:** Reduces pilot workload; maintains station in currents; improves sensor data quality
- **Disadvantages:** Still requires pilot for all other tasks; may conflict with environmental conditions

### Dynamic Positioning (DP)

DP systems maintain position and heading automatically in all three horizontal dimensions, using sensor fusion (USBL, DVL, heading) and thruster coordination:

- **Advantages:** Accurate station-keeping; frees pilot to focus on the task; essential for precision survey
- **Disadvantages:** Requires high-quality positioning sensors; can fail if sensors fail; may consume significant thrust

### Fully Supervised Autonomous Functions

Some ROV systems include autonomous functions (auto-tracking of a pipeline, auto-hover during inspection) with the pilot monitoring and overriding:

- **Advantages:** Consistent, precise execution of repetitive tasks
- **Disadvantages:** Autonomous functions have limited environmental adaptability; supervisor must remain vigilant

## AUV Control Architectures

### Deliberative (Sense-Plan-Act)

The deliberative architecture builds a world model, plans a sequence of actions to achieve the goal, and executes the plan:

1. **Sense** — Gather sensor data
2. **Plan** — Plan actions to achieve goals given current world state
3. **Act** — Execute the planned actions

- **Advantages:** Optimal or near-optimal planning; handles complex multi-step goals
- **Disadvantages:** Slow to react to unexpected events; world model may be stale or wrong; computationally expensive

### Reactive (Subsumption/Behaviour-Based)

Reactive architectures connect sensors directly to behaviours without maintaining a world model. Behaviours are prioritised and the highest-priority applicable behaviour controls the vehicle:

1. **Low-level behaviours** — Obstacle avoidance, collision prevention (highest priority)
2. **Mid-level behaviours** — Station-keeping, target tracking
3. **High-level behaviours** — Mission execution (lowest priority, can be pre-empted)

- **Advantages:** Fast reaction to hazards; robust to unexpected events; simple to implement and test
- **Disadvantages:** Cannot plan complex multi-step actions; may exhibit emergent behaviour that is difficult to predict

### Hybrid Architectures

Most practical AUV systems combine deliberative and reactive elements:

- **Reactive layer** — Handles immediate safety and environmental response (obstacle avoidance, emergency behaviours)
- **Deliberative layer** — Plans mission execution and handles complex sequencing

The reactive layer can pre-empt the deliberative layer when safety-critical situations arise.

### Model Predictive Control (MPC)

MPC uses a vehicle dynamics model to predict future behaviour and optimises control inputs over a receding horizon:

- **Advantages:** Handles constraints explicitly (thruster limits, current limits); optimal within prediction horizon
- **Disadvantages:** Computationally intensive; requires accurate vehicle model; prediction errors accumulate

## Safety Architecture Considerations

### Fail-Safe Behaviours

Safety-critical behaviours must be implemented in the highest-priority layer and must activate on component failure:

- **Loss of communication** → abort and return to surface (or defined safe point)
- **Low battery** → abort and return to surface
- **Sensor failure** → fall back to conservative navigation; surface if critical sensor lost
- **Obstacle detection** → stop and request guidance or execute avoidance

### Watchdog Systems

Independent hardware or software monitors that trigger fail-safe behaviour if the main control system stops responding:

- Must be independent of the main control system (cannot share the processor that might be frozen)
- Must be tested regularly
- Must act on a short timeout (seconds, not minutes)

### State Machines

Explicit state machines make vehicle behaviour predictable and auditable:

- Each state defines what the vehicle does and what transitions are possible
- Transitions require specific conditions to be met
- State is logged continuously to support incident investigation

## Related Topics

- [ROV Systems Overview](/subsea-robotics/rov-systems/)
- [AUV Platforms Overview](/subsea-robotics/auv-platforms/)
- [Failure Modes & Recovery](/subsea-robotics/failure-modes/)
- [Loss-of-Comms Behavior](/swarm-systems/loss-of-comms/)
- [Multi-Vehicle Coordination](/swarm-systems/coordination/)
- [Why Auditability Matters](/open-standards/auditability/)
