# AI Compliance Loss Estimator

Quantifies financial compliance exposure for AI use cases using jurisdiction-specific law, regulatory enforcement outcomes, litigation data, incident-frequency estimates, and statistical loss modelling. It ranks scenarios by expected financial loss over a defined time horizon, including relevant regulatory penalties, litigation and compensation, fraud, reputation loss where defensibly measurable, and incident response costs.

## What it does

The skill assesses a specific AI use case in its deployment and legal context, identifies relevant obligations and enforcement mechanisms, and estimates gross and, where supported by available data, net losses.

It is designed to:
- Identify applicable AI, privacy, cybersecurity, employment, consumer protection, contractual, intellectual property, competition, and other relevant legal regimes.
- Distinguish statutory maximum penalties from observed enforcement outcomes and plausible case-specific exposure.
- Define distinct loss scenarios, estimate event frequency and severity, and account for dependencies between events where evidence supports doing so.
- Rank scenarios by expected loss and report uncertainty ranges, event probabilities, and tail-loss estimates.
- Cite legal authorities and evidence, distinguish facts from assumptions, and state research limitations.

## Expected output

A concise assessment containing:
1. A bottom line with expected loss, uncertainty range, tail exposure, and main drivers.
2. A ranked scenario table.
3. Evidence and source citations, with evidence quality described in words.
4. Key assumptions, exclusions, and sensitivity drivers.
5. Verification status for the legal and empirical sources used.

## Important principles

- Quantitative loss estimates are used instead of heatmaps, traffic-light categories, or composite qualitative scores.
- Missing organisation-specific information must not be invented. Assumptions and reference-organisation inputs must be labelled.
- Reputation loss is included only when a defensible monetary method and supporting evidence are available.
- Insurance recoveries and net loss are estimated only when sufficient policy and recovery data are provided.
- Modelled estimates are not legal advice and should be reviewed by appropriately qualified professionals. Escalation to counsel and senior stakeholders is recommended for the triggers specified in the skill.

## Installation and use

Use `SKILL.md` as the skill definition in a compatible skill-enabled assistant environment. Activate it when assessing legal, regulatory, or compliance exposure for an AI use case, or when ranking compliance-risk scenarios by expected financial loss.

## Scope and methodology

The complete activation rules, legal research requirements, quantitative modelling method, escalation criteria, and required response format are defined in [SKILL.md](SKILL.md). That file preserves the original skill prompt.
