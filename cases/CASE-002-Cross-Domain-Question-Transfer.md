# CASE-002 — Cross-Domain Question Transfer

**Project:** Autonomous Questioning Structural Intelligence (AQSI)  
**Version:** v1.0.0 — Research Case  
**Status:** Proposed architecture and illustrative thought experiment; not an empirical result  
**Scope:** UTN-aligned, multi-granularity, directional, evidence-aware question transfer

## Abstract

This case examines how Autonomous Questioning Structural Intelligence (AQSI) might discover and evaluate useful research questions by transferring *partial structures* across domains. The illustrative source domain is continuous-integration (CI) flaky-test diagnosis; the target domain is intermittent anomalies in environmental sensor networks. The domains are not asserted to be equivalent. Instead, AQSI represents a source question as typed factors, identifies candidate mappings under Universal Typing and Naming (UTN) contracts, generates target-domain questions, estimates directional influence and historical transfer potential, and authorizes bounded exploration. A worked example traces one question through discovery, alignment, scoring, exploration, counter-evidence, and structural relay. All scores, observations, and outcomes below are hypothetical. The case defines falsifiable hypotheses and a conformance-oriented MVP plan rather than claiming demonstrated transfer performance.

**Keywords:** AQSI, cross-domain question transfer, UTN, structural influence, Question Differential Trees, historical question intelligence, structural relay, evidence provenance, research governance

---

## 1. Purpose and Research Boundary

AQSI aims to move beyond responding to a given prompt by discovering, selecting, and refining research questions. Cross-domain transfer is one candidate mechanism: a diagnostic question useful in one domain may expose a previously neglected relation in another. However, lexical resemblance is insufficient. Transfer must preserve relevant semantic constraints, identify non-transferable assumptions, and expose uncertainty.

This case asks:

> Can an AQSI system use typed, multi-granularity structural alignment and historical feedback to produce *more useful and testable* target-domain questions than a domain-only or unstructured analogy baseline, under comparable budgets?

This is a research question, not a positive finding.

### 1.1 Source and target domains

- **Source (D_s):** intermittent failures in CI test pipelines, where failures may depend on timing, concurrency, environment, hidden state, or instrumentation.
- **Target (D_t):** intermittent anomalous readings in a distributed environmental sensor network, where anomalies may depend on sampling, synchronization, calibration, physical conditions, communication, or hardware faults.

The shared abstraction is **an intermittent observed deviation with potentially hidden contextual causes**. It does *not* imply shared physical causality or identical diagnostic interventions.

### 1.2 What is transferred?

The transferable object is not a ready-made answer. It is a **Question Unit** (QU) with typed structural factors, a candidate mapping, a test plan, and explicit leftovers. Source-domain evidence can motivate target-domain hypotheses but cannot verify them.

## 2. Connection to the AQSI Research Framework

This case operationalizes the following research documents:

| Document | Contribution to this case |
|---|---|
| `AQSI-002-Biomimetic-Question-Discovery.md` | Gap-, residual-, association-, and relay-driven candidate discovery |
| `AQSI-003-Multi-Granularity-Structural-Influence-Factors.md` | Typed factors and directed, heterogeneous relationships |
| `AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md` | Historical assessment and Core/Delta representation |
| `AQSI-005-Directional-Question-Scoring-and-Portfolio-Selection.md` | Goal-open candidate influence and resource-aware portfolio choice |
| `AQSI-006-Question-Units-and-Exploration-Contracts.md` | Durable question identity and bounded exploration |
| `AQSI-007-Question-Structural-Relay-and-Collective-Learning.md` | Evidence, counter-evidence, and derivative questions |
| `AQSI-008-Strategic-Question-Control-Planes.md` | Research direction, resource budgets, and action authorization |
| `AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md` | Semantic alignment and transfer operators |
| `SPEC-001-Canonical-Question-Unit-Contract.md` | Question identity and provenance |
| `SPEC-002-Structural-Influence-and-Scoring-Contract.md` | Directionality, uncertainty, and folding |
| `SPEC-003-Question-Relay-and-Exploration-Lifecycle.md` | Exploration/relay transitions |
| `SPEC-004-Control-Plane-and-Policy-Conformance.md` | Policy conformance and authority boundaries |

The contracts above are proposed research specifications; this document does not assert that a conformant implementation exists.

## 3. Starting Question in the Source Domain

A source-domain question is:

**QU-CI-017:** *When a CI test fails intermittently, can controlled perturbation of scheduling and environment distinguish hidden shared-state interference from an intrinsic test defect?*

The question is intentionally decomposed into factors:

| Factor ID | Kind | Source-domain meaning | Evidence status |
|---|---|---|---|
| CI-C1 | Phenomenon | Intermittent failure | Observed in hypothetical scenario |
| CI-A1 | Attribute | Failure frequency varies by context | Hypothesized |
| CI-M1 | Method | Controlled perturbation | Proposed intervention |
| CI-M2 | Method | Repeated execution with logging | Proposed measurement |
| CI-R1 | Relation | Scheduling influences observed failure | Unverified candidate |
| CI-E1 | Evidence | Test run traces | Potential evidence source |
| CI-L1 | Leftover | Unknown shared-state dependencies | Open question |

A hypothetical historical registry might contain related questions about concurrency, environmental drift, or test isolation. A history record must retain its observation context and cannot be treated as transferable proof.

## 4. UTN-Based Structural Alignment

### 4.1 Identity, type, and scope

UTN is used here as a proposed infrastructure for explicit type identity, namespaces, granularity, and semantic contracts. Example type labels below are illustrative, not an established UTN standard:

```text
utn:aqsi/phenomenon/intermittent-deviation
utn:aqsi/attribute/context-dependence
utn:aqsi/method/controlled-perturbation
utn:aqsi/method/repeated-measurement
utn:aqsi/evidence/timestamped-observation
utn:aqsi/relation/context-affects-observation
utn:aqsi/leftover/unmodeled-dependency
```

A mapping must record **source type**, **target type**, **semantic contract**, **mapping direction**, **conditions**, **confidence**, and **known exclusions**. Shared labels alone do not constitute a valid mapping.

### 4.2 Candidate factor mapping

| Source factor | Target factor | Mapping type | Essential condition / limitation |
|---|---|---|---|
| Intermittent test failure | Intermittent sensor anomaly | Analogical phenomenon | Sensor anomaly may be a true physical event, not a system defect |
| Environment dependence | Operating-context dependence | Attribute transfer | Weather, power, and calibration differ from CI environments |
| Schedule perturbation | Sampling/synchronization perturbation | Method analogy | Intervention must not compromise measurement integrity |
| Repeated test runs | Repeated sensor observations | Method transfer | Temporal autocorrelation reduces independent evidence |
| Execution traces | Time-stamped sensor/network logs | Evidence analogy | Sensor provenance and clocks may be unreliable |
| Hidden shared state | Hidden common-mode dependency | Causal hypothesis | Common-mode mechanisms must be discovered, not assumed |

A mapping registry distinguishes `proposed`, `supported`, `refuted`, and `unresolved` mapping states. **Unknown mappings are not assigned zero influence by default.**

### 4.3 Why partial mapping matters

The domains have distinct failure semantics. CI tests are designed to return expected software outcomes; sensor measurements describe physical phenomena under uncertainty. A cross-domain system must be able to transfer a *diagnostic method* without transferring a *causal explanation*.

## 5. Question Differential Tree: Core and Delta

Represent a question family as:

$$
Q = \langle C,\Delta_D,\Gamma_D\rangle,
$$

where \(C\) is a reusable structural core, \(\Delta_D\) is the domain-specific delta, and \(\Gamma_D\) records constraints and exclusions.

**Core:** When intermittent observations vary with context, which controlled perturbations and measurements can distinguish competing hidden causes?

**CI delta:** Test scheduling, shared state, runtime environment, repeatability of assertions.

**Sensor delta:** Sampling clocks, calibration, communications, physical events, common-mode environmental effects.

**Sensor constraints:** Preserve raw observations; avoid unsafe device control; separate real environmental events from instrumentation faults.

The differential-tree representation is a proposed method for tracking retained structure and modified assumptions. It does not establish that the resulting question is useful.

## 6. Target-Domain Question Generation

Three target-domain candidates are derived from the aligned structure:

**QU-SN-101 — Timing hypothesis:** *Can time-synchronization checks and controlled changes in sampling schedules distinguish timestamp artifacts from genuine transient environmental events?*

**QU-SN-102 — Common-mode hypothesis:** *Do anomalies co-occur across sensors sharing a power supply or communications gateway, and can this pattern distinguish infrastructure effects from local physical events?*

**QU-SN-103 — Repeated-observation hypothesis:** *Under what conditions do repeated measurements reduce uncertainty about intermittent sensor anomalies, and when does temporal dependence invalidate apparent corroboration?*

These are candidates, not conclusions. Each should record the parent question, transfer operator, UTN mappings, proposed evidence, and non-transferable assumptions.

### 6.1 Structure-first and LLM-first routes

- **Structure-first:** map typed factors and detect unresolved relationships; then express the missing relation as a question.
- **LLM-first:** ask a model for candidate analogies; subsequently normalize them into typed factors and test their semantic validity.

A conformant comparison holds retrieval access, exploration budget, and target-domain evidence constant wherever possible.

## 7. Directional Influence and Transfer Scoring

### 7.1 Factor-level influence

Let \(H(q)\) denote typed factors of a question. A directional relation score may be defined as:

$$
I(q_i\rightarrow q_j)=operatorname{Fold}_{a\in H(q_i),\,b\in H(q_j)}
\left[w_{ab}\,R_{ab}(a\rightarrow b)\right].
$$

Here \(R_{ab}\) represents a proposed directional influence relationship; \(w_{ab}\) and the folding operator are versioned, replaceable components. An evidence state and uncertainty interval should accompany the numerical estimate. Generally, \(I(q_i\rightarrow q_j)\ne I(q_j\rightarrow q_i)\).

### 7.2 Separate transfer plausibility from research value

A candidate can be structurally plausible yet scientifically unimportant. Keep at least three distinct assessments:

1. **Alignment validity:** Does the typed mapping preserve relevant semantics?
2. **Question potential:** Is the target question testable, informative, and likely to reduce a meaningful uncertainty?
3. **Exploration admissibility:** Is the proposed investigation within resource and authorization constraints?

These assessments must not be collapsed into an unexplained scalar. A portfolio policy may fold them only under an explicit, auditable rule.

### 7.3 Illustrative candidate assessment

The following values are **invented solely to demonstrate a scoring interface**; they are not measurements.

| Candidate | Alignment plausibility (0–1) | Historical support (0–1) | Expected information value (0–1) | Major uncertainty |
|---|---:|---:|---:|---|
| QU-SN-101 | 0.82 | 0.58 | 0.76 | Clock quality and causal identifiability |
| QU-SN-102 | 0.74 | 0.66 | 0.83 | Shared exposure versus shared infrastructure |
| QU-SN-103 | 0.88 | 0.49 | 0.71 | Autocorrelation and observation dependence |

The illustrative numbers are not comparable without defined calibration, confidence, and provenance. A system should preserve individual factors and support alternative folding policies.

### 7.4 Goal-open and strategic selection

Under goal-open selection, a question may be ranked by its directional influence on other candidate questions:

$$
S(q_i)=\sum_{j\ne i} I(q_i\rightarrow q_j).
$$

A portfolio may also consider diversity, cost, information gain, dependencies, and uncertainty. A Strategic Question Control Plane may prioritize environmental monitoring reliability without dictating each specific question. Policy priority must remain distinct from evidence of truth.

## 8. Historical Question Intelligence Across Domains

A historical record should minimally contain:

```yaml
history_record_id: HIST-CI-042
source_question_id: QU-CI-017
source_domain: software-ci
observed_outcome: illustrative-partial-success
assessment_type: retrospective-question-utility
assessment_version: hqi-v0.1
method_context: controlled-scheduling-perturbation
supporting_evidence_refs: [EV-CI-101]
counter_evidence_refs: [EV-CI-102]
transfer_scope:
  candidate_target_domain: environmental-sensors
  reusable_factors: [controlled-perturbation, repeated-measurement]
  excluded_assumptions: [software-test-oracle, identical-failure-mechanism]
uncertainty: high
status: hypothetical-example
```

Historical success in the source domain should influence *which question is worth testing*, not the truth of the target-domain hypothesis. History-based filtering should support `defer` and `revisit`, not irreversible suppression of unfamiliar research directions. Avoid leakage between historical training and target-domain evaluation sets.

## 9. Exploration Contract for QU-SN-102

The following is an **illustrative contract sketch**, not a validated schema implementation:

```yaml
contract_id: EC-SN-102-v0.1
question_id: QU-SN-102
contract_version: draft-0.1
research_goal: distinguish common-mode infrastructure artifacts from local events
allowed_actions:
  - read_deidentified_historical_sensor_logs
  - compute_cross_sensor_cooccurrence_statistics
  - run_offline_hypothesis_tests
prohibited_actions:
  - change_live_sensor_calibration
  - disable_operational_alerting
  - infer_personal_location_from_sensor_data
resources:
  max_compute_hours: 4
  max_human_review_hours: 2
required_evidence:
  - sensor_timestamp_quality_report
  - topology_or_shared_infrastructure_metadata
  - alternative_cause_analysis
required_counterevidence:
  - test_for_shared_external_environmental_event
  - assess_autocorrelation_and_missing_data
exit_conditions:
  - evidence_sufficient_for_review
  - budget_exhausted
  - authorization_revoked
review_required_before_external_action: true
status: hypothetical-example
```

A selected question does **not** grant authority to manipulate live sensors or external systems. The operational plane must verify the active policy and contract before any action.

## 10. Hypothetical Exploration and Evidence Handling

Assume, for illustration only, that offline analysis finds anomalous readings concentrated among sensors sharing one gateway. This observation supports investigating a common-mode mechanism but does not establish the gateway as the cause. Alternative explanations include correlated environmental events, deployment topology, time-alignment errors, and selective missingness.

An evidence ledger should distinguish:

| Record | Claim | Epistemic status | Next check |
|---|---|---|---|
| EV-SN-201 | Co-occurrence is higher within one gateway group | Hypothetical observation | Recompute with timestamp uncertainty |
| EV-SN-202 | Gateway failure caused the anomalies | Unsupported inference | Compare controls and alternative causes |
| CE-SN-203 | Same anomaly pattern appears across unrelated gateways | Hypothetical counter-evidence | Investigate external common exposure |
| LO-SN-204 | Unknown physical-event confounding | Explicit leftover | Seek independent physical measurements |

A correct system must not promote an inference to verified evidence merely because multiple agents agree.

## 11. Structural Relay: The Next Question Family

The exploration can produce new Question Units even when the initial causal hypothesis remains unresolved:

- **Derive:** *Which gateway metadata best predicts the observed co-occurrence pattern?*
- **Split:** *Are timing artifacts and power interruptions distinguishable from the existing logs?*
- **Transfer:** *Does the same common-mode diagnostic structure apply to industrial equipment telemetry?*
- **Refute:** *What observation would falsify the gateway-causation hypothesis?*
- **Replicate:** *Does the pattern recur in a non-overlapping sensor deployment?*
- **Revisit:** *Should QU-SN-101 be re-scored after clock-quality measurements improve?*

Each relay piece needs parent references, transformation type, UTN alignment, provenance, evidence state, and policy context. Repeated execution is a valid relay when it accumulates meaningful observations or tests robustness; repeated correlated measurements are not automatically independent confirmation.

## 12. Proposed Canonical Relay Record

```yaml
relay_id: RELAY-SN-102-01
parent_question_ids: [QU-CI-017, QU-SN-102]
child_question_id: QU-SN-104
relay_operator: derive
source_domain: software-ci
target_domain: environmental-sensors
utn_mapping_ref: MAP-CI-SN-001
exploration_contract_ref: EC-SN-102-v0.1
evidence_refs: [EV-SN-201]
counter_evidence_refs: [CE-SN-203]
explicit_leftovers: [LO-SN-204]
claim_status: unresolved
review_status: pending
policy_ref: POLICY-SN-RESEARCH-v0.1
status: hypothetical-example
```

This record is a readable example; canonical field-level requirements belong to the specifications. Real implementations should use stable identifiers and schema-version negotiation rather than assuming these exact names are final.

## 13. Failure Modes and Safeguards

| Failure mode | Consequence | Safeguard |
|---|---|---|
| Surface-level analogy | Irrelevant or misleading questions | Typed factor alignment and domain expert review |
| Hidden domain assumptions | False causal transfer | Explicit excluded-assumption register |
| Historical score overfitting | Suppression of novel ideas | Cold-start exploration budget and revisit policy |
| Unknown relation treated as zero | Lost discovery opportunities | Separate unknown and measured-null states |
| Score double counting | Inflated candidate ranking | Evidence-dependency and provenance tracking |
| Correlated repetitions | False confidence | Independence checks and uncertainty accounting |
| Uncalibrated cross-domain scores | Misleading ranking | Domain-specific calibration and sensitivity analysis |
| Prompt leakage or source contamination | Invalid evaluation | Isolated datasets and audit logs |
| Unauthorized exploration | Operational or privacy harm | Contract-based authorization and human review |
| Relay semantic drift | Degraded knowledge ecosystem | Versioned UTN mappings and conformance tests |

## 14. MVP Architecture

A minimal, contract-first prototype may comprise:

```text
Source Question Registry + Historical Outcomes
                   |
                   v
          UTN Factor Extractor
                   |
                   v
       Typed Alignment / Delta Builder
                   |
                   v
     Candidate Question Generation
       (structure-first + LLM-first)
                   |
                   v
       Directional Influence Scorer
                   |
                   v
      History-Aware Portfolio Selector
                   |
                   v
          Policy / Contract Gate
                   |
                   v
         Offline Exploration Agent
                   |
                   v
     Evidence + Counter-Evidence Ledger
                   |
                   v
       Question Structural Relay
                   |
                   +----> Registry / History Update
```

The architecture is deliberately modular: each scorer, mapper, generator, and evaluator can be replaced while preserving contracts.

### 14.1 Incremental stages

**M0 — Representation and traceability.** Curate a small source/target question set, UTN mappings, and immutable provenance records.

**M1 — Candidate comparison.** Compare structure-first, LLM-first, and combined question generation under matched budgets.

**M2 — Historical scoring.** Add prior question outcomes and assess calibration, ranking, and novelty suppression.

**M3 — Controlled exploration.** Execute authorized offline tests, capture counter-evidence, and measure useful relay output.

**M4 — Cross-domain replication.** Repeat the protocol with a different source/target pair to test generality.

No stage requires live operational autonomy to demonstrate the research mechanism.

## 15. Evaluation Protocol

### 15.1 Baselines

- **B0 Domain-only:** Generate target-domain questions without source-domain history or analogy.
- **B1 LLM analogy:** Generate cross-domain questions using a language model without explicit typed mapping.
- **B2 Typed mapping only:** Use UTN factor alignment without historical scoring.
- **B3 Historical retrieval only:** Retrieve related questions without explicit cross-domain mapping.
- **B4 Full proposed AQSI:** Typed mapping, multi-granularity influence, history, portfolio selection, exploration, and relay.

Hold model access, target-domain corpus, token budget, exploration time, and human-review budget as comparable as possible. Pre-register the protocol and keep evaluation examples separate from training and prompt tuning.

### 15.2 Outcome measures

1. **Semantic validity:** Fraction of candidate mappings judged to preserve the claimed relation.
2. **Testability:** Fraction of questions with feasible falsification or discrimination procedures.
3. **Question utility:** Blind expert ratings of expected information value, reported with agreement statistics.
4. **Evidence yield:** New, independently reviewable observations per exploration cost.
5. **Relay productivity:** Number and quality of non-redundant follow-up questions, not raw question count.
6. **Calibration:** Correspondence between predicted value and later assessed outcomes.
7. **Novelty retention:** Rate at which unfamiliar but later useful questions survive early screening.
8. **Governance conformance:** Policy violations, missing provenance, and unauthorized actions.
9. **Cross-domain robustness:** Stability across different source/target domain pairs.

Expert ratings alone are not evidence of scientific discovery; where feasible, independent downstream experiments should assess actual knowledge gain.

## 16. Testable Hypotheses

**H1 — Semantic validity.** Typed, contract-checked mapping produces fewer invalid analogies than unstructured LLM analogy under matched conditions.

**H2 — Testability.** Structure-first plus LLM-first generation yields a higher proportion of operationally testable questions than either route alone.

**H3 — Historical efficiency.** Historical question intelligence reduces wasted exploration budget without materially lowering the discovery of useful novel questions.

**H4 — Directional scoring.** Direction-aware influence estimates predict useful downstream question dependencies better than symmetric similarity scores.

**H5 — Core/Delta transparency.** Question Differential Trees improve expert identification of non-transferable assumptions compared with flat question text.

**H6 — Relay quality.** Evidence-linked relay produces more non-redundant, actionable follow-up questions than free-form summaries.

**H7 — Unknown-state preservation.** Explicitly preserving unknown relations improves novel-link discovery compared with treating missing relations as zero.

**H8 — Governance conformance.** Contract-gated exploration reduces unauthorized actions without eliminating the ability to conduct approved offline studies.

All hypotheses may fail. Null results and negative transfer should be retained as reusable historical evidence.

## 17. Conformance Checklist

A proposed implementation should demonstrate that it:

- [ ] Assigns stable identity and version to each Question Unit.
- [ ] Records source and target domain separately.
- [ ] Stores typed, multi-granularity factor mappings with semantic conditions.
- [ ] Records directional mappings without assuming symmetry.
- [ ] Distinguishes unknown relations from measured null effects.
- [ ] Separates analogy plausibility from verified scientific claims.
- [ ] Links historical assessments to evidence, context, and versioned scorers.
- [ ] Supports cold-start questions and reversible defer/revisit decisions.
- [ ] Logs score folding policies, uncertainty, and dependency controls.
- [ ] Preserves parent/child provenance through question transfer and relay.
- [ ] Separates question selection from exploration authorization.
- [ ] Enforces resource limits and prohibited actions.
- [ ] Preserves counter-evidence and explicit leftovers.
- [ ] Does not count correlated repeated observations as independent corroboration.
- [ ] Supports independent review and reproducible offline evaluation.

These are case-level checks and do not supersede the normative contracts in `SPEC-001` through `SPEC-004`.

## 18. Open Questions

1. Which UTN granularity is sufficient to preserve transferable semantics without making mapping prohibitively costly?
2. How should conflicting type alignments be represented and arbitrated?
3. Can directional influence be calibrated when downstream research outcomes are delayed or sparse?
4. How can a system distinguish useful structural novelty from merely unusual phrasing?
5. What is the correct treatment of negative transfer in historical question scoring?
6. When does human expert review improve semantic validity, and when does it introduce disciplinary bias?
7. How should question portfolios allocate budget to weakly supported but potentially high-impact transfers?
8. Can relay quality be measured without rewarding the production of many low-value derivative questions?
9. What conditions justify promoting a new recurring mapping into a UTN type or relation extension?
10. How much of the proposed method generalizes beyond software and sensor diagnostics?

## 19. Research Interpretation

The central proposal is **partial structural transfer with explicit contracts**, not cross-domain equivalence. AQSI may use a question that was productive in one domain as a source of *new, testable questions* in another. UTN provides a candidate semantic alignment layer; multi-granularity directional influence supports question comparison; historical outcomes inform but do not determine selection; exploration contracts preserve governance; and structural relay returns both successful and failed insights to the question ecosystem.

Whether this architecture improves discovery quality, cost efficiency, or cross-domain generality remains an empirical question. The proposed contribution of this case is a traceable, falsifiable design for investigating those claims.

## 20. Conclusion

Cross-domain autonomous questioning is best understood as a controlled transformation of research structures. The transferable unit is not a slogan, analogy, or unqualified answer. It is a versioned question with typed factors, explicit mapping conditions, uncertain influence estimates, bounded exploration, evidence provenance, and relay lineage. A successful AQSI implementation would make those transformations inspectable and experimentally comparable. Until such tests are completed, the case remains a research design rather than evidence of achieved autonomous scientific discovery.

---

## Appendix A — Minimal Question Transfer Envelope

```yaml
transfer_id: TRANSFER-CI-SN-001
source_question_id: QU-CI-017
target_question_id: QU-SN-102
source_domain: software-ci
target_domain: environmental-sensors
transfer_operator: partial-structural-analogy
utn_mapping_ref: MAP-CI-SN-001
retained_core:
  - intermittent-deviation
  - context-dependence
  - controlled-discrimination
changed_delta:
  - from: test-scheduling
    to: sensor-sampling-and-network-topology
excluded_assumptions:
  - identical-causal-mechanism
  - software-test-oracle
alignment_state: proposed
influence_state: estimated
verified_target_outcome: null
historical_assessment_refs: [HIST-CI-042]
policy_ref: POLICY-SN-RESEARCH-v0.1
status: hypothetical-example
```

## Appendix B — Illustrative Transfer Procedure

```text
INPUT: source question q_s, target-domain registry D_t,
       UTN contracts U, historical question records H,
       policy P, exploration budget B

1. Extract typed factors F_s and source assumptions A_s.
2. Retrieve target factors F_t under U.
3. Propose directed mappings M from F_s to F_t.
4. Validate type compatibility; preserve unknowns and exclusions.
5. Derive target question candidates Q_t via Core/Delta transformations.
6. Retrieve relevant history H_t without promoting source claims to facts.
7. Estimate influence, uncertainty, and candidate utility separately.
8. Select a diverse, budget-constrained question portfolio under P.
9. For each selected question, request an exploration contract.
10. Execute only authorized offline investigations.
11. Record evidence, counter-evidence, failures, and explicit leftovers.
12. Generate and validate relay pieces and derived questions.
13. Update history with provenance; preserve scorer and policy versions.
OUTPUT: audited question/relay lineage and evaluation artifacts.
```

## Appendix C — Publication and Research Notes

- **Document classification:** Illustrative research case, not a completed experiment.
- **Version:** v1.0.0.
- **Recommended location:** `cases/CASE-002-Cross-Domain-Question-Transfer.md`.
- **Suggested figure:** `figures/Fig-008-UTN-Cross-Domain-Relay-and-RSI.png` (optional cross-reference; do not imply the figure is present until added).
- **Related next case:** `CASE-003-Research-Portfolio-and-Multi-Agent-Relay.md`.
- **Licensing:** Intended for inclusion in the AQSI repository under its project-level Apache-2.0 license.
- **Citation:** Use the repository's published `CITATION.cff` and release DOI once actually assigned; no DOI is assumed here.
