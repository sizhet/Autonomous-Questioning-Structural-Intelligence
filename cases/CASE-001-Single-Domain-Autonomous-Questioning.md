# CASE-001 — Single-Domain Autonomous Questioning

**Project:** Autonomous Questioning Structural Intelligence (AQSI)  
**Version:** v1.0.0 — Initial Research Framework  
**Document type:** Illustrative research case / proposed MVP  
**Status:** Design proposal; not an implemented or empirically validated system  
**Scope:** Single-domain software engineering research

## Abstract

This case develops a minimal, inspectable instance of Autonomous Questioning Structural Intelligence (AQSI) within one software engineering domain: diagnosing and reducing flaky automated tests. The aim is not to demonstrate that an AQSI system has already solved this problem, but to specify a reproducible question-discovery and exploration loop that could be built and compared with conventional LLM prompting. The case connects candidate discovery, multi-granularity structural influence, historical question intelligence, portfolio selection, exploration contracts, evidence and counter-evidence, and question-to-question structural relay. It also illustrates how a strategic control plane can allocate research effort without prescribing every individual question.

> **Evidence status:** All question records, influence scores, outcomes, and budgets below are synthetic teaching examples. They are not measurements, benchmark results, or claims of demonstrated superiority.

## 1. Research Purpose and Boundaries

The central question is whether a system that *selects and revises its own research questions* can produce a more useful, traceable sequence of investigations than an answer-only assistant given a fixed initial prompt.

The proposed MVP is deliberately constrained:

- **One domain:** flaky tests in a continuous-integration (CI) pipeline.
- **One bounded corpus:** test logs, failure metadata, test definitions, change history, and documented environment configuration, accessed only with authorization.
- **One question portfolio:** a small candidate set per cycle, selected under a fixed exploration budget.
- **One exploration mode:** read-only analysis first; any code changes or test reruns require separate authorization.
- **One evidence registry:** observed results, hypotheses, counter-evidence, uncertainty, and unresolved residuals remain distinguishable.

The case does **not** assume that a language model's explanation is a verified root cause, that all question relationships are measurable, or that an autonomous research loop has permission to modify production systems.

## 2. Scenario: Flaky CI Tests

A software team observes intermittent CI failures. Some tests pass locally but fail under parallel execution; others fail after changes to runtime or infrastructure. The team's initial question might be:

> Why do these tests fail intermittently?

That prompt is broad and can elicit plausible but weakly evidenced explanations. AQSI instead attempts to identify *which next questions are worth asking*, with each question linked to observable structures and possible tests.

### 2.1 Authorized information sources

| Source | Structural content | Possible limitations |
|---|---|---|
| CI execution records | test IDs, run IDs, timestamps, worker IDs, pass/fail events | incomplete retention, sampling bias |
| Test source and fixtures | setup/teardown, shared state, ordering assumptions | dynamic behavior may be hidden |
| Runtime configuration | parallelism, timeouts, operating system, dependency versions | configuration drift |
| Change history | code and dependency deltas | correlation is not causation |
| Historical investigations | prior questions, actions, evidence, outcomes | inconsistent labels, missing failures |
| Existing issue tracker | unresolved incidents, suspected causes | unverified reports |

All ingestion is subject to access controls, redaction rules, retention limits, and provenance tracking.

## 3. Minimal AQSI Objects

The MVP uses distinct objects rather than treating every artifact as free-form prompt text.

**Question Unit (QU).** A persistent, versioned research question with identity, structural factors, provenance, hypotheses, status, and references to scoring and evidence.

**Influence Record (IR).** A directed, context-specific estimate of how investigation of one question may inform another. It records factor-level support and uncertainty.

**Historical Question Record (HQR).** A past question and its observed exploration outcomes, including unsuccessful attempts and delayed relay contributions.

**Portfolio Decision (PD).** A recorded selection/defer decision with resource constraints, policy context, and scoring model version.

**Exploration Contract (EC).** A bounded plan stating the allowed actions, required evidence, stop conditions, budget, and reviewer or authorization boundary.

**Relay Piece (RP).** A transferable result, counterexample, method, derived question, or explicit leftover with traceable origin.

These objects align conceptually with `SPEC-001` through `SPEC-004`; this case is illustrative rather than a substitute for the normative specifications.

## 4. Step A — Discover Candidate Questions

A discovery cycle combines several channels:

1. **Gap-driven:** What causal variables are absent from current failure reports?
2. **Residual-driven:** Which incidents remain unexplained after earlier attempts?
3. **Association-driven:** Which test failures share structural factors, such as fixtures or execution workers?
4. **History-driven:** Which previous questions were informative, misleading, or prematurely abandoned?
5. **Structure-first:** Which missing links in the relation graph suggest a testable question?
6. **LLM-first:** Which candidate hypotheses can be proposed from authorized context, subject to structural checking?

An illustrative candidate set is:

| ID | Candidate question | Main source |
|---|---|---|
| Q-01 | Do failures correlate with parallel worker count after controlling for code revision? | gap / structure |
| Q-02 | Do failing tests share mutable fixtures or external resources? | association |
| Q-03 | Are timeout failures concentrated in a particular runtime version? | change / history |
| Q-04 | Can failure order be reproduced with an isolated test subset? | residual / experiment |
| Q-05 | Are previously reported “random” failures actually clustered by CI host? | history / structure |
| Q-06 | What additional instrumentation would distinguish timing contention from shared-state interference? | meta-question |

A candidate is not promoted merely because it sounds novel. It must have a coherent investigation target, provenance, and a plausible path to evidence, or be explicitly marked as speculative.

## 5. Step B — Multi-Granularity Structural Representation

Each question may be associated with heterogeneous structural factors:

$$
X(q)=\{(t_k, v_k, c_k, p_k)\}_{k=1}^{m}
$$

where `t` denotes a UTN-compatible factor type, `v` its value or reference, `c` its context, and `p` its provenance. This is a proposed representation, not a universal ontology.

For Q-01, factors might include:

- **Concept:** nondeterministic test outcome.
- **Attribute:** CI worker count.
- **Method:** stratified comparison by code revision.
- **Constraint:** no modification of production configuration.
- **Evidence target:** failure-rate differences with uncertainty intervals.
- **Residual:** unknown effects of shared fixtures.

For Q-02, factors include mutable fixture identity, test dependency edges, resource contention, and teardown semantics. A relation between Q-01 and Q-02 may therefore arise at the *method*, *attribute*, or *evidence* level, not just from semantic similarity between their titles.

### 5.1 Directionality matters

Investigating shared fixtures (Q-02) might help interpret worker-count effects (Q-01), but observing worker-count correlation alone may not identify which fixture is responsible. Therefore:

$$
I(Q\text{-}02\rightarrow Q\text{-}01)\ne I(Q\text{-}01\rightarrow Q\text{-}02)
$$

Both values are estimates under an explicit context. An unmeasured edge remains **unknown**, not automatically zero.

## 6. Step C — Historical Question Intelligence

Suppose a local question registry includes three prior investigations:

| Historical ID | Earlier question | Recorded outcome | Important caveat |
|---|---|---|---|
| H-01 | Are failures caused by test ordering? | partial evidence for one suite | does not generalize to all suites |
| H-02 | Does increasing timeout fix failures? | symptoms decreased, cause unresolved | mitigation is not diagnosis |
| H-03 | Are failures linked to shared fixtures? | investigation deferred | missing instrumentation, not disproved |

A historical scorer may estimate whether Q-02 resembles H-03 structurally and whether the missing instrumentation from H-03 is now available. It should not assign Q-02 a permanently low value merely because H-03 was deferred.

A proposed screening function is:

$$
\widehat V(q)=F_{\theta}(X(q),\mathcal H,\mathcal C)
$$

where `H` is the versioned history and `C` is current research context. The scorer returns a value estimate **and** confidence or uncertainty metadata. A candidate with little historical coverage may receive an exploration allocation rather than an unjustified rejection.

### 6.1 Question Differential Tree example

A possible shared core is **“identify the cause of intermittent failure.”** Deltas distinguish:

- execution-order hypothesis;
- worker-parallelism hypothesis;
- shared-fixture hypothesis;
- runtime-version hypothesis.

The differential tree supports retrieval and controlled comparison. It is not evidence that the branches share the same causal mechanism.

## 7. Step D — Directional Influence and Portfolio Selection

For illustration, let `I(i → j)` denote an estimated influence of resolving question `i` on the usefulness of exploring `j`, normalized to `[0, 1]` under one model version.

| Source → Target | Q-01 | Q-02 | Q-03 | Q-04 |
|---|---:|---:|---:|---:|
| **Q-01** | — | 0.3 | 0.2 | 0.6 |
| **Q-02** | 0.8 | — | 0.1 | 0.7 |
| **Q-03** | 0.2 | 0.1 | — | 0.3 |
| **Q-04** | 0.5 | 0.6 | 0.2 | — |

**Synthetic example only.** These values are chosen to illustrate asymmetry; they were not learned from CI data.

A simple goal-open baseline is:

$$
S(q_i)=\sum_{j\ne i} I(q_i\rightarrow q_j)
$$

This yields illustrative outgoing sums of `1.1`, `1.6`, `0.6`, and `1.3` for Q-01 through Q-04, respectively. The baseline is intentionally simple and does not imply that a high outgoing score is scientifically valuable.

A practical selector also considers historical estimates, evidence quality, uncertainty, cost, coverage, diversity, and policy constraints. One **illustrative** portfolio objective is:

$$
\max_{P\subseteq Q}\left[\sum_{q\in P}\widehat V(q)
+\lambda\,operatorname{Coverage}(P)
-\mu\,operatorname{Redundancy}(P)\right]
$$

subject to:

$$
\sum_{q\in P}operatorname{Cost}(q)\le B,
\qquad P\text{ satisfies policy constraints.}
$$

This objective is a candidate design, not a validated optimal formulation. If Q-01 and Q-02 largely overlap in their required data collection, selecting both may still be beneficial, but shared cost and evidence dependencies should be explicitly modeled rather than counted twice.

## 8. Step E — Create an Exploration Contract

Suppose Q-02 is selected for a read-only investigation. A compact contract could be:

```yaml
contract_id: aqsi-ec-flaky-002
version: "1.0"
question_ref: aqsi:question:Q-02
question_version: 1
purpose: "Assess whether failing tests share mutable fixtures or resources"
mode: read_only_analysis
allowed_sources:
  - ci_execution_records
  - test_source_repository
  - approved_issue_history
prohibited_actions:
  - modify_production_configuration
  - push_code_changes
  - execute_unapproved_external_requests
required_outputs:
  - evidence_records
  - counter_evidence_records
  - uncertainty_assessment
  - residual_questions
  - provenance_links
stop_conditions:
  - budget_exhausted
  - insufficient_authorized_data
  - safety_or_policy_violation
  - explicit_human_stop
authorization:
  execution_scope: read_only
  approver_for_expansion: human_reviewer
```

The contract is a **conceptual YAML example**, not a claim of conformance to a machine-validated schema. A future implementation must reconcile exact fields and state transitions with the repository's normative specifications.

## 9. Step F — Explore and Distinguish Evidence from Hypothesis

A possible investigation would:

1. Group failure events by test, fixture, worker, and revision.
2. Compare failing and passing runs under similar conditions.
3. Identify shared fixture/resource patterns.
4. Examine alternative explanations, including host load and timeout configuration.
5. Record which observations are independent and which derive from the same log batch.
6. Propose a controlled rerun or instrumentation change **only as a separately authorized next action**.

Illustrative output classification:

| Record | Content | Status |
|---|---|---|
| E-01 | Two failing tests reference the same fixture | hypothetical observation for case illustration |
| HYP-01 | Fixture mutation causes the failures | unverified hypothesis |
| CE-01 | Some failures occur without that fixture | hypothetical counter-evidence |
| R-01 | Need to distinguish fixture reuse from worker contention | explicit leftover |

Even if E-01 were observed, it would not by itself establish HYP-01. The contract requires that competing explanations remain visible.

## 10. Step G — Structural Relay and New Questions

The exploration result is packaged into a relay piece with parent question, method, evidence references, limitations, and derived questions. Possible follow-up questions include:

- **Q-07:** Does fixture isolation remove the failure under controlled worker counts?
- **Q-08:** Which shared-resource access patterns predict the observed failures?
- **Q-09:** Does the same failure mechanism appear in another test suite?
- **Q-10:** What instrumentation most efficiently separates the two competing hypotheses?

Q-07 and Q-08 are not assumed to be useful merely because they are descendants of Q-02. They re-enter discovery, scoring, and portfolio selection as independently assessable Question Units.

### 10.1 Repeated-execution relay

A rerun of an authorized test experiment can contribute new data, calibration, or reproducibility evidence. Repeating the same execution without new information may still be logged, but it must not be represented as independent corroboration when results share the same underlying dependencies.

### 10.2 Failed investigations are relayable

An investigation stopped by insufficient data can still yield a reusable **missing-observation specification**. For example, “worker ID is not retained in older logs” is a concrete residual that may guide future instrumentation planning.

## 11. End-to-End MVP Loop

The proposed loop is:

```text
Authorized domain data + historical question registry
                     |
                     v
        Discover candidate Question Units
                     |
                     v
      Represent multi-granularity factors
                     |
                     v
      Retrieve historical question evidence
                     |
                     v
       Estimate directed influence + value
                     |
                     v
       Select a policy-compliant portfolio
                     |
                     v
       Define exploration contracts
                     |
                     v
          Execute authorized analysis
                     |
                     v
       Record evidence / counter-evidence
                     |
                     v
       Relay results + explicit leftovers
                     |
                     +----> update history and models
                     |
                     +----> generate next candidate questions
```

A minimal research implementation may begin with a human-reviewed spreadsheet or structured JSON registry and manually approved exploration steps. Full agent autonomy is not required to test whether the question-centric architecture adds value.

## 12. Strategic Control Plane in a Single Domain

A human research owner may set a policy such as:

- prioritize **diagnostic clarity** over quick symptom suppression;
- permit read-only log and source analysis;
- reserve a portion of the budget for novel, uncertain hypotheses;
- require human approval before test reruns or code changes;
- record evidence provenance and unresolved questions.

The policy does not dictate that Q-02 must be chosen. It governs the permissible research direction and action boundaries while the question scorer and portfolio selector recommend concrete investigations.

A recommendation to expand access or modify code is a **policy proposal**, not an authorization.

## 13. Conformance Checks for the Case

The following checks are suitable for an early test harness:

| Check | Expected behavior |
|---|---|
| C-01 Identity | Each question has a stable identifier and version |
| C-02 Provenance | Every candidate records its discovery source |
| C-03 Factor typing | Structural factors have explicit types and contexts |
| C-04 Directionality | Influence records preserve source and target order |
| C-05 Unknown edges | Missing influence values are not silently treated as zero |
| C-06 Historical separation | Prior outcomes remain distinct from current predictions |
| C-07 Evidence integrity | Hypotheses and observations are not conflated |
| C-08 Authorization | Selection never grants unapproved execution rights |
| C-09 Relay lineage | Derived questions point to source records |
| C-10 Failure retention | Negative and inconclusive outcomes remain retrievable |
| C-11 Budget | Selected work fits authorized limits |
| C-12 Revisit | Deferred questions can be reconsidered when context changes |

These are proposed case-level checks; full normative requirements remain in `SPEC-001`–`SPEC-004`.

## 14. Evaluation Design

### 14.1 Baselines

Compare at least four approaches under matched data access, tool permissions, and compute budgets:

- **B0 — Fixed-prompt LLM:** answer the initial broad diagnostic question.
- **B1 — LLM question brainstorming:** generate questions without a persistent structural registry.
- **B2 — AQSI without history:** use structural discovery and selection, but no learned historical scoring.
- **B3 — Full proposed MVP:** structural discovery, history, directed influence, portfolio selection, and relay.

Optional ablations remove directionality, factor granularity, or relay feedback one at a time.

### 14.2 Outcome metrics

| Metric | Operational interpretation |
|---|---|
| Verified diagnostic yield | proportion of investigations producing externally checked findings |
| Cost per useful finding | authorized effort divided by validated information gained |
| Question redundancy | fraction of questions repeating equivalent investigations |
| Calibration | agreement between predicted value and observed utility |
| Novel useful coverage | validated hypotheses or factors absent from the initial question set |
| Counter-evidence retention | completeness of recorded disconfirming observations |
| Relay utility | downstream validated value of derived questions |
| Governance compliance | rate of policy and authorization violations |

Evaluation should be blinded where possible, include multiple projects or incident groups, and report confidence intervals rather than single-point success claims.

### 14.3 Avoiding evaluation leakage

Historical question records used for scoring must not include outcomes from held-out evaluation incidents. Split by incident family or time window, not merely by paraphrased question text. Otherwise a system could appear to predict high-value questions by recalling their already-known answers.

## 15. Testable Hypotheses and Falsifiers

**H1 — Discovery yield.** AQSI's combined discovery channels identify more *validated, nonredundant* diagnostic questions per fixed budget than B1. **Falsifier:** no reliable improvement across held-out incidents.

**H2 — Historical screening.** Historical Question Intelligence reduces repeated low-yield investigations without materially suppressing genuinely novel findings. **Falsifier:** savings disappear after controlling for selection bias, or novel yield falls disproportionately.

**H3 — Directional influence.** Directed factor-level influence improves portfolio selection over undirected similarity alone. **Falsifier:** directionality provides no measurable benefit in controlled ablations.

**H4 — Structural relay.** Explicit relay records improve downstream question quality and traceability. **Falsifier:** downstream value and auditability are unchanged.

**H5 — Evidence discipline.** Exploration contracts reduce unsupported causal claims and unauthorized actions. **Falsifier:** no reduction in adjudicated violations relative to equivalent controls.

**H6 — Revisit mechanism.** Deferred questions revisited after new evidence produce useful discoveries that permanent pruning would miss. **Falsifier:** revisit cost consistently exceeds verified information gain.

These are research hypotheses, not reported findings.

## 16. Failure Modes and Mitigations

**Historical lock-in.** Prior failed attempts can unfairly suppress new questions. Mitigation: uncertainty-aware exploration quotas and revisit triggers.

**Spurious structural influence.** Shared vocabulary or fixtures can inflate scores without causal relevance. Mitigation: factor provenance, counterfactual checks, and held-out validation.

**Popularity bias.** Frequently discussed issues may dominate question portfolios. Mitigation: coverage constraints and calibrated novelty budgets.

**Metric gaming.** Optimizing question counts or model agreement may reduce scientific value. Mitigation: independent evidence adjudication and cost-adjusted outcomes.

**Evidence duplication.** Multiple logs from one root event may be mistaken for independent support. Mitigation: dependency-aware evidence records.

**Unbounded question growth.** Recursive generation can exhaust resources. Mitigation: bounded portfolios, stop conditions, explicit leftovers, and deferred queues.

**Authorization drift.** Research recommendations may be misread as permission to execute. Mitigation: separate selection and action authorization contracts.

**Ontology overreach.** A rigid UTN mapping may hide domain-specific meaning. Mitigation: local types, explicit partial alignment, and unknown relations.

## 17. Phased Implementation Plan

**M0 — Manual inspectable loop.** Curate 10–30 historical questions, construct a small candidate portfolio, and log decisions and evidence manually. Goal: test whether object boundaries and records are usable.

**M1 — Structured retrieval and scoring.** Add typed factors, question differential trees, historical retrieval, and directed influence estimation. Goal: evaluate scoring and screening ablations.

**M2 — Authorized exploration orchestration.** Connect read-only diagnostic tools, formalize exploration contracts, and create provenance-linked relay pieces. Goal: test end-to-end traceability and governance.

**M3 — Controlled improvement.** Allow the system to propose revisions to discovery and scoring rules, evaluate them on held-out cases, and require approval before deployment. Goal: study recursive improvement without self-certifying its own gains.

No phase implies unrestricted autonomous action or guaranteed performance improvement.

## 18. Expected Research Artifacts

A replicable study should publish, subject to privacy and licensing constraints:

1. A documented Question Unit dataset and factor typing guide.
2. Historical question records with explicit missing-data indicators.
3. Influence estimates and scorer versions.
4. Portfolio decisions with budgets and policy references.
5. Exploration contracts and redacted evidence traces.
6. Relay lineage and unresolved residuals.
7. Baseline and ablation protocols.
8. Negative results and known failure cases.

Where raw CI logs cannot be released, publish synthetic schemas, redacted examples, and reproducible evaluation procedures instead of claiming unrestricted reproducibility.

## 19. Relationship to the AQSI Research Series

| Document | Contribution to this case |
|---|---|
| `AQSI-001-From-Answering-to-Autonomous-Questioning.md` | Question-centric research motivation |
| `AQSI-002-Biomimetic-Question-Discovery.md` | Candidate discovery channels |
| `AQSI-003-Multi-Granularity-Structural-Influence-Factors.md` | Factor-level directional relationships |
| `AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md` | Historical screening and structural retrieval |
| `AQSI-005-Directional-Question-Scoring-and-Portfolio-Selection.md` | Portfolio selection principles |
| `AQSI-006-Question-Units-and-Exploration-Contracts.md` | Research objects and bounded exploration |
| `AQSI-007-Question-Structural-Relay-and-Collective-Learning.md` | Derived questions and relay provenance |
| `AQSI-008-Strategic-Question-Control-Planes.md` | Human strategic authority and budgets |
| `AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md` | Typed alignment foundations; transfer is out of scope here |
| `AQSI-010-MVP-Architecture-and-Recursive-Evolution.md` | System integration and phased validation |
| `SPEC-001`–`SPEC-004` | Canonical object, scoring, lifecycle, and policy contracts |

## 20. Conclusion

This case proposes a bounded single-domain AQSI research loop in which questions are discoverable, structurally represented, historically evaluated, selected under policy and budget constraints, explored under explicit contracts, and relayed into further research. Its distinctive testable proposition is that **the research question itself can become a persistent, scored, transferable, and revisable intelligence unit**, rather than a disposable prompt preceding an answer.

The case does not establish that AQSI improves diagnostic accuracy or research productivity. Its value at this stage is to make the claim precise enough to implement, compare, challenge, and potentially falsify. Positive results would justify broader experiments; negative results should be preserved as historical question intelligence and used to revise the architecture.

---

**Suggested repository location:** `cases/CASE-001-Single-Domain-Autonomous-Questioning.md`  
**Suggested companion figure:** `figures/Fig-001-AQSI-Grand-Architecture.png` (architecture overview, not experimental evidence)  
**License:** Apache-2.0 (repository-level license governs this document)
