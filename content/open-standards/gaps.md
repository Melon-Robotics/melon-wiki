+++
title = 'Gaps in Current Standards'
description = 'Where existing standards fail to address modern subsea robotics, autonomy, and data integrity'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Gaps in Current Standards

Existing standards for subsea operations were developed primarily for human divers and remotely operated vehicles with continuous operator oversight. They do not adequately address autonomous vehicles, multi-vehicle systems, AI-assisted decision-making, or modern data integrity requirements. This page identifies the most significant gaps.

## Why This Exists

Operating in regulatory grey areas carries risk — legal, safety, and reputational. Identifying gaps explicitly allows operators to develop interim mitigations, engage with standards bodies, and make informed decisions about where to apply conservative interpretations.

## Who This Is For

- Standards body participants and contributors
- Regulatory compliance teams identifying risks
- Engineers designing systems that must operate within (or despite) current frameworks
- Project managers scoping regulatory engagement for novel operations

## Gap 1: Autonomous Decision-Making

**What standards say:** Most standards require human decision-making for safety-critical actions. "The operator shall ensure…" assumes a human is making real-time decisions.

**What autonomous systems do:** AUVs make decisions — about route, speed, sensor operation, and emergency response — without real-time human input.

**Impact:** No standards specify how to validate autonomous decision logic, how to allocate liability for autonomous decisions, or how to certify autonomous safety behaviours.

**Interim approach:** Treat autonomous systems as tools that extend human capability; define the operating envelope within which the vehicle may act autonomously; require human authorisation for actions outside that envelope.

## Gap 2: Multi-Vehicle Coordination

**What standards say:** Regulations define safety zones and operating envelopes for individual vehicles. Interaction between vehicles is addressed only for collision avoidance at the maritime level.

**What swarm systems do:** Multiple vehicles operate in close proximity, share information, and make coordinated decisions. The safety of any one vehicle depends on the behaviour of others.

**Impact:** No standards address minimum separation requirements for cooperative subsea vehicles, coordination protocol requirements, or how to handle loss of one vehicle in a multi-vehicle mission.

**Interim approach:** Define mission-specific rules of encounter; require that each vehicle is safe to operate independently (no safety dependency on peer vehicles); document all coordination assumptions in the mission plan.

## Gap 3: Software Verification and Validation

**What standards say:** General safety management frameworks require that equipment is fit for purpose. Software is rarely addressed specifically, beyond requiring testing.

**What modern systems require:** AUVs and autonomous systems depend on complex software stacks. Failure modes in software are not analogous to hardware failures. Software can fail in emergent, unanticipated ways.

**Impact:** No standards specify software development lifecycle requirements, testing coverage expectations, or how to handle software updates to deployed systems.

**Interim approach:** Apply aerospace or automotive software standards (DO-178C, ISO 26262) by analogy; maintain software version traceability; require controlled update processes for deployed vehicles.

## Gap 4: Data Integrity and Provenance

**What standards say:** Operational records must be maintained. Formats and content are sometimes specified for specific industries (diving logs, survey records).

**What modern operations produce:** Large volumes of sensor data from multiple systems, processed through complex pipelines, stored in distributed systems. The lineage from raw measurement to delivered data product is rarely documented systematically.

**Impact:** Data used for safety decisions, regulatory submissions, and legal proceedings may not be demonstrably reliable. Data integrity cannot be audited retrospectively.

**Interim approach:** Implement data provenance tracking as described in [Data Provenance & Chain-of-Custody](/ocean-data/provenance/); apply audit log requirements from [Audit Logs & Immutability](/ocean-data/audit-logs/).

## Gap 5: Communication Loss Handling

**What standards say:** Emergency procedures require that operations can be halted. The implicit assumption is that communication with the operating system is always available.

**What autonomous systems experience:** Communication loss is an expected operational condition for AUVs operating at range or depth. Autonomous systems must handle communication loss safely without human intervention.

**Impact:** No standards specify what behaviour is required of an autonomous system during communication loss, how long a vehicle may operate without communication before mission abort is required, or how communication loss events must be logged.

**Interim approach:** Define explicit loss-of-comms behaviours for each mission type; require that vehicles default to a safe state on communication loss; log all communication loss events with duration and vehicle state.

## Gap 6: AI and Machine Learning

**What standards say:** Decision systems must be reliable and verifiable. Traditional engineering standards assume deterministic systems.

**What ML-based systems do:** Learn from data; may behave differently on data outside their training distribution; cannot always explain decisions.

**Impact:** No standards address how to validate ML models for safety-critical applications, what training data requirements apply, how to handle model drift, or how to audit ML-based decisions.

**Interim approach:** Treat ML as advisory only; require human authorisation for safety-critical actions recommended by ML; maintain training data and model version records; monitor for performance degradation.

## Related Topics

- [Why Auditability Matters](/open-standards/auditability/)
- [Autonomy Challenges & Legacy Assumptions](/open-standards/autonomy-challenges/)
- [Open Problems in Subsea Operations](/open-standards/open-problems/)
- [Regulatory Landscape Overview](/safety-compliance/regulatory-landscape/)
