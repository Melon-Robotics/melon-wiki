+++
title = 'Autonomy Challenges & Legacy Assumptions'
description = 'Why autonomous subsea systems challenge legacy regulatory and operational assumptions'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Autonomy Challenges & Legacy Assumptions

Autonomous subsea systems operate in ways that existing regulatory frameworks were not designed to accommodate. Rules written for human divers, remotely operated vehicles with continuous operator control, or surface vessels with crews do not map cleanly onto systems that make independent decisions in real time. This page examines where legacy assumptions break down and what that means for operations, liability, and standards development.

## Why This Exists

Deploying autonomous systems without understanding the gaps in applicable frameworks creates legal, regulatory, and operational risk. Organisations must identify which assumptions underlie their regulatory compliance posture and whether those assumptions still hold when the system acts autonomously.

## Who This Is For

- Engineers designing autonomous subsea systems
- Legal and compliance teams reviewing regulatory applicability
- Standards bodies developing new frameworks
- Project managers identifying regulatory risks before deployment

## What Makes Autonomy Different

### Continuous Human Control Assumption

Most existing regulations for subsea vehicles assume a human operator is continuously monitoring and controlling the vehicle. Regulations specify:

- "The operator shall ensure…" — Who is the operator of an AUV completing a long-duration mission?
- "The pilot shall maintain…" — An autonomous vehicle has no pilot
- Response time requirements — An AUV operating beyond acoustic communication range cannot respond to real-time commands

**Gap:** Regulations that specify continuous operator control are unenforceable for, and inapplicable to, truly autonomous systems.

### Defined Operating Area Assumption

ROV regulations assume the vehicle operates in a defined, known, and cleared area within the umbilical's reach. AUVs may traverse large areas including:

- Regions not cleared for operations
- Areas with unknown hazards
- Zones where other operations are underway

**Gap:** Safe area definitions and exclusion zones designed for tethered operations do not account for autonomous navigation through variable terrain.

### Immediate Abort Capability Assumption

Emergency procedures in existing frameworks assume operations can be halted immediately on command. An AUV:

- May be beyond acoustic communication range
- May be executing a manoeuvre that cannot be safely interrupted
- May experience communication loss at a critical moment

**Gap:** Emergency stop requirements presuppose communication that autonomous systems cannot guarantee.

## Liability and Accountability Gaps

### Distributed Decision-Making

When an autonomous system makes a decision that results in an incident, attributing responsibility is complex:

- **Designer** — Did the system behave as specified?
- **Operator** — Was the mission planned appropriately?
- **Programmer** — Was the decision logic correct?
- **Certifier** — Was the system properly assessed before deployment?

Existing liability frameworks typically assign responsibility to an operator/employer. They do not describe how to assign liability when the decision was made by an algorithm.

### Software as Evidence

If an autonomous vehicle is involved in an incident, the software state at the time of the incident is critical evidence. This requires:

- Logging of all autonomous decisions with sufficient context to reconstruct the decision process
- Version control and immutable deployment records
- Black-box equivalent capabilities for autonomous vehicles

See [Why Auditability Matters](/open-standards/auditability/) for the logging requirements that follow from this.

## Legacy Assumptions in Standards

### Manned Submersible Rules Applied to AUVs

Some regulators apply manned submersible rules to AUVs because no AUV-specific rules exist. This creates:

- Over-specified requirements (life support systems for a vehicle with no crew)
- Under-specified requirements (no guidance on autonomous decision-making)
- Arbitrary interpretations that vary by jurisdiction and inspector

### ROV Rules Applied to AUVs

ROV rules typically require:

- Continuous surface monitoring
- Umbilical as a physical lifeline
- Defined safe areas matching the umbilical radius

None of these translate to AUV operations. Applying ROV rules to AUVs either prevents AUV operations entirely or forces fictitious compliance.

## Paths Forward

### New Regulatory Categories

Effective frameworks will likely need separate regulatory categories for:

- Fully supervised ROVs (existing frameworks apply)
- Supervised AUVs (periodic communication required)
- Extended autonomous AUVs (pre-mission approval model)
- Persistent autonomous systems (continuous environmental monitoring)

### Performance-Based vs Prescriptive Standards

Prescriptive standards (do X, use Y) cannot anticipate autonomous system designs. Performance-based standards (achieve outcome Z, demonstrate how) allow innovation while maintaining safety objectives. The challenge is defining measurable performance criteria for autonomous behaviour.

## Related Topics

- [Why Auditability Matters](/open-standards/auditability/)
- [Gaps in Current Standards](/open-standards/gaps/)
- [Open Problems in Subsea Operations](/open-standards/open-problems/)
- [Failure Modes & Recovery](/subsea-robotics/failure-modes/)
- [Loss-of-Comms Behavior](/swarm-systems/loss-of-comms/)
