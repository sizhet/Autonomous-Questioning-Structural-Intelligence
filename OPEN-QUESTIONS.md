# OPEN QUESTIONS
## Autonomous Questioning Structural Intelligence (AQSI)

**Version:** 1.0.0  
**Status:** Open research agenda; proposals, not validated findings  
**Scope:** Question discovery, multi-granularity structural influence, historical learning, exploration, relay, governance, and recursive improvement  
**Companion documents:** [README](README.md) · [CONTENTS](CONTENTS.md) · [TESTABLE-HYPOTHESES](TESTABLE-HYPOTHESES.md) · [VALIDATION-ROADMAP](VALIDATION-ROADMAP.md)

---

## 1. Purpose and research discipline

AQSI investigates whether an AI research system can improve the *selection and investigation of questions*, rather than merely increase the volume of generated questions. This document records unresolved problems that should remain visible across releases. It does not assert that autonomous questioning, structural transfer, or recursive improvement has been empirically demonstrated.

An open question is represented here by an identifier, a research issue, a potential investigation, and a possible falsification or failure signal. Open questions are not requirements to implement every proposed mechanism. They are candidates for experimental prioritization under explicit resource and governance constraints.

**Working distinctions:**

- A novel question is not necessarily an important question.
- A plausible structural relationship is not proof of causal influence.
- Historical low scores are not evidence of permanent lack of value.
- A selected question does not grant permission to execute an experiment.
- A successful relay is not automatically an independently verified result.
- More questions, agents, or recursive cycles do not by themselves establish intelligence growth.

## 2. Question discovery and biomimetic inspiration

### OQ-DISC-001 — What makes a question scientifically productive?

**Issue.** Novelty, answerability, explanatory reach, and downstream research value can diverge. A question may be initially unanswerable yet unlock productive subquestions.

**Investigation.** Compare expert judgments, experimentally resolved uncertainty, and downstream reusable findings under matched budgets.

**Failure signal.** AQSI-selected questions score highly on internal novelty metrics but do not improve independent research outcomes.

### OQ-DISC-002 — Which biomimetic mechanisms transfer beyond metaphor?

**Issue.** Human curiosity, anomaly detection, analogy, and uncertainty reduction inspire design, but their cognitive origins do not prove computational efficacy.

**Investigation.** Ablate gap-driven, residual-driven, association-driven, and relay-driven discovery against non-biomimetic baselines.

**Failure signal.** No mechanism adds measurable value after controlling for model capability and exploration budget.

### OQ-DISC-003 — How should LLM-first and structure-first discovery interact?

**Issue.** LLM generation can be fluent but structurally shallow; structure-first methods may expose relations that are difficult to express as prompts.

**Investigation.** Compare sequential and parallel pipelines, including structure-first proposals later rendered into prompts or API requests.

**Failure signal.** Added structural machinery increases cost without improving question quality or diversity.

### OQ-DISC-004 — How can the system find unknown unknowns without pretending to enumerate them?

**Issue.** A system can only explicitly score relationships that have been represented or hypothesized.

**Investigation.** Preserve unknown edges, support exploratory probes, and track discovery of previously absent relation types.

**Failure signal.** Exploration repeatedly collapses into known neighborhoods and fails on held-out domain shifts.

## 3. Multi-granularity influence and scoring

### OQ-INFL-001 — What is the minimal useful vocabulary of structural factors?

**Issue.** Concepts, attributes, methods, constraints, evidence, residuals, and transfer points may require different relation semantics.

**Investigation.** Test extensible typed factors against a fixed ontology and against untyped embeddings.

**Failure signal.** Greater granularity causes unstable alignment or complexity without measurable benefit.

### OQ-INFL-002 — How should directional influence be defined and calibrated?

**Issue.** The proposed quantity \(I(q_i \rightarrow q_j)\) may represent predicted enablement, information gain, methodological transfer, or another specified relation; these are not interchangeable.

**Investigation.** Define relation-specific targets, calibration datasets, confidence intervals, and prospective outcome tests.

**Failure signal.** Predicted direction or magnitude does not correlate with held-out observed outcomes.

### OQ-INFL-003 — Which folding operators preserve useful distinctions?

**Issue.** Aggregating heterogeneous evidence can hide counterevidence, duplicate correlated signals, or reward prolific factor enumeration.

**Investigation.** Compare sum, robust aggregation, dependency-aware folding, perspective-specific scoring, and explicit abstention.

**Failure signal.** Rankings change arbitrarily under harmless representation changes or duplicate factors.

### OQ-INFL-004 — How should unknown, missing, contradictory, and negative relationships differ?

**Issue.** Treating unknown influence as zero can systematically suppress exploration; treating it as positive can encourage speculative noise.

**Investigation.** Compare explicit unknown states, uncertainty bounds, exploration bonuses, and abstention policies.

**Failure signal.** The system becomes either overconfident or unable to prioritize actionable questions.

### OQ-INFL-005 — Can influence graphs remain computationally tractable?

**Issue.** Dense pairwise question scoring scales approximately quadratically in candidate count before factor-level comparisons.

**Investigation.** Evaluate sparse retrieval, approximate nearest neighbors, hierarchical factor indexing, incremental updates, and bounded candidate neighborhoods.

**Failure signal.** Compute overhead exceeds the value of improved research selection at realistic corpus sizes.

## 4. Historical Question Intelligence and Differential Trees

### OQ-HIST-001 — What constitutes a reliable historical question outcome?

**Issue.** Answers, partial progress, reproducible experiments, reusable methods, and descendant questions have different evidentiary status.

**Investigation.** Define outcome labels with provenance, evaluation horizon, confidence, and delayed effects.

**Failure signal.** Historical labels cannot be reproduced by independent reviewers or reliably predict future utility.

### OQ-HIST-002 — How can selection bias be corrected?

**Issue.** Only explored questions receive outcomes, while screened-out questions remain largely unobserved.

**Investigation.** Use randomized exploration quotas, propensity logging, off-policy evaluation, and uncertainty-aware revisits.

**Failure signal.** A history-trained scorer systematically rejects useful but unconventional questions.

### OQ-HIST-003 — When do Question Differential Trees help?

**Issue.** Core-plus-Delta representations may support reuse, but poor cores can erase decisive domain distinctions.

**Investigation.** Compare tree-based family retrieval with flat embeddings, graph retrieval, and expert taxonomies.

**Failure signal.** Tree compression reduces retrieval accuracy or transfer reliability.

### OQ-HIST-004 — How should failed or deferred questions be revisited?

**Issue.** New evidence, methods, resources, or domain knowledge may reverse earlier assessments.

**Investigation.** Define event-triggered and time-triggered re-evaluation with cost-aware thresholds.

**Failure signal.** Revisit policies cause endless retries or systematically miss later breakthroughs.

### OQ-HIST-005 — How can delayed relay value be attributed?

**Issue.** A question may be valuable because it enables several later questions, but simple descendant counting invites double counting.

**Investigation.** Compare causal attribution approximations, provenance-based credit assignment, and bounded time-horizon measures.

**Failure signal.** Credit can be inflated by trivial splitting or repeated relaying.

## 5. Goal-open scoring and portfolio selection

### OQ-PORT-001 — What does goal-open selection optimize?

**Issue.** Absence of a predetermined target question does not mean absence of evaluation criteria or values.

**Investigation.** Specify candidate influence, uncertainty reduction, diversity, feasibility, and policy constraints separately; compare their predictive value.

**Failure signal.** An opaque composite score cannot be audited or meaningfully validated.

### OQ-PORT-002 — When does pairwise influence sum work?

**Issue.** A baseline score \(S(q_i)=\sum_{j\ne i}I(q_i\rightarrow q_j)\) may favor central or broadly connected questions while overlooking isolated breakthroughs.

**Investigation.** Compare degree-normalized, robust, novelty-aware, and portfolio-marginal alternatives.

**Failure signal.** The baseline systematically prefers redundant hubs over productive frontier questions.

### OQ-PORT-003 — How should complementarity and redundancy be measured?

**Issue.** Two individually valuable questions may overlap, while low-ranked questions may be jointly decisive.

**Investigation.** Test pairwise and higher-order portfolio interactions under matched research budgets.

**Failure signal.** Portfolio selection performs no better than independent top-k ranking.

### OQ-PORT-004 — Can breakthrough readiness be estimated responsibly?

**Issue.** Proximity to a breakthrough is difficult to define prospectively and may be confounded by hindsight.

**Investigation.** Pre-register readiness indicators and test on temporally held-out research histories.

**Failure signal.** Apparent accuracy vanishes under prospective evaluation or domain shift.

## 6. Question Units, exploration, and evidence

### OQ-UNIT-001 — What is the smallest interoperable Question Unit?

**Issue.** A portable unit must preserve identity, semantics, provenance, and evidence without imposing a rigid universal ontology.

**Investigation.** Test canonical minimum fields plus typed extensions and conformance checks across heterogeneous agents.

**Failure signal.** Implementations cannot exchange questions without substantial manual reinterpretation.

### OQ-UNIT-002 — How should prompts and execution contracts remain distinct?

**Issue.** The same research question can be expressed as a prompt, query, experiment, or formal task; expression alone does not define authorization.

**Investigation.** Evaluate adapters that preserve Question Unit semantics and separate execution permissions.

**Failure signal.** Re-expression changes the underlying research claim or bypasses governance.

### OQ-UNIT-003 — How should evidence quality be adjudicated?

**Issue.** Model agreement, repeated generated explanations, and real-world corroboration are not equivalent.

**Investigation.** Use source independence, replication, provenance, uncertainty, and adversarial review in evidence contracts.

**Failure signal.** Self-referential model outputs are mistaken for independent support.

### OQ-UNIT-004 — How can negative and inconclusive outcomes remain reusable?

**Issue.** Discarded failures can waste resources and bias later question selection.

**Investigation.** Encode counterevidence, limitations, failed methods, and explicit leftover in transferable records.

**Failure signal.** Future agents repeatedly pursue previously refuted approaches without new justification.

## 7. Structural Relay and collective learning

### OQ-RELAY-001 — What makes a relay semantically faithful?

**Issue.** Derive, split, compose, transfer, refute, revisit, replicate, fold, and unfold can alter the meaning of a question.

**Investigation.** Require operator-specific provenance and semantic-preservation or semantic-change declarations.

**Failure signal.** Relay chains accumulate unrecognized semantic drift.

### OQ-RELAY-002 — When does multi-agent exchange become collective learning?

**Issue.** Message passing alone does not guarantee reusable knowledge or improved future decisions.

**Investigation.** Measure independent reuse, transfer success, provenance retention, and future research outcomes.

**Failure signal.** Additional agents increase communication but not independently verified progress.

### OQ-RELAY-003 — When is repeated execution informative?

**Issue.** Repetition may reveal variance or drift, but identical runs may provide little new independent evidence.

**Investigation.** Track environmental changes, independence assumptions, reproducibility, and marginal information gain.

**Failure signal.** Repetition inflates confidence without new information.

### OQ-RELAY-004 — How can relay ecosystems resist contamination?

**Issue.** Incorrect findings, duplicated evidence, and malicious or low-quality contributions can propagate.

**Investigation.** Test quarantine, review, revocation, lineage tracing, and trust-aware reuse policies.

**Failure signal.** One unverified claim contaminates multiple downstream research decisions.

## 8. UTN and cross-domain transfer

### OQ-UTN-001 — Which semantic alignment contracts are sufficient for transfer?

**Issue.** Shared names and structural resemblance do not guarantee equivalent causal mechanisms.

**Investigation.** Define type, unit, relation, assumption, context, and evidence compatibility checks.

**Failure signal.** Mapped questions fail because hidden domain constraints were ignored.

### OQ-UTN-002 — How can partial transfer be distinguished from full equivalence?

**Issue.** Useful transfer may apply only to a method, attribute, constraint, or question-generating relation.

**Investigation.** Represent transferable cores alongside target-domain deltas and invalidity conditions.

**Failure signal.** The system transfers answers or conclusions where only methods were transferable.

### OQ-UTN-003 — When should AQSI propose new UTN types?

**Issue.** New structural relationships can motivate ontology evolution, but uncontrolled proliferation harms interoperability.

**Investigation.** Compare conservative extension, aliasing, versioned migration, and review-gated type proposals.

**Failure signal.** Type changes break existing question identities or invalidate historical comparisons.

### OQ-UTN-004 — How can negative transfer be detected early?

**Issue.** High structural similarity may mask divergent domain assumptions.

**Investigation.** Test counterexample search, target-domain probes, confidence decay, and reversible transfer decisions.

**Failure signal.** Cross-domain mechanisms systematically underperform source-domain-only baselines.

## 9. Strategic Question Control Plane and governance

### OQ-GOV-001 — How should strategic priorities constrain autonomous discovery?

**Issue.** Policies may specify directions, budgets, and boundaries without naming every research question.

**Investigation.** Compare explicit policy contracts with informal prompt instructions under identical research portfolios.

**Failure signal.** The system silently optimizes away mandated research diversity or safety constraints.

### OQ-GOV-002 — What is the correct separation of decision rights?

**Issue.** Discovery, scoring, portfolio selection, resource commitment, and action authorization are different decisions.

**Investigation.** Test multi-layer authorization, audit trails, and denial behavior under conflicting policies.

**Failure signal.** A high-scoring question triggers unauthorized experiments or policy changes.

### OQ-GOV-003 — How should competing stakeholders be represented?

**Issue.** Research priorities may conflict across funders, researchers, affected communities, and safety authorities.

**Investigation.** Compare perspective-aware scoring, transparent constraints, and appeal/revision procedures.

**Failure signal.** Hidden weighting makes one stakeholder's preferences appear objectively universal.

### OQ-GOV-004 — Can strategic policy adapt without authority drift?

**Issue.** Research findings may justify policy recommendations but should not automatically grant the system authority to enact them.

**Investigation.** Require proposal, review, approval, versioning, and rollback for policy updates.

**Failure signal.** Feedback loops gradually expand execution privileges without explicit authorization.

## 10. Meta-questions, co-evolution, and recursive improvement

### OQ-RSI-001 — Which meta-questions are worth pursuing?

**Issue.** AQSI may question its own discovery, scoring, or relay mechanisms; not every self-directed proposal is useful.

**Investigation.** Rank meta-questions by independently measurable improvement potential and expected validation cost.

**Failure signal.** Self-analysis consumes resources without improving external research outcomes.

### OQ-RSI-002 — What qualifies as verified recursive improvement?

**Issue.** Generating a modification proposal is not evidence of improved capability.

**Investigation.** Require held-out benchmarks, regression tests, cost accounting, and rollback-ready deployment.

**Failure signal.** Gains disappear under independent replication or new tasks.

### OQ-RSI-003 — Can AQSI, UTN, HQI, SIF, and UIERU co-evolve beneficially?

**Issue.** Cross-system feedback may create productive innovations or destabilizing incompatibilities.

**Investigation.** Evaluate isolated updates, paired updates, and jointly governed updates with interface conformance.

**Failure signal.** Co-updates degrade interoperability, reliability, or cumulative learning.

### OQ-RSI-004 — How can recursive optimization resist Goodhart effects?

**Issue.** Optimizing a question score can decouple it from actual scientific value.

**Investigation.** Use multiple evaluators, independent outcomes, adversarial checks, and periodic metric revision.

**Failure signal.** Internal scores rise while validated discoveries stagnate or decline.

### OQ-RSI-005 — What can and cannot be inferred about ASI?

**Issue.** Open-ended question generation, collective learning, and recursive improvement are candidate research mechanisms, not sufficient demonstrations of artificial superintelligence.

**Investigation.** Define narrow, falsifiable capability milestones without assuming a guaranteed path to ASI.

**Failure signal.** Broad intelligence claims rest only on self-reported model performance or speculative extrapolation.

## 11. Measurement and evaluation design

### OQ-EVAL-001 — Which outcomes should be primary?

Candidate outcomes include validated uncertainty reduction, independently reproduced findings, useful derived questions, transfer success, and cost-adjusted research progress. Their relative weights should be pre-registered for each experiment rather than retrofitted after observing results.

### OQ-EVAL-002 — Which baselines are indispensable?

At minimum: unstructured LLM questioning, random or diversity-based selection, history-only scoring, structure-only scoring, flat semantic retrieval, and a human-curated question portfolio. Additional baselines should be selected based on the hypothesis under test.

### OQ-EVAL-003 — How should evaluation avoid leakage?

Separate training history, selection history, evaluator access, and test outcomes; use temporal holdouts and independent adjudication where feasible. Record model versions, prompts, seeds, tools, and budgets.

### OQ-EVAL-004 — What are appropriate stopping rules?

Define budget limits, evidence thresholds, safety constraints, diminishing marginal value, and revisit triggers. A stopped question should retain its status, reason, and explicit leftover rather than being silently discarded.

## 12. Prioritization framework

The following is a **proposed initial research order**, not an empirically established ranking.

| Priority | Questions | Reason for early attention | Suggested initial artifact |
|---|---|---|---|
| P0 | OQ-UNIT-001, OQ-INFL-002, OQ-HIST-001 | Establish interoperable records and measurable targets | Contract fixtures and annotated question corpus |
| P0 | OQ-EVAL-001, OQ-EVAL-002, OQ-EVAL-003 | Make comparative claims testable | Pre-registered benchmark protocol |
| P0 | OQ-GOV-002, OQ-UNIT-002 | Separate selection from execution authority | Authorization and denial tests |
| P1 | OQ-DISC-003, OQ-INFL-003, OQ-HIST-002 | Test core discovery, folding, and historical learning | Ablation study |
| P1 | OQ-PORT-002, OQ-PORT-003, OQ-RELAY-002 | Evaluate portfolio and collective-learning claims | Matched-budget study |
| P1 | OQ-UTN-001, OQ-UTN-004 | Test semantic transfer and failure detection | Cross-domain transfer benchmark |
| P2 | OQ-RSI-002, OQ-RSI-003, OQ-RSI-004 | Study controlled structural improvement after baselines exist | Versioned improvement trials |
| P2 | OQ-RSI-005 | Maintain explicit long-horizon scientific boundaries | Capability-claims review |

Priority labels are revisable through the Strategic Question Control Plane; they do not imply permission to execute a study.

## 13. Open-question record template

Future contributions should use a compact, reviewable record:

```yaml
open_question_id: OQ-EXAMPLE-001
version: 1
status: open                 # open | investigating | deferred | resolved | superseded
research_issue: "Precisely stated uncertainty"
structural_factors:
  - type: method
    utn_ref: "example:method:1"
proposed_test: "Prospective comparison under matched budgets"
primary_metric: "Independent validated findings per unit cost"
comparison_baseline: "Unstructured LLM question selection"
possible_falsifier: "No statistically or practically meaningful improvement"
evidence_refs: []
counterevidence_refs: []
provenance_refs: []
explicit_leftover: []
policy_ref: null
owner: null
last_reviewed: null
```

This YAML is **illustrative**, not a normative schema. Normative fields and lifecycle requirements belong in [SPEC-001](specs/SPEC-001-Canonical-Question-Unit-Contract.md), [SPEC-002](specs/SPEC-002-Structural-Influence-and-Scoring-Contract.md), [SPEC-003](specs/SPEC-003-Question-Relay-and-Exploration-Lifecycle.md), and [SPEC-004](specs/SPEC-004-Control-Plane-and-Policy-Conformance.md).

## 14. How to contribute evidence

A useful contribution states the question addressed, the protocol and baseline, data provenance, resource budget, uncertainty, counterevidence, and whether findings have been independently reproduced. Negative findings and failed transfers are welcome if they are reproducible and clearly scoped.

Contributions can also propose new question families, UTN mappings, influence operators, evaluator designs, or governance contracts. Structural changes should preserve backward traceability and be reviewed before they are treated as validated improvements.

## 15. Related research files

- [AQSI-002 — Biomimetic Question Discovery](docs/AQSI-002-Biomimetic-Question-Discovery.md)
- [AQSI-003 — Multi-Granularity Structural Influence Factors](docs/AQSI-003-Multi-Granularity-Structural-Influence-Factors.md)
- [AQSI-004 — Historical Question Intelligence and Differential Trees](docs/AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md)
- [AQSI-005 — Directional Question Scoring and Portfolio Selection](docs/AQSI-005-Directional-Question-Scoring-and-Portfolio-Selection.md)
- [AQSI-007 — Question Structural Relay and Collective Learning](docs/AQSI-007-Question-Structural-Relay-and-Collective-Learning.md)
- [AQSI-008 — Strategic Question Control Planes](docs/AQSI-008-Strategic-Question-Control-Planes.md)
- [AQSI-009 — UTN and Cross-Domain Question Transfer](docs/AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md)
- [EXT-001 — Question Ecosystem and Meta-Question Discovery](extensions/EXT-001-Question-Ecosystem-and-Meta-Question-Discovery.md)
- [EXT-002 — Cross-Structural Co-Evolution](extensions/EXT-002-Cross-Structural-Co-Evolution.md)
- [EXT-003 — Open-Ended Question Intelligence and ASI Boundaries](extensions/EXT-003-Open-Ended-Question-Intelligence-and-ASI-Boundaries.md)

---

**Research position:** AQSI is an open, theory-first research framework. Its proposed mechanisms require prospective testing, independent evaluation, and appropriate human governance before claims of reliable autonomous research improvement can be made.
