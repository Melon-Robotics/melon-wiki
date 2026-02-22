+++
title = 'Physics vs Control Realism'
description = 'Tradeoffs between physics fidelity and control system realism in subsea simulation'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Physics vs Control Realism

Building a simulator involves fundamental tradeoffs: a system that models physics perfectly may not run fast enough for real-time training; a simplified physics model may not prepare operators for real conditions. Understanding these tradeoffs helps designers make informed choices about where fidelity matters and where simplification is acceptable.

## Why This Exists

Every simulation involves simplifications. Some simplifications matter enormously for training effectiveness; others are irrelevant. Knowing which is which allows resources to be directed toward the fidelity that counts, and prevents false confidence that "more realistic" always means "better training."

## Who This Is For

- Simulation designers building training systems
- Training managers evaluating simulation platforms
- Engineers integrating real hardware with simulation environments
- Researchers studying simulation effectiveness

## The Fidelity Spectrum

### Physics Fidelity

Physics fidelity refers to how accurately the simulation models the behaviour of physical systems:

- **High physics fidelity** — Accurately models fluid dynamics, structural mechanics, acoustic propagation
- **Low physics fidelity** — Uses simplified models (linear dynamics, lookup tables) that approximate behaviour

**Computational cost:** High-fidelity physics (e.g., computational fluid dynamics) is computationally expensive and may not run at real-time rates.

### Control System Fidelity

Control system fidelity refers to how accurately the simulation models the control software and hardware:

- **High control fidelity** — Runs actual vehicle control software against simulated sensor inputs
- **Low control fidelity** — Uses simplified models of vehicle response that may not match the real control system

**Testing value:** High control fidelity is essential for testing control system software before deployment. Low control fidelity is acceptable for training operator skills that do not depend on control system specifics.

## Where Fidelity Matters for Training

### Task-Dependent Fidelity Requirements

The required fidelity depends on what is being trained:

| Training Objective | Required Fidelity |
|-------------------|------------------|
| Procedure knowledge | Low — simulator only needs to present the right situations |
| Emergency decision-making | Medium — situation development must be plausible |
| Manual vehicle control skills | High — vehicle response must match reality |
| Fault diagnosis | High — failure modes must manifest as they do in reality |
| Environmental hazard recognition | High — environmental cues must be representative |

### The Negative Transfer Problem

Negative transfer occurs when simulation training teaches the wrong habits — habits that degrade performance in the real environment. Negative transfer is caused by:

- **Simulator controls that differ from real controls** — Operators learn control habits on the simulator that are wrong for the real system
- **Physics that differs significantly from reality** — Operators learn to anticipate vehicle response that does not match real behaviour
- **Consequence-free failure** — Operators learn that they can recover from errors that are unrecoverable in reality

**Principle:** It is better to train with a lower-fidelity simulation that does not cause negative transfer than a high-fidelity simulation that teaches wrong habits for the wrong reasons.

## Hardware-in-the-Loop (HIL)

HIL simulation runs actual vehicle hardware (control electronics, actuator drivers) against a simulated environment. This provides:

- **Real control system behaviour** — Exactly the same response characteristics as the real vehicle
- **Real failure modes** — Hardware failures manifest as they do in deployment
- **Software validation** — Control software can be tested without deploying the vehicle

**Cost:** HIL requires procuring additional hardware and integrating it with the simulation environment. For high-value vehicles, this investment is typically justified.

## Software-in-the-Loop (SIL)

SIL runs the vehicle control software in simulation without physical hardware. This provides:

- **Control software testing** — Software bugs can be found without hardware
- **Faster iteration** — Easier to reset and re-run than HIL
- **Limited hardware validation** — Does not validate hardware implementation

## Physics Simplifications and Their Implications

### Simplified Hydrodynamics

Real vehicle hydrodynamics are nonlinear and coupled. Simplified models (linear drag, decoupled axes) are adequate for:

- High-level mission planning
- Operator training in stable conditions

Simplified models fail for:

- Training in strong currents or near seabed
- Control system design and tuning
- Fault behaviour in unusual attitudes

### Simplified Acoustic Models

Acoustic propagation in the ocean depends on the sound velocity profile, bathymetry, and sea state. Simplified models may not accurately represent:

- Multipath effects that cause ranging errors
- Communication blackout zones
- Sonar image artefacts

**Training implication:** Operators trained only on simplified acoustic models may not recognise or respond correctly to multipath-induced errors in real operations.

## Choosing the Right Level of Fidelity

A practical framework:

1. **Define training objectives** — What skills and knowledge must the training develop?
2. **Identify critical fidelity requirements** — Which aspects of the simulation must be realistic to achieve those objectives?
3. **Identify acceptable simplifications** — Which aspects can be simplified without affecting training effectiveness?
4. **Validate the training** — Measure training transfer to confirm the chosen fidelity is adequate

## Related Topics

- [Why Simulation Matters](/simulation-training/why-simulation/)
- [Confidence Calibration](/simulation-training/confidence/)
- [Digital Twins](/simulation-training/digital-twins/)
- [Pre-Mission Rehearsal](/simulation-training/rehearsal/)
