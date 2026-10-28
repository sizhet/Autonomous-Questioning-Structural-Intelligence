# TESTABLE HYPOTHESES
## Autonomous Questioning Structural Intelligence (AQSI)

**Version:** 1.0.0  
**Status:** Proposed, falsifiable research hypotheses; no experiments reported  
**Repository:** `Autonomous-Questioning-Structural-Intelligence`  
**Companions:** [OPEN-QUESTIONS.md](OPEN-QUESTIONS.md) · [VALIDATION-ROADMAP.md](VALIDATION-ROADMAP.md) · [FUTURE-DIRECTIONS.md](FUTURE-DIRECTIONS.md)

---

## 1. Purpose and epistemic status

AQSI proposes that a structured loop for discovering, evaluating, selecting, exploring, and relaying questions may produce more *independently verified research value per resource unit* than simpler question-generation workflows. This document converts that proposition into falsifiable tests. Every hypothesis below is **unverified**; suggested thresholds are illustrative design choices, not observed effects or guarantees.

The unit of evaluation is not the number of questions generated, model confidence, rhetorical novelty, or agreement among collaborating agents. It is an independently auditable outcome, such as a reproduced finding, a resolved uncertainty, a validated reusable method, or a downstream question that yields such an outcome. Null and adverse results must remain publishable and relayable.

## 2. Evaluation contract shared by all hypotheses

**Experimental units.** Use predefined research tasks or question families, sampled from at least two domains when cross-domain generality is claimed. Randomize at the task or independent question-family level; do not treat correlated descendants as independent observations.

**Primary outcome.** Verified research yield (VRY): the count or quality-weighted total of outcomes that pass a prespecified external verification rubric, divided by actual resource consumption (e.g., model-token cost, tool calls, investigator time, or a common budget unit). Report raw numerator and denominator separately; avoid a single opaque composite.

**Secondary outcomes.** Independent expert usefulness; calibration (Brier score or reliability error for explicitly defined binary outcomes); question diversity; downstream verified relay value; time-to-first-verification; false-positive rate; coverage of neglected topics; and safety/policy violations.

**Controls.** Match model family, tool access, information cutoff, human support, budget, evaluation rubric, and exploration time. Include an LLM-only baseline and a random or stratified selection baseline where feasible. Where an ablation changes computational cost, compare both at equal candidate counts and equal total budgets.

**Pre-registration.** Before outcome inspection, freeze datasets or rolling evaluation windows, allocation rules, stopping criteria, target effect sizes, analysis plan, and evaluation authority. Preregister a minimum practically important difference (MPID) for each primary endpoint. No arbitrary numerical MPID in this document should be interpreted as validated.

**Independence and leakage.** Blind outcome assessors to method when feasible; isolate held-out tasks, domains, and temporal cohorts; audit duplicated prompts, paraphrases, shared sources, and leaked ground truth. Track provenance, UTN types, policy version, model version, and scorer version.

**Uncertainty.** Report confidence or credible intervals, sample sizes, domain-level heterogeneity, and all excluded or deferred questions. Distinguish absence of evidence from evidence of equivalence. Use multiple-comparison correction or hierarchical modeling for broad hypothesis families.

**Governance.** No experimental score authorizes external actions. All exploration follows SPEC-003 and SPEC-004, with human approval for consequential or restricted activities.

## 3. Hypothesis registry

Each entry defines a proposed mechanism, an operational test, a primary endpoint, a falsification or non-support condition, and a relevant research anchor. The notation `H-XXX` is stable for future evidence and counterevidence records.

### H-DISC-001 — Structural discovery adds value beyond fluent generation

**Hypothesis.** A combined gap/residual/association/relay discovery pipeline yields more externally verified findings per budget than LLM-only question generation.

**Proposed test.** Randomize comparable domain tasks to combined discovery or prompt-only discovery; hold exploration and evaluation fixed.

**Primary measurement.** VRY and verified question yield per 100 candidates.

**Non-support / falsification signal.** No positive MPID-sized gain under equal total budget, or gains disappear after independent verification.

**Research anchors.** AQSI-002; CASE-001.

### H-DISC-002 — Structure-first discovers complementary questions

**Hypothesis.** Structure-first generation produces verified useful questions not recovered by LLM-first generation under matched candidate budgets.

**Proposed test.** Compare structure-first, LLM-first, and their union on hidden gaps; deduplicate semantically before judging.

**Primary measurement.** Incremental independently verified unique questions.

**Non-support / falsification signal.** Union offers no incremental verified coverage after controlling for candidate count and review cost.

**Research anchors.** AQSI-002; AQSI-003.

### H-DISC-003 — Biomimetic channels are not merely labels

**Hypothesis.** Gap, residual, association, and relay channels contribute distinct, measurable discovery value.

**Proposed test.** Ablate one channel at a time with fixed compute and same candidate normalization.

**Primary measurement.** Marginal VRY and coverage of prespecified gap categories.

**Non-support / falsification signal.** Removing channels has no reliable effect or improves yield without a material coverage loss.

**Research anchors.** AQSI-002.

### H-INFL-001 — Multi-granularity scoring improves prioritization

**Hypothesis.** Typed concept, attribute, method, evidence, and residual relations predict verified downstream value better than concept-only similarity.

**Proposed test.** Train scorers on matched histories; evaluate on held-out question families and domains with equal feature budgets.

**Primary measurement.** Rank correlation with verified value; top-k VRY.

**Non-support / falsification signal.** No improvement over concept-only or text embedding baselines after leakage and complexity controls.

**Research anchors.** AQSI-003; SPEC-002.

### H-INFL-002 — Directional relationships matter

**Hypothesis.** Asymmetric influence estimates improve downstream relay prediction compared with forced symmetric matrices.

**Proposed test.** Compare directed and symmetrized versions of the same scoring model on temporally ordered question derivations.

**Primary measurement.** Held-out directional edge prediction and top-k downstream VRY.

**Non-support / falsification signal.** Directed representation adds no value or systematically predicts reversed causal order.

**Research anchors.** AQSI-003; AQSI-005.

### H-INFL-003 — Unknown is distinct from zero

**Hypothesis.** Explicit unknown-relation states improve calibration and exploration coverage over imputing all unmeasured relations as zero.

**Proposed test.** Randomly mask known relations during training and test; compare unknown-aware and zero-filled scorers.

**Primary measurement.** Calibration on masked edges and verified yield from exploration of unknown edges.

**Non-support / falsification signal.** Unknown-aware approach does not improve calibration or verified exploration return.

**Research anchors.** AQSI-003; SPEC-002.

### H-INFL-004 — Folding preserves useful provenance

**Hypothesis.** Evidence-aware multi-factor folding reduces double counting and improves calibrated selection versus untracked score aggregation.

**Proposed test.** Inject correlated evidence sources and compare provenance-aware versus naive aggregation.

**Primary measurement.** Calibration error and false-positive selection rate.

**Non-support / falsification signal.** Provenance-aware folding fails to reduce overconfidence or increases missed verified findings beyond MPID.

**Research anchors.** AQSI-003; SPEC-002.

### H-HIST-001 — History improves candidate screening

**Hypothesis.** Historical Question Intelligence reduces exploration waste without proportionally suppressing high-value novel questions.

**Proposed test.** Compare history-informed, no-history, and novelty-protected screening on temporal holdouts.

**Primary measurement.** VRY per budget and recall of independently verified high-value questions.

**Non-support / falsification signal.** Savings are absent or recall falls below a preregistered minimum.

**Research anchors.** AQSI-004; CASE-001.

### H-HIST-002 — Question Differential Trees aid reuse

**Hypothesis.** Core-plus-Delta question families improve retrieval and prediction compared with flat textual similarity.

**Proposed test.** Compare QDT retrieval with embedding and lexical baselines across controlled paraphrase and domain-shift sets.

**Primary measurement.** Top-k retrieval precision for genuinely transferable precedent and VRY.

**Non-support / falsification signal.** QDT offers no added verified transfer or costs outweigh its benefit.

**Research anchors.** AQSI-004; AQSI-009.

### H-HIST-003 — Negative histories are conditionally useful

**Hypothesis.** Preserving failed explorations with conditions and evidence reduces repeated unproductive investigations.

**Proposed test.** Run sequential cohorts with and without structured failure records; permit explicit revisit triggers.

**Primary measurement.** Redundant exploration cost and missed discoveries after context changes.

**Non-support / falsification signal.** No decrease in waste or unjustified suppression of valuable revisits.

**Research anchors.** AQSI-004; AQSI-007.

### H-HIST-004 — Delayed value changes rankings

**Hypothesis.** Including verified descendant value improves question ranking over immediate-outcome-only labels.

**Proposed test.** Use temporally split question lineages; compare short-horizon and preregistered long-horizon labels.

**Primary measurement.** Long-horizon VRY at equal cost.

**Non-support / falsification signal.** No improvement after discounting uncertain lineage attribution and duplicated credit.

**Research anchors.** AQSI-004; AQSI-007.

### H-PORT-001 — Portfolio selection beats single-score top-k

**Hypothesis.** Budgeted portfolio selection using complementarity and redundancy yields more verified discoveries than choosing the highest individual scores.

**Proposed test.** Randomize task batches to portfolio optimizer or greedy top-k under identical constraints.

**Primary measurement.** Portfolio-level VRY, diversity, and redundancy-adjusted outcomes.

**Non-support / falsification signal.** No gain or higher cost/complexity without verified improvement.

**Research anchors.** AQSI-005; CASE-003.

### H-PORT-002 — Goal-open influence has predictive utility

**Hypothesis.** Pairwise outgoing question influence predicts useful downstream research contributions without requiring a fixed target answer.

**Proposed test.** Compute S(q_i)=sum over j≠i I(q_i→q_j); compare with novelty, centrality, and expert rankings on future outcomes.

**Primary measurement.** Out-of-sample descendant verified yield and ranking calibration.

**Non-support / falsification signal.** Influence scores correlate only with graph size, verbosity, or generated question volume.

**Research anchors.** AQSI-005.

### H-PORT-003 — Exploration reserve prevents lock-in

**Hypothesis.** A protected exploratory budget reduces long-run discovery loss from history-biased selection.

**Proposed test.** Compare zero, modest, and larger exploration reserves over sequential rounds; predefine horizon.

**Primary measurement.** Long-horizon VRY and discovery of previously low-scored families.

**Non-support / falsification signal.** Reserve imposes cost without improved long-run yield or harms required safety coverage.

**Research anchors.** AQSI-005; EXT-001.

### H-UNIT-001 — Canonical Question Units improve reproducibility

**Hypothesis.** Stable typed Question Units with provenance outperform prompt-only records for reproducible exploration handoffs.

**Proposed test.** Have independent teams reproduce blinded research tasks from QU records or prompts, with equal preparation time.

**Primary measurement.** Successful reproduction and provenance completeness.

**Non-support / falsification signal.** No reproducibility gain or excessive authoring burden.

**Research anchors.** AQSI-006; SPEC-001.

### H-UNIT-002 — Contracts reduce unauthorized or ambiguous exploration

**Hypothesis.** Exploration contracts reduce policy violations and untraceable outcomes compared with informal agent instructions.

**Proposed test.** Conduct sandboxed conformance tests with adversarial and ambiguous cases; no real-world unsafe execution.

**Primary measurement.** Violation rate, audit completeness, and false refusal rate.

**Non-support / falsification signal.** Violation rate not reduced or benign research blocked excessively.

**Research anchors.** AQSI-006; SPEC-003; SPEC-004.

### H-RELAY-001 — Structured relay produces reusable knowledge

**Hypothesis.** Typed relay pieces improve independent downstream reuse over narrative-only handoffs.

**Proposed test.** Randomize research teams to structured relay or prose reports, blind downstream teams to origin.

**Primary measurement.** Verified reuse success and time to reproduce.

**Non-support / falsification signal.** No gain in independent reuse or unacceptable relay overhead.

**Research anchors.** AQSI-007; SPEC-003.

### H-RELAY-002 — Repeated execution contributes conditional information

**Hypothesis.** Recorded repeat experiments improve uncertainty estimates when repetitions differ in conditions or independently replicate observations.

**Proposed test.** Compare tracked repetitions, untracked repetitions, and independent replications; model evidence dependence explicitly.

**Primary measurement.** Calibration and reproducibility under drift.

**Non-support / falsification signal.** Tracked repetition adds no value, or correlated evidence is incorrectly counted as independent.

**Research anchors.** AQSI-007.

### H-RELAY-003 — Multi-agent discussion is not enough

**Hypothesis.** Multi-agent systems with explicit relay, independent verification, and counterevidence outperform discussion-only multi-agent workflows.

**Proposed test.** Hold agent count and budget fixed; ablate structured relay and verification.

**Primary measurement.** Verified VRY, error correction, and auditability.

**Non-support / falsification signal.** Only agreement or text volume rises; independently verified outcomes do not.

**Research anchors.** AQSI-007; CASE-003.

### H-XDOM-001 — UTN alignment improves transfer precision

**Hypothesis.** Typed UTN alignment reduces negative transfer compared with surface analogy or embedding-only matching.

**Proposed test.** Transfer questions between software CI and sensor anomaly settings using matched source histories.

**Primary measurement.** Verified transfer precision, negative transfer rate, and target-domain VRY.

**Non-support / falsification signal.** No gain after type-authoring cost or systematic false equivalence persists.

**Research anchors.** AQSI-009; CASE-002.

### H-XDOM-002 — Transferable parts outperform whole-domain equivalence

**Hypothesis.** Partial method/constraint/evidence mappings yield more valid transfer candidates than assuming global domain equivalence.

**Proposed test.** Compare part-level alignment with domain-level analogical matching on held-out mappings.

**Primary measurement.** Independently validated useful transfers per review hour.

**Non-support / falsification signal.** Part-level method adds no verified useful transfers or worsens semantic drift.

**Research anchors.** AQSI-009.

### H-GOV-001 — Strategic guidance preserves tactical autonomy

**Hypothesis.** Human policy and resource constraints can improve mission relevance without specifying every research question.

**Proposed test.** Compare strategic policy-only, manual question lists, and unguided AQSI in a simulated funding program.

**Primary measurement.** Verified mission-relevant VRY, autonomy/diversity, and compliance.

**Non-support / falsification signal.** Guidance collapses diversity or fails to improve relevance under equal budget.

**Research anchors.** AQSI-008; SPEC-004; CASE-003.

### H-GOV-002 — Policy conformance remains stable across relay

**Hypothesis.** Policy and authorization checks prevent unauthorized scope expansion across cross-agent and cross-domain relay.

**Proposed test.** Red-team policy propagation with synthetic authority-conflict and escalation scenarios.

**Primary measurement.** Unauthorized execution attempts blocked; false positive blocks.

**Non-support / falsification signal.** Relay silently broadens authority or policy checks prevent legitimate work disproportionately.

**Research anchors.** AQSI-008; SPEC-004.

### H-META-001 — Meta-question discovery can identify repairable weaknesses

**Hypothesis.** Explicit meta-questions discover actionable defects in discovery/scoring pipelines more effectively than generic retrospective prompts.

**Proposed test.** Seed benchmark defects and compare meta-question workflow with conventional diagnostics.

**Primary measurement.** Verified defect discovery and corrected defect rate.

**Non-support / falsification signal.** No advantage after controlling for diagnostic budget and assessor effort.

**Research anchors.** EXT-001.

### H-COEV-001 — Cross-structural updates can yield joint benefit

**Hypothesis.** Governed co-evolution of AQSI and UTN/scoring structures improves held-out outcomes over independently frozen components.

**Proposed test.** Compare frozen, independently updated, and jointly proposed-but-approved structural updates with rollback.

**Primary measurement.** Held-out VRY, semantic compatibility, and regression rate.

**Non-support / falsification signal.** Joint changes show no net gain or cause uncontrolled compatibility regressions.

**Research anchors.** EXT-002.

### H-RSI-001 — Validated recursive updates outperform static pipeline

**Hypothesis.** A versioned, independently tested improvement loop yields sustained gains beyond a frozen AQSI pipeline.

**Proposed test.** Evaluate successive candidate updates on sealed future tasks; require approval and rollback criteria.

**Primary measurement.** Cumulative held-out VRY per resource and regression incidence.

**Non-support / falsification signal.** Improvements vanish on fresh tasks, are not reproducible, or reflect benchmark overfitting.

**Research anchors.** AQSI-010; EXT-003.

### H-BOUND-001 — Question volume is not a proxy for intelligence

**Hypothesis.** Increasing candidate generation alone fails to reliably predict verified research progress after controlling for budget and diversity.

**Proposed test.** Vary candidate volume while holding exploration and verification budgets fixed.

**Primary measurement.** Marginal verified yield per additional candidate.

**Non-support / falsification signal.** If volume alone reliably improves verified yield, this boundary hypothesis is not supported.

**Research anchors.** EXT-003.

## 4. Measurement and attribution rules

### 4.1 Verified research yield

For a preregistered study, define a verification indicator `v_k ∈ {0,1}` and a prespecified quality weight `w_k` for outcome `k`. One possible transparent metric is:

`VRY = (Σ_k w_k · v_k) / B`, where `B` is measured resource expenditure.

Report `Σ_k v_k`, `Σ_k w_k · v_k`, and `B` alongside VRY. Quality weights must be frozen before seeing treatment assignments; independent assessors should adjudicate contested outcomes. Report an unweighted analysis as a sensitivity check. Never award a verified outcome merely because an LLM judges its own answer correct.

### 4.2 Directed influence and downstream value

A proposed baseline influence score is `S(q_i) = Σ_{j ≠ i} I(q_i → q_j)`. This is a **selection heuristic**, not a measurement of scientific truth. Compare it to independently observed downstream outcomes. Normalize for graph size, missingness, question age, and candidate-generation exposure; prevent descendants from receiving multiple credits for the same verified finding.

### 4.3 Historical feedback and censored outcomes

A deferred, untested, or currently unanswerable question is **not** a negative outcome. Distinguish `failed_with_evidence`, `unresolved`, `not_selected`, `deferred_by_policy`, and `verified_success`. Account for selection bias because only explored questions yield ordinary outcome labels; use randomized audit exploration or suitable propensity methods when ethically and operationally appropriate.

### 4.4 Cross-domain generalization

Prespecify source and target domains. Test on target tasks not used to author UTN mappings or tune scorers. Record mapping confidence, unresolved type mismatches, domain-specific constraints, and negative transfers. A successful analogy is not a verified answer in the target domain.

### 4.5 Governance and safety

Measure compliance independently of research yield. A high-scoring question must not bypass an exploration contract. Record policy versions, delegated scopes, approvals, denials, overrides, and rollbacks; evaluate false refusals as well as missed violations.

## 5. Minimal experimental program

| Phase | Focus | Essential comparisons | Exit criterion |
|---|---|---|---|
| M0 | Single-domain questioning | LLM-only, random selection, AQSI core | Reproducible task set, stable contracts, no untracked outcomes |
| M1 | Historical and influence intelligence | No-history, concept-only, symmetric, full multi-granularity | Held-out improvement or informative null with cost accounting |
| M2 | Cross-domain and multi-agent relay | Surface analogy, prose handoff, typed UTN relay | Independently verified transfer/reuse with policy compliance |
| M3 | Meta-question and recursive updates | Frozen system, ablated updates, governed updates | Sustained sealed-test improvement with rollback and audit |

A phase can conclude with a well-characterized negative result; advancing phases is not evidence of improvement.

## 6. Priority and dependency map

- **Foundation:** H-UNIT-001, H-UNIT-002, H-INFL-003, H-GOV-002 establish record integrity, missingness semantics, and authorization.
- **Initial empirical core:** H-DISC-001, H-INFL-001, H-HIST-001, H-PORT-001 test whether AQSI beats simpler alternatives under fixed budgets.
- **Relay and transfer:** H-RELAY-001, H-RELAY-003, H-XDOM-001 require reliable provenance and independent adjudication.
- **Long-horizon:** H-HIST-004, H-PORT-003, H-COEV-001, H-RSI-001 require temporal holdouts and versioned updates.

This is a suggested dependency order, not an imposed research priority; strategic policy may allocate resources differently within authorized constraints.

## 7. Hypothesis evidence record template

```yaml
hypothesis_id: H-INFL-001
study_id: null
protocol_version: null
preregistration_uri: null
dataset_and_split: null
model_and_scorer_versions: []
policy_version: null
comparison_arms: []
resource_budget_definition: null
primary_metric: null
minimum_practically_important_difference: null
sample_size_plan: null
blinding_and_independence: null
results_uri: null
confidence_interval: null
costs_and_failures_uri: null
counterevidence_uri: null
status: proposed  # proposed | preregistered | running | supported | not_supported | inconclusive | superseded
reviewer_and_date: null
explicit_leftover: []
```

`Supported` means supported **under the specified protocol and population**, not established as a universal law. A null result should be classified as `not_supported` only when the design has adequate precision for the stated MPID; otherwise use `inconclusive`.

## 8. Threats to validity

1. **Goodhart effects:** optimizing question scores instead of independently verified outcomes.
2. **Circular evaluation:** the same model proposes, answers, and judges a question.
3. **Data leakage:** repeated or paraphrased benchmark questions across train/test boundaries.
4. **Survivorship and censoring:** treating unselected questions as failures.
5. **Correlated relay evidence:** double counting the same finding across agents or descendants.
6. **Unequal compute:** comparing sophisticated AQSI pipelines with underfunded baselines.
7. **Domain mismatch:** treating a shared term or UTN label as semantic equivalence.
8. **Unmeasured opportunity cost:** ignoring curation, schema maintenance, and human review.
9. **Governance drift:** allowing policy changes to contaminate experimental comparisons.
10. **Short horizons:** overlooking delayed benefits or delayed harm.

## 9. Publication and collective-learning protocol

Publish preregistered protocols, evaluation rubrics, conformance tests, anonymized evidence records where permitted, baseline configurations, negative results, and known limitations. When a hypothesis is revised, keep its prior identifier and evidence trail; issue a new version or linked hypothesis rather than silently changing its meaning. Accept counterevidence and alternative scorers as first-class contributions.

No result in this document is presented as an empirical finding. In particular, it does **not** claim demonstrated recursive self-improvement, autonomous scientific discovery, or progress toward ASI.

## 10. Cross-references

- [AQSI-002 — Biomimetic Question Discovery](docs/AQSI-002-Biomimetic-Question-Discovery.md)
- [AQSI-003 — Multi-Granularity Structural Influence Factors](docs/AQSI-003-Multi-Granularity-Structural-Influence-Factors.md)
- [AQSI-004 — Historical Question Intelligence and Differential Trees](docs/AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md)
- [AQSI-005 — Directional Question Scoring and Portfolio Selection](docs/AQSI-005-Directional-Question-Scoring-and-Portfolio-Selection.md)
- [AQSI-007 — Question Structural Relay and Collective Learning](docs/AQSI-007-Question-Structural-Relay-and-Collective-Learning.md)
- [AQSI-008 — Strategic Question Control Planes](docs/AQSI-008-Strategic-Question-Control-Planes.md)
- [AQSI-009 — UTN and Cross-Domain Question Transfer](docs/AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md)
- [AQSI-010 — MVP Architecture and Recursive Evolution](docs/AQSI-010-MVP-Architecture-and-Recursive-Evolution.md)
- [SPEC-001 — Canonical Question Unit Contract](specs/SPEC-001-Canonical-Question-Unit-Contract.md)
- [SPEC-002 — Structural Influence and Scoring Contract](specs/SPEC-002-Structural-Influence-and-Scoring-Contract.md)
- [SPEC-003 — Question Relay and Exploration Lifecycle](specs/SPEC-003-Question-Relay-and-Exploration-Lifecycle.md)
- [SPEC-004 — Control Plane and Policy Conformance](specs/SPEC-004-Control-Plane-and-Policy-Conformance.md)
- [OPEN-QUESTIONS](OPEN-QUESTIONS.md) · [FUTURE-DIRECTIONS](FUTURE-DIRECTIONS.md) · [VALIDATION-ROADMAP](VALIDATION-ROADMAP.md)

---

*AQSI v1.0.0 — Theory-first, falsification-oriented, specifications before runtime, evidence before claims, and collective-learning friendly.*
