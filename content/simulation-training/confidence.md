+++
title = 'Confidence Calibration'
description = 'Measuring and improving the match between simulation performance and real-world capability'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Confidence Calibration

Confidence calibration is the process of measuring whether operator confidence in their abilities matches their actual performance. In simulation-based training, poorly calibrated confidence is a serious hazard: operators who are overconfident will take risks they are not equipped to handle; operators who are underconfident will hesitate when decisive action is needed.

## Why This Exists

Simulation training creates a risk that is not present in apprenticeship-based training: the trainee may perform well in simulation without that performance transferring to the real environment. If trainees exit training believing they are more capable than they are, the training has created a hazard rather than eliminating one.

## Who This Is For

- Training designers building simulation curricula
- Instructors assessing trainee readiness
- Operations managers making deployment decisions
- Safety officers reviewing training programme effectiveness

## What Is Confidence Calibration?

A well-calibrated operator:

- Correctly identifies situations they can handle competently
- Correctly identifies situations that exceed their current capability
- Knows when to ask for assistance or defer to more experienced colleagues
- Adjusts confidence appropriately as experience accumulates

**Overconfidence:** Performance is worse than the operator believes. This is more dangerous — the operator takes on situations they cannot handle safely.

**Underconfidence:** Performance is better than the operator believes. This is less dangerous but reduces operational efficiency and may prevent deployment of a competent operator.

## Measuring Confidence Calibration

### Self-Assessment vs. Objective Performance

Calibration is measured by comparing:

1. **Subjective confidence** — How certain is the operator that they can perform a task correctly?
2. **Objective performance** — How well do they actually perform the task?

If an operator says "I'm 90% confident I can complete this task" and completes it correctly 90% of the time across many trials, they are well-calibrated for that task.

### Calibration Methods

**Scenario-based assessment:** Present the operator with scenarios of varying difficulty. Before each, ask for confidence rating. After each, assess performance. Plot confidence vs. performance.

**Knowledge questions:** Present questions about procedures, limits, and emergency actions. Ask for confidence in each answer. Score the answers. Compare.

**Judgment tasks:** Ask operators to assess whether a simulated situation is within limits. Compare judgments to correct answers.

## Factors That Distort Confidence

### Simulator Fidelity Gaps

If the simulator is easier than reality (smoother controls, cleaner sensor data, more forgiving physics), operators may perform well in simulation without real capability. They exit training overconfident.

**Mitigation:** Introduce realistic noise, failure modes, and environmental variability in simulation. See [Physics vs Control Realism](/simulation-training/realism-tradeoffs/).

### Lack of Failure Consequences

In simulation, failure is safe. This can reduce the psychological pressure that affects real performance. Operators may perform better in simulation than they would in a real emergency.

**Mitigation:** Structured debriefs that emphasise what would have happened in reality; progressive assessment of performance under simulated pressure.

### Instructor Feedback Effects

Positive instructor feedback can inflate confidence. Critical feedback without performance data can deflate it unnecessarily.

**Mitigation:** Feedback should be based on objective performance metrics, not instructor impression. Distinguish between praise for effort (appropriate) and claims about competence (must be evidence-based).

## Calibration in Training Programmes

### Entry Assessment

Assess baseline confidence and performance at programme entry:

- Identifies trainees with prior experience that may or may not match their confidence
- Sets a baseline for measuring programme effectiveness

### Progressive Calibration Checkpoints

Throughout training:

- Regular calibration assessments as capability is built
- Trainees should see their confidence and performance data together
- Instructors should intervene when significant miscalibration is detected

### Certification Readiness Assessment

Before certification:

- Full calibration assessment across the scope of the certification
- Trainees must demonstrate not just performance but appropriate confidence in that performance
- Significant overconfidence should delay certification even if raw performance meets criteria

## Calibration for New Technology

When operators are transitioning to new systems (e.g., from manual ROV operation to autonomy-assisted operation), confidence calibration is especially important:

- Prior experience may create false confidence about new system behaviour
- New failure modes may not be intuited from old experience
- Performance in the new system must be specifically assessed before deployment

## Related Topics

- [Why Simulation Matters](/simulation-training/why-simulation/)
- [Physics vs Control Realism](/simulation-training/realism-tradeoffs/)
- [Pre-Mission Rehearsal](/simulation-training/rehearsal/)
- [Digital Twins](/simulation-training/digital-twins/)
- [Human Factors in Diving Operations](/commercial-diving/human-factors/)
