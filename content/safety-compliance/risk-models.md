+++
title = 'Operational Risk Models'
description = 'Risk assessment frameworks and quantitative risk models for subsea and diving operations'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Operational Risk Models

Risk models provide a structured way to estimate the likelihood and consequences of hazardous events. They translate qualitative hazard identification into quantifiable risk estimates that support decision-making, ALARP demonstration, and regulatory submissions.

## Why This Exists

Risk management requires more than identifying hazards — it requires understanding their significance. Risk models provide the common language for comparing risks, prioritising mitigations, and demonstrating compliance with ALARP and regulatory requirements.

## Who This Is For

- Safety engineers building and reviewing risk assessments
- Operations managers making risk-based decisions
- Regulators reviewing safety cases
- Project managers allocating resources for risk reduction

## Risk Fundamentals

### The Risk Equation

**Risk = Likelihood × Consequence**

Both dimensions must be assessed. A very unlikely event with catastrophic consequences may warrant more attention than a frequent event with minor consequences, depending on organisational risk tolerances.

### Risk Matrices

A risk matrix categorises risks by likelihood and consequence into risk bands:

**Likelihood scale (example):**
- 5 — Frequent: Expected to occur more than once per year
- 4 — Probable: Expected to occur once per year
- 3 — Occasional: May occur once per 10 years
- 2 — Remote: May occur once per 100 years
- 1 — Improbable: Unlikely to occur in system lifetime

**Consequence scale (example):**
- 5 — Catastrophic: Multiple fatalities
- 4 — Critical: Single fatality or permanent disability
- 3 — Marginal: Lost-time injury; significant environmental damage
- 2 — Negligible: Minor injury; minor environmental effect
- 1 — Minimal: No injury; no environmental effect

**Risk band = Likelihood rating × Consequence rating**

The risk band determines acceptability and required response.

## Qualitative vs Quantitative Risk Assessment

### Qualitative Risk Assessment (QRA-L)

Uses the risk matrix with expert judgement for likelihood and consequence ratings:

- **Faster and less resource-intensive** — Suitable for most operational decisions
- **Dependent on expert judgement** — Results reflect team experience and bias
- **Limited comparability** — Different teams may rate the same risk differently

### Quantitative Risk Assessment (QRA)

Uses historical data, fault trees, and event trees to calculate numerical risk estimates:

- **Provides numerical risk estimates** (e.g., 1×10⁻⁴ fatalities per year)
- **Enables comparison against numerical risk criteria** (e.g., individual risk criteria)
- **Resource-intensive** — Requires significant data and expertise
- **Appropriate for complex, high-consequence operations** — Major facilities, novel systems

## Common Risk Models for Subsea Operations

### Bow-Tie Analysis

Bow-tie diagrams link a central hazardous event (the "top event") to its causes (threats) on the left and consequences on the right. Barriers are identified on each side:

- **Prevention barriers** — Prevent threats from causing the top event
- **Recovery barriers** — Limit consequences after the top event occurs

Bow-ties are particularly useful for diving and subsea operations because they visualise the entire risk pathway clearly and support ALARP demonstration.

### Fault Tree Analysis (FTA)

FTA identifies combinations of failures that lead to an undesired top event:

- **Top-down analysis** — Start with the top event and work down to causes
- **Logic gates** — AND gates (all inputs required) and OR gates (any input sufficient)
- **Minimum cut sets** — Smallest combinations of failures that cause the top event
- **Useful for:** Complex systems with multiple independent failure modes

### Event Tree Analysis (ETA)

ETA traces sequences of events from an initiating event to final outcomes:

- **Forward analysis** — Start with the initiating event and trace forward
- **Branch points** — At each branch, success or failure of a safeguard is considered
- **Outcome probabilities** — Combined with FTA results to estimate consequence likelihood

## Individual Risk and Societal Risk

### Individual Risk

The probability that a specific individual in a defined role or location will die due to the operation per year:

- **Typical criterion for workers:** <1×10⁻³ per year (broadly acceptable); intolerable above 1×10⁻² per year
- **HSE guidance (UK):** Maximum tolerable individual risk for workers is 1×10⁻³ per year

### Societal Risk (F-N Curves)

Societal risk considers the risk to the public or workforce as a whole, accounting for both frequency and number of fatalities. Plotted as F-N curves (frequency vs. number of fatalities), these are compared against regulatory criteria lines.

## Residual Risk and ALARP

Risk models quantify risk both before and after controls are applied. The residual risk (after controls) must be demonstrated as ALARP — that all reasonably practicable controls have been applied.

See [ALARP Principles](/safety-compliance/alarp/) for the ALARP assessment process.

## Related Topics

- [ALARP Principles](/safety-compliance/alarp/)
- [Hazard Identification (HAZID/HAZOP)](/safety-compliance/hazard-identification/)
- [Responsibility Boundaries](/safety-compliance/responsibility/)
- [Regulatory Landscape Overview](/safety-compliance/regulatory-landscape/)
- [Dive Planning & Risk Assessment](/commercial-diving/dive-planning/)
