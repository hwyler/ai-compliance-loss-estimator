---
name: ai-compliance-loss-estimator
description: Quantifies financial compliance exposure for an AI use case (legal, regulatory, fraud, reputation and response costs) using jurisdiction-specific law, enforcement outcomes, litigation data, incident-frequency estimates and statistical loss modelling over a stated horizon. Activate whenever an AI use case needs legal, regulatory or compliance risk assessment, or whenever someone asks for scenarios ranked by expected loss.
metadata:
  version: '2026.10.13'
  precedence: This skill overrides any severity-by-likelihood, colour-rating or qualitative scoring skill if both are active. Reuse their escalation and research rules only where this skill says so.
---

# AI Compliance Loss Estimator

## 1. Purpose and activation

Identify the legal and compliance obligations of a specific AI use case and estimate the **financial losses** from non-compliance, enforcement, disputes, fraud, incidents and their follow-on effects.

- Quantify. Do **not** produce heatmaps, red/amber/green classes, qualitative ratings, or composite scores.
- Assess the actual use case: purpose, deployment context, data, affected persons, capabilities, autonomy, integrations, human oversight, controls, and the organisation's role (provider, deployer, or both).
- If essential information is missing, ask concise questions. Otherwise state assumptions and proceed. **Never invent** the organisation's revenue, incident history, exposure, control effectiveness or jurisdiction. When a number is needed and not supplied, use a clearly labelled **reference organisation** and show how results scale.
- Be concise and direct. Lead with the answer.

## 2. Compliance scope

"Compliance" covers legal obligations and the other losses that follow from failing them. Include only categories that are factually and legally relevant, and avoid assuming every law is breached or every breach is fined.

- AI-specific law (EU AI Act and national enforcement; US state and local AI laws).
- Data protection and privacy (GDPR, UK GDPR, CCPA/CPRA and others): unlawful processing, automated decision-making, transfers.
- Cybersecurity: breaches, unauthorised access, model-related attacks, AI-enabled attacks.
- Commercial litigation, contract, liability, indemnity, warranty, IP and confidentiality.
- Employment: discrimination, automated decision-making, monitoring.
- Antitrust, pricing, collusion, abuse of dominance.
- Consumer protection and misleading claims.
- **Fraud**: fraud against the organisation enabled or missed by the AI system (e.g. synthetic identities, deepfakes, insider access), and fraud losses to customers or counterparties.
- **Reputation loss**: only with a monetary method (see 4).
- **Response costs**: forensics, notification, counsel, regulator engagement, remediation.
- Cross-category exposure where one incident triggers several proceedings.

## 3. Jurisdictions and legal basis

Choose jurisdictions from the facts (provider and deployer location, affected persons, markets, territorial reach). For each material exposure:

1. Identify the law, competent authority, enforcement mechanism, and the **version and effective date** (application dates move; check them).
2. Separate statutory maximum, observed penalties and plausible case-specific outcomes.
3. Verify turnover-based limits, damages, remedies, limitation periods and national variation.
4. Count concurrent proceedings only where legally plausible; state whether penalties combine, exclude each other or are capped. **Never add statutory maxima across regimes.**
5. Cite authoritative sources: legislation, regulator guidance, judgments, enforcement decisions.

### Research method (before modelling)

1. Establish the prevailing position from primary text.
2. **Search adversarially** for contradicting authority using opposing terms.
3. Check recent doctrine and commentary (law-firm alerts, regulator statements).
4. **Recency check**: if the newest supporting authority is over 3 years old, search the last ~24 months, lower confidence, and flag it. Check amendments, delays and repeals of the legislation itself.

If a check finds a reversal or conflict, reflect it in the numbers and tell the user. Use connected legal research tools where available; otherwise use web search, mark authorities as unverified, and say so. **Never invent or reconstruct citations from memory.** Cite inline and list sources used.

## 4. Loss categories

Estimate **gross** and **net** loss, where data permit, for:

- Regulatory fines and administrative penalties
- Civil compensation, damages and restitution
- Settlements and contractual claims
- External counsel, litigation and defence costs
- Investigation, forensics, regulator response, remediation, corrective measures
- Business interruption, lost profits and other directly attributable losses
- **Fraud losses** (direct theft, payments, stolen data or access)
- **Reputation loss**: include only as a separate line, with an explicit monetary method (e.g. recruiting or acquisition cost uplift x volume x duration, or revenue-at-risk x measured churn) and stated evidence quality. Exclude it if no defensible method exists.
- Insurance recoveries, indemnities and other recoveries

Keep direct losses separate from indirect or hard-to-measure effects. Report gross (before recoveries) and net (after) separately. Model insurance limits, retentions, sub-limits, exclusions and notice conditions **only if policy data are provided**; otherwise report gross and say net was not estimated.

## 5. Quantitative method

1. **Define scenarios**: distinct loss events, each with trigger, legal basis, affected population and loss categories. Merge overlapping ones; keep fraud, breach, regulatory, litigation and reputation separate.
2. **Frequency**: annual event rate (Poisson or per-year probability) with start date from the law's effective date. Anchor on base rates (enforcement counts, filings, incident rates, breach notifications) and say how you adjusted for the organisation's exposure.
3. **Severity**: lognormal or other heavy-tailed distribution fitted to an observed low and high (e.g. smallest and largest comparable settlements or fines, median and 95th percentile of cost surveys). Cap at statutory limits where they bind (e.g. percent-of-turnover caps).
4. **Dependence**: model common-cause links (one public failure triggering several proceedings) or state that independence understates the tail.
5. **Simulate** (Monte Carlo, at least 50,000 runs) over the stated horizon (default 10 years). Report per scenario and in total:
   - expected loss over the horizon
   - low-high range from sensitivity (e.g. frequency x0.5 and x2, severity x0.7 and x1.5)
   - probability of at least one event
   - 95th percentile (and 99th for the total)
6. **Rank scenarios by expected loss, descending.**
7. State currency, discounting (default none), gross or net, and the reference inputs used.

Label the **evidence quality** of each input (primary data / survey / vendor claim / judgement) in words, not as a score. Do not present modelled output as more precise than the inputs.

## 6. Escalation (not a rating)

Independently of the numbers, recommend outside counsel and senior escalation when any of these is present: filed litigation, a regulator or law-enforcement inquiry, potential criminal exposure, securities-disclosure impact, board-level matters, a regulated data breach, a statutory notification or response deadline, or unsettled law where the position could set precedent. Flag litigation-hold and insurer-notice duties when proceedings are reasonably anticipated.

## 7. Output format (concise)

1. **Bottom line** (2-3 sentences): expected loss over the horizon, range, 95th percentile, top drivers.
2. **Ranked table**: scenario | expected loss | range | P(at least 1 event) | 95th percentile. Total row. Note that percentiles do not add.
3. **Evidence** (bullets): the data behind each input, with inline links and evidence quality.
4. **Assumptions and what would change the result**: the few inputs that move the total most, and what is excluded (insurance, correlation).
5. **Verification status**: which sources were primary, which were summaries, what was not checked.

Optional only if asked: mitigation value, expressed as change in expected loss against the control's cost, never as a colour or score.

## 8. Style rules

- Specific numbers with units; no adjectives in place of figures.
- Separate facts from assumptions; label judgement inputs as judgement.
- Do not state that a document is privileged on counsel's behalf; mark outputs as drafts for review by qualified professionals. You assist with compliance workflows and do not provide legal advice.