# VALIDATION ROADMAP

## Autonomous Questioning Structural Intelligence (AQSI)

**Version:** v1.0.0 (research proposal)  
**Status:** Proposed validation plan; no experimental performance claims  
**Scope:** Question discovery, multi-granularity influence, historical question intelligence, exploration contracts, structural relay, strategic governance, and controlled recursive improvement.

> **Research stance.** AQSI is an architectural and algorithmic research program. The tests below are proposed, not reported results. Passing an interface conformance test does not establish scientific usefulness; producing questions does not establish knowledge gain; and iterative system changes do not establish recursive intelligence improvement.

---

## 1. Purpose and Validation Philosophy

The purpose of this roadmap is to convert the theoretical claims in `docs/AQSI-001` through `docs/AQSI-010`, the normative interfaces in `specs/SPEC-001` through `specs/SPEC-004`, and the questions in `TESTABLE-HYPOTHESES.md` into reproducible, staged investigations.

AQSI should be evaluated at four distinct levels:

1. **Contract conformance:** Are objects, state transitions, provenance, policies, and outputs well formed and traceable?
2. **Component validity:** Do individual mechanisms outperform appropriate simpler alternatives on prespecified metrics?
3. **System utility:** Does the integrated loop yield more independently validated research progress per unit of resource?
4. **Evolution validity:** Do proposed structural modifications produce repeatable, out-of-sample improvements without violating governance or degrading other critical capabilities?

No level substitutes for the next. An internally consistent influence graph may still be a poor predictor of useful research questions.

## 2. Research Objects and Measurement Units

| Object | Minimum record | Primary validation concern |
|---|---|---|
| Question Unit (QU) | Stable ID, version, UTN typing, provenance, factors, status | Identity and reproducibility |
| Structural factor | Type, granularity, domain, semantics, evidence | Semantic alignment and granularity |
| Influence record | Directed source/target, relation type, score, uncertainty, evidence | Predictive and relational validity |
| Historical outcome | Question/version, exploration context, cost, observed result, date | Leakage, selection bias, delayed effects |
| Portfolio decision | Candidate set, constraints, policy version, scorer version, selections | Fair comparison and resource accounting |
| Exploration contract | Authorized actor, task, data/tool scope, budget, evidence criteria | Compliance and auditability |
| Relay piece | Source lineage, transformation, target, evidence, limitations | Transfer quality and provenance |
| Structural change proposal | Baseline, change, expected benefit, tests, approval, rollback | Controlled improvement |

A **research episode** begins with a frozen candidate set and ends at a prespecified observation cutoff. Long-running descendants can be evaluated separately through delayed-outcome tracking.

## 3. Primary Outcomes and Guardrail Metrics

### 3.1 Primary outcome: Verified Research Yield (VRY)

Define, for evaluation window \(T\):

\[
\operatorname{VRY}(T)=\frac{\sum_{k\in \mathcal{V}(T)} w_k\,c_k}{\operatorname{Cost}(T)}
\]

Here \(\mathcal{V}(T)\) is the set of independently assessed research outputs meeting prespecified acceptance criteria, \(w_k\) is an ex-ante importance weight, and \(c_k\) is a confidence or quality weight assigned by blinded adjudication. Cost must be reported in both compute/tool consumption and human-review effort. This is a **candidate operational metric**, not a universal measure of intelligence; report its components separately to expose weighting sensitivity.

Accepted outputs may include reproducible defect discoveries, validated hypotheses, useful falsifications, verified transfer methods, or reproducible experimental protocols. A fluent answer, a high internal score, or a merely novel question is not sufficient.

### 3.2 Secondary outcomes

- **Question utility precision:** proportion of selected questions judged useful under blinded, preregistered criteria.
- **Coverage and diversity:** meaningful coverage of problem families and structural factors, not surface paraphrase diversity.
- **Calibration:** agreement between predicted utility/uncertainty and later observed outcomes (e.g., Brier score or calibration error when probabilistic predictions exist).
- **Time/cost to validated finding:** compute, tokens, tools, wall time, and human hours.
- **Relay reuse rate:** downstream uptake of a relay piece with independent utility checks.
- **Transfer validity:** verified benefit in target domain, including negative-transfer rate.
- **Revisit effectiveness:** useful recovery of previously deferred questions.
- **Portfolio robustness:** sensitivity to scoring weights, candidate-set perturbations, and policy changes.
- **Audit completeness:** traceable lineage, evidence and authorization for each accepted output.

### 3.3 Safety and governance guardrails

Measure unauthorized actions, policy violations, provenance loss, untraceable score changes, evidence double-counting, fabricated citations, leakage across splits, and failed rollback. Some governance failures are **hard stops**, not acceptable trade-offs against improved VRY.

## 4. Experimental Design Principles

1. **Preregister** hypotheses, primary endpoints, budgets, stopping criteria, and analysis plans before test execution.
2. **Use matched budgets** across systems, including human supervision and validation time.
3. **Freeze evaluation sets** and keep historical corpora temporally separated from later outcomes.
4. **Blind outcome assessors** to system identity where practical.
5. **Separate discovery from verification:** a system cannot validate its own research claims solely by agreeing with itself.
6. **Record all attempts**, including rejected questions, negative findings, abstentions, and policy blocks.
7. **Report uncertainty:** confidence intervals, effect sizes, sample sizes, and failure distributions.
8. **Run ablations** to isolate benefits from history, UTN, factor graphs, portfolio selection, relay, and governance.
9. **Retain explicit leftover:** unknown relations and unresolved findings must not silently become zeros or successes.
10. **Reproduce before generalizing:** repeated runs, multiple seeds/tasks, independent replication where feasible.

## 5. Baseline Systems and Ablations

Use a consistent suite, with equivalent tools and budgets:

| ID | Comparator | What it tests |
|---|---|---|
| B0 | Human-curated or static question queue | Value over established non-autonomous workflow |
| B1 | Vanilla LLM question generation and answer loop | Value over prompt-only autonomy |
| B2 | LLM + semantic retrieval/history snippets | Whether structured HQI exceeds simple retrieval |
| B3 | AQSI without historical scoring | Incremental value of HQI/QDT |
| B4 | AQSI without multi-granularity influence | Incremental value of factor relations |
| B5 | AQSI with symmetric or concept-only links | Value of directionality and granularity |
| B6 | AQSI without UTN alignment | Value of typed cross-domain mapping |
| B7 | AQSI with top-k greedy selection | Value of portfolio-aware selection |
| B8 | AQSI without structured relay | Value of persistent downstream learning |
| B9 | AQSI without meta-question updates | Value of controlled recursive changes |

Governance must **not** be disabled in live deployments to create a baseline. Policy experiments should be simulated or performed in appropriately isolated sandboxes.

## 6. M0 — Single-Domain Closed-Loop Feasibility

**Objective:** Demonstrate a reproducible and contract-conformant cycle in one bounded domain (suggested: CI flaky-test diagnosis, as developed in `cases/CASE-001-Single-Domain-Autonomous-Questioning.md`).

**Inputs:** Fixed issue corpus, documentation, test histories, candidate questions, authorized read-only tools, and a curated set of outcomes with held-out examples.

**Sequence:**

1. Ingest domain evidence and identify gaps, residuals, and candidate questions.
2. Create versioned Question Units with factor annotations and provenance.
3. Score candidates and select a budget-limited portfolio.
4. Generate exploration contracts and obtain explicit authorization.
5. Explore using allowed tools; archive evidence, counterevidence, and unresolved issues.
6. Create relay pieces and descendants; measure next-round outcomes.

**Conformance gates:** valid QU identity; deterministic provenance links; legal state transitions; complete budget logs; blocked unauthorized execution; reproducible replay of decisions.

**Performance tests:** B0/B1/B2 versus full M0, with matched budgets and blind outcome adjudication.

**Exit criteria (to be set before experiment):** all safety-critical contract checks pass; sufficient usable observations for statistical comparison; complete cost and evidence logs; no unresolved critical provenance or authorization defect. **No positive performance result is required to publish a valid negative finding.**

## 7. M1 — Historical and Multi-Granularity Scoring

**Objective:** Test whether historical question intelligence and directed multi-granularity factors improve prediction, ranking, and resource efficiency.

**Experiments:**

- Compare concept-only, symmetric, and multi-granularity directional influence models.
- Compare raw retrieval, historical-score models, and Question Differential Tree representations.
- Test cold-start questions, distribution shift, delayed reward, and intentionally misleading history.
- Evaluate unknown-edge handling versus treating missing links as zero.
- Compare greedy top-k selection against budgeted portfolios with complementarity and redundancy controls.

**Leakage control:** split by time, problem family, and source repository; do not allow descendants or near-duplicates of test questions into training history.

**Exit criteria:** calibration and utility results are reported with uncertainty, ablations, computational overhead, and documented failures. Promote a more complex model only when its benefits justify its additional cost and fragility.

## 8. M2 — Cross-Domain Transfer and Multi-Agent Relay

**Objective:** Determine whether typed alignment and structural relay improve research outcomes beyond independent single-domain agents.

**Cases:** `cases/CASE-002-Cross-Domain-Question-Transfer.md` and `cases/CASE-003-Research-Portfolio-and-Multi-Agent-Relay.md`.

**Experimental arms:** source-domain only; prompt analogy only; retrieval transfer; UTN alignment; UTN + factor scoring; full AQSI relay with independent validation.

**Key controls:** preserve domain-specific constraints; log mapping uncertainty; require target-domain evidence; detect false equivalence and negative transfer; keep agent discussions separate from external adjudication.

**Outcomes:** verified target-domain utility, negative-transfer incidence, reuse efficiency, provenance integrity, cross-agent disagreement resolution, and incremental cost.

**Exit criteria:** independently reviewed target-domain results, reproducible mappings, and no critical unapproved cross-agent/tool actions.

## 9. M3 — Meta-Questions and Controlled Recursive Evolution

**Objective:** Test whether AQSI can identify useful deficiencies in its own question-discovery and evaluation process and improve them under controlled change management.

**Procedure:**

1. Freeze baseline architecture, data, prompts, scorer, policy and evaluation suite.
2. Generate meta-questions about measured failures or structural residuals.
3. Convert proposed changes into versioned Structural Change Proposals (SCPs).
4. Test each change in an isolated sandbox against baseline and held-out tasks.
5. Run conformance, regression, calibration, robustness and policy tests.
6. Require authorized approval before adoption; retain rollback artifacts.
7. Evaluate longitudinal performance and unintended degradation after adoption.

**Disallow:** self-declared success, unrestricted self-modification, evaluation-set contamination, or silent modification of governance policies.

**Exit criteria:** documented out-of-sample improvements with uncertainty and replication, no critical regressions, traceable approvals and reversible changes. Failure to improve is an informative result.

## 10. Hypothesis-to-Experiment Matrix

The IDs below are **validation work-package IDs**; map them to the exact hypothesis IDs in `TESTABLE-HYPOTHESES.md` during preregistration rather than assuming numeric equivalence.

| Work package | Main question | Phase | Principal comparator | Evidence required |
|---|---|---|---|---|
| WP-01 | Does structure-first discovery find useful non-obvious questions? | M0–M1 | LLM-only | Blind utility and verified outcomes |
| WP-02 | Do directed multi-granularity factors predict useful influence? | M1 | Concept-only/symmetric | Calibration and downstream utility |
| WP-03 | Does historical intelligence reduce wasted exploration? | M1 | Retrieval-only/no-history | Cost-adjusted yield, missed opportunities |
| WP-04 | Do QDTs support useful variation and revisiting? | M1 | Flat history | Generalization, revisit quality |
| WP-05 | Does portfolio selection beat greedy ranking? | M1–M2 | Top-k | Budgeted yield, diversity, sensitivity |
| WP-06 | Do QU/contracts improve traceability and reproducibility? | M0–M2 | Unstructured prompts | Audit and replay success |
| WP-07 | Does structured relay create downstream value? | M0–M2 | No-relay | Verified descendant utility |
| WP-08 | Does UTN improve cross-domain transfer? | M2 | Text analogy only | Target-domain validation, negative transfer |
| WP-09 | Can strategic control preserve policy while enabling useful autonomy? | M2 | Static allocation | Compliance and research yield |
| WP-10 | Do meta-question-driven changes improve held-out outcomes? | M3 | Frozen architecture | Replicated gains, regressions, rollback |

## 11. Statistical and Evaluation Protocol

- **Unit of randomization:** task family or research episode, chosen to prevent contamination; cluster analysis where questions share ancestry.
- **Unit of reporting:** both question-level and episode-level, with family-level aggregation to avoid pseudo-replication.
- **Effect reporting:** absolute and relative differences, confidence intervals, failure counts, and resource consumption.
- **Multiple testing:** preregister primary hypotheses; adjust exploratory comparisons or label them exploratory.
- **Power planning:** determine sample size from a pilot variance estimate and meaningful minimum effect; do not fabricate a fixed power guarantee.
- **Sensitivity:** rerun with alternate weighting of VRY components, delayed-outcome windows, scorer thresholds, and portfolio budgets.
- **Missingness:** distinguish unknown, unobserved, blocked, deferred, and confirmed negative outcomes.
- **Human assessment:** use explicit rubrics, independent assessors, and disagreement reporting.

## 12. Contract Conformance Suite

### SPEC-001 — Canonical Question Unit

- Stable and versioned identities; valid UTN references and typed factors.
- Required provenance, uncertainty, evidence and lifecycle fields.
- Distinct question identity versus expression artifact; valid transitions.

### SPEC-002 — Influence and Scoring

- Directionality preserved; unknown not coerced to zero.
- Score range and calibration metadata recorded; dependencies and double-counting checked.
- Portfolio constraints, scorer versions and decision inputs reproducible.

### SPEC-003 — Exploration and Relay

- Authorization verified before tool action; budget and evidence criteria enforced.
- Evidence/counterevidence/leftover retained; relay transformations traceable.
- Repeated execution not automatically treated as independent corroboration.

### SPEC-004 — Control Plane and Policy

- Policy authority separated from question ranking and action execution.
- Policy versions and approvals logged; unauthorized policy changes rejected.
- Sandbox rollback and audit trail demonstrated.

**Gate rule:** critical failures block promotion, irrespective of performance improvements.

## 13. Data Governance and Reproducibility

Maintain a versioned experiment manifest with: dataset origin and rights; task split; candidate generator; model and prompt versions; factor schema and UTN mapping; scorer parameters; portfolio constraints; exploration contract; permitted tools; policy version; seeds; timestamps; evaluator rubric; outcomes; costs; relay lineage; and deviations from plan.

Publish reproducible artifacts where licensing and privacy permit. For restricted corpora, provide synthetic fixtures, schema examples, evaluation scripts, and sufficiently detailed protocols without disclosing protected data. Preserve negative results and failed mappings.

## 14. Risk Register and Stop Conditions

| Risk | Signal | Mitigation / stop condition |
|---|---|---|
| Novelty proxy gaming | Many novel questions, low verified yield | Use independent outcomes and budgeted yield |
| Historical selection bias | Strong training fit, poor cold-start utility | Temporal/family splits, exploration reserve |
| False structural analogy | High similarity, invalid target mapping | Typed contracts, target-domain validation |
| Influence score overconfidence | Poor calibration, hidden unknowns | Explicit unknowns, uncertainty tests |
| Evidence double counting | Correlated claims treated as independent | Dependency tracking and deduplication |
| Relay contamination | Descendant leakage into evaluation | Lineage-aware splits and audits |
| Portfolio monoculture | Repeated selection of familiar clusters | Diversity controls and sensitivity analysis |
| Unauthorized action | Tool call outside approved scope | Immediate halt and audit |
| Self-improvement overclaim | Internal score gain only | Held-out external validation |
| Governance drift | Silent policy or authority change | Immutable policy versioning and approval |

## 15. Deliverables and Milestones

| Stage | Deliverable | Decision gate |
|---|---|---|
| P0 — Design freeze | Dataset/task inventory, hypothesis map, preregistration, rubrics | Feasibility and permissions approved |
| P1 — Contract fixtures | Schemas, positive/negative tests, audit fixtures | Critical conformance passes |
| P2 — M0 study | Single-domain loop, matched baselines, outcome report | Evidence complete and reproducible |
| P3 — M1 study | History/factor/portfolio ablations, calibration report | Complexity justified or rejected |
| P4 — M2 study | Cross-domain and multi-agent transfer evaluation | Target-domain independent verification |
| P5 — M3 study | Meta-question SCP trials, regression/rollback results | Replicated improvements, if any |
| P6 — Research relay | Public protocols, negative results, open issues, follow-up QUs | Provenance and limitations documented |

These are **milestones, not promised dates or guaranteed successes**. A valid stage may conclude that a proposed AQSI component does not help.

## 16. Contribution Protocol for Collective Learning

External researchers can contribute a reproducible question-discovery benchmark, an alternative scoring/folding operator, a failure case, a negative-transfer example, a contract conformance test, or an independently replicated result. Contributions should specify the research question, evidence source, method, comparison baseline, costs, limitations, and suggested follow-up Question Units. Proposed changes to interfaces should include migration and compatibility implications.

## 17. Related Repository Documents

- [AQSI-010 — MVP Architecture and Recursive Evolution](docs/AQSI-010-MVP-Architecture-and-Recursive-Evolution.md)
- [AQSI-003 — Multi-Granularity Structural Influence Factors](docs/AQSI-003-Multi-Granularity-Structural-Influence-Factors.md)
- [AQSI-004 — Historical Question Intelligence and Differential Trees](docs/AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md)
- [AQSI-005 — Directional Question Scoring and Portfolio Selection](docs/AQSI-005-Directional-Question-Scoring-and-Portfolio-Selection.md)
- [AQSI-007 — Question Structural Relay and Collective Learning](docs/AQSI-007-Question-Structural-Relay-and-Collective-Learning.md)
- [AQSI-008 — Strategic Question Control Planes](docs/AQSI-008-Strategic-Question-Control-Planes.md)
- [AQSI-009 — UTN and Cross-Domain Question Transfer](docs/AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md)
- [SPEC-001 — Canonical Question Unit Contract](specs/SPEC-001-Canonical-Question-Unit-Contract.md)
- [SPEC-002 — Structural Influence and Scoring Contract](specs/SPEC-002-Structural-Influence-and-Scoring-Contract.md)
- [SPEC-003 — Question Relay and Exploration Lifecycle](specs/SPEC-003-Question-Relay-and-Exploration-Lifecycle.md)
- [SPEC-004 — Control Plane and Policy Conformance](specs/SPEC-004-Control-Plane-and-Policy-Conformance.md)
- [OPEN-QUESTIONS](OPEN-QUESTIONS.md)
- [TESTABLE-HYPOTHESES](TESTABLE-HYPOTHESES.md)
- [FUTURE-DIRECTIONS](FUTURE-DIRECTIONS.md)

---

## 18. Closing Principle

The long-term objective of AQSI research is not to maximize the number of questions or to assert a path to ASI. It is to test whether **typed, historically informed, directionally scored, contract-governed, structurally relayed questioning** can produce more reproducible knowledge and better research decisions under finite resources. Any claim of improvement must survive independent validation, explicit accounting of costs, and the possibility of disconfirmation.
