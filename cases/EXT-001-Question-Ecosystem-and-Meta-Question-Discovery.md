# EXT-001 — Question Ecosystem and Meta-Question Discovery

**Project:** Autonomous Questioning Structural Intelligence (AQSI)  
**Document type:** Research Extension / Directional Hypothesis  
**Version:** 1.0.0  
**Status:** Theory-first proposal; not an empirical performance claim  
**License:** Apache-2.0 (repository-level)

## Abstract

An autonomous questioning system should not be evaluated solely by the number or apparent novelty of questions it produces. Questions form an evolving ecosystem: they share structural components, compete for finite exploration resources, support or undermine one another, generate descendants, and alter the methods by which subsequent questions are discovered. This extension proposes a **Question Ecosystem (QE)** as a typed, provenance-aware, multi-granularity research structure, and **Meta-Question Discovery (MQD)** as the process of asking evidence-seeking questions about that ecosystem and its own discovery mechanisms. The proposal integrates Question Units, UTN alignment, Question Differential Trees, directional structural influence, Historical Question Intelligence, Structural Relay, and human-governed research portfolios. It defines candidate mechanisms, contracts, failure modes, experiments, and falsification criteria without presuming that recursive questioning produces scientific progress or general intelligence.

**Keywords:** autonomous questioning; question ecosystem; meta-question; structural intelligence; directional influence; UTN; question differential tree; research portfolio; collective learning; recursive improvement.

---

## 1. Motivation: From a Question Queue to an Evolving Ecosystem

A queue represents questions as largely independent work items. In practice, a question may:

- expose a missing premise of another question;
- share a method with a distant research domain;
- invalidate a high-ranked line of inquiry;
- create reusable evidence, instruments, or evaluation criteria;
- produce several more precise descendant questions;
- become worth revisiting after a new result or policy change.

Consequently, optimizing a static list can overlook valuable **relations, dependencies, and delayed effects**. AQSI proposes that question discovery, selection, exploration, and relay should operate over an evolving, explicitly represented ecology rather than a one-time prompt collection.

The term *ecosystem* is an architectural analogy. It does not imply biological reproduction, agency, or an independently validated theory of scientific evolution.

### 1.1 Research proposition

> A typed, history-aware question ecosystem may yield more useful and reproducible research trajectories than isolated question generation and ranking, when compared under matched resources and independent evaluation.

This is a testable proposition, not a demonstrated outcome.

## 2. Scope and Boundaries

This extension addresses three coupled problems:

1. **Ecosystem representation:** How should questions, evidence, methods, dependencies, and exploration histories be represented and updated?
2. **Meta-question discovery:** How can the system identify useful questions about its own question-generation, scoring, relay, and governance mechanisms?
3. **Controlled ecosystem evolution:** How can proposed changes be evaluated and admitted without unbounded self-modification?

It does **not** assert that every question is valuable, that novelty implies discovery, or that autonomous self-improvement necessarily converges to better science or ASI.

## 3. Core Definitions

### 3.1 Question Unit (QU)

A **Question Unit** is a versioned research object with identity, typed structural features, provenance, evidence links, historical assessments, exploration state, and relay references. A natural-language prompt is one possible expression of a QU, not its canonical identity. See `SPEC-001-Canonical-Question-Unit-Contract.md`.

### 3.2 Question Ecosystem (QE)

At time $t$, let:

$$
\mathcal E_t=(Q_t,F_t,R_t,H_t,P_t,C_t),
$$

where:

- $Q_t$: active, deferred, completed, and archived Question Units;
- $F_t$: typed structural factors, including concepts, attributes, methods, constraints, evidence, residuals, and transfer points;
- $R_t$: typed, directed, evidence-qualified relations among questions and factors;
- $H_t$: historical explorations, assessments, outcomes, and counter-evidence;
- $P_t$: research portfolios, dependencies, budgets, and selection decisions;
- $C_t$: policy, authority, provenance, and conformance records.

This is a logical model, not a requirement to store all data in one graph database.

### 3.3 Meta-Question (MQ)

A **Meta-Question** is a Question Unit whose subject is a mechanism or property of the questioning system itself. Examples:

- Which discovery channels produce independently validated, reusable questions?
- When does history-based screening suppress genuinely new directions?
- Which UTN alignments generate spurious cross-domain influence?
- Does the portfolio over-invest in densely connected question families?
- Under what conditions does repeated exploration add independent evidence?

A meta-question requires the same provenance, evidence, authorization, and falsifiability discipline as an ordinary question.

### 3.4 Ecosystem Evolution

An ecosystem change may modify question relations, factor types, historical models, portfolio policies, or the *proposed* discovery/scoring procedures. Changes to system behavior require separate evaluation and authorization; merely generating a meta-question never grants permission to deploy a change.

## 4. Multi-Granularity Ecosystem Representation

A question's structural signature can be modeled as:

$$
X(q)=\{(f_k,\tau_k,g_k,p_k,e_k)\}_{k=1}^{m_q},
$$

where $f_k$ is a factor, $\tau_k$ its UTN-compatible type, $g_k$ its granularity, $p_k$ its provenance, and $e_k$ its evidence or uncertainty metadata.

Relevant relation families include:

| Relation | Directional interpretation | Typical evidence |
|---|---|---|
| `depends_on` | Q2 needs an answer, instrument, or premise from Q1 | dependency analysis |
| `enables` | Q1 may make Q2 cheaper or more testable | historical experiment |
| `contradicts` | a result for Q1 may weaken a premise of Q2 | counter-evidence |
| `shares_method` | method from Q1 may transfer to Q2 | typed method alignment |
| `refines` | Q2 narrows or makes Q1 testable | question differential |
| `transfers_to` | source structure may inform a target domain | validated mapping |
| `duplicates` | exploration overlaps substantially | semantic and evidence audit |
| `generates` | Q1's exploration produced Q2 | relay provenance |

These relations should not be collapsed into an undifferentiated similarity edge. An unknown relation is not a zero-valued influence, and a proposed relation is not a verified one.

### 4.1 Directed influence

A candidate influence estimate may take the form:

$$
\widehat I_t(q_i\!\to\!q_j)=
operatorname{Fold}_{(a,b)\in\mathcal A_{ij}}
\bigl[w_{ab,t}\,r_t(f_{ia},f_{jb})\bigr],
$$

where $\mathcal A_{ij}$ is an admissible set of typed factor pairs, $r_t$ estimates a relation, and `Fold` is an explicitly versioned operator. Its output must carry a scale, uncertainty, provenance, and evidence-dependence metadata. In general:

$$
\widehat I_t(q_i\!\to\!q_j)\neq\widehat I_t(q_j\!\to\!q_i).
$$

This estimate is **not** a direct measure of verified scientific importance. Calibration must be tested against independent downstream outcomes.

## 5. Ecosystem Dynamics and Question Families

### 5.1 Events rather than silent overwrites

Useful event types include `QUESTION_CREATED`, `FACTOR_ALIGNED`, `RELATION_PROPOSED`, `RELATION_REFUTED`, `EXPLORATION_COMPLETED`, `EVIDENCE_ATTACHED`, `QUESTION_DERIVED`, `QUESTION_DEFERRED`, `QUESTION_REVISITED`, `POLICY_CHANGED`, and `MODEL_VERSION_EVALUATED`.

An event should record actor, time, version, source, authorization context, and affected identifiers. Derived material must not erase the original evidence or negative results.

### 5.2 Question Differential Trees (QDT)

A family of questions can share a structural core and differ in domain-specific deltas:

$$
q_k=operatorname{Instantiate}(\mathrm{Core}_{\mathcal F},\Delta_k).
$$

QDTs can expose repeated dead ends, useful refinements, untested branches, and transferable methods. A tree is one view of a richer ecosystem: a question may participate in multiple overlapping families, and cross-family relations need not be tree-shaped.

### 5.3 Birth, merge, defer, revisit, retire

Question lifecycle operations should be explicit and reversible where possible:

- **Birth:** introduce a candidate with provenance and a minimum structural signature.
- **Merge/link:** retain distinct identities unless equivalence is demonstrated; record why they were grouped.
- **Defer:** pause exploration based on current evidence, budget, or policy, not a permanent declaration of worthlessness.
- **Revisit:** reopen after new evidence, improved tools, changed dependencies, or altered policy.
- **Retire:** preserve an archival record and reactivation criteria.

## 6. Sources of Meta-Questions

Meta-questions should be generated from observable ecosystem residuals, not only from unrestricted LLM introspection.

### 6.1 Coverage and representation residuals

Examples: unrepresented question families; repeated “unknown” relation types; incompatible UTN mappings; missing evidence schemas; unexplained cross-domain failures.

### 6.2 Historical performance residuals

Examples: high predicted value with low realized value; successful questions consistently screened out; uncalibrated confidence; systematic delayed benefits ignored by short-horizon scoring.

### 6.3 Portfolio and governance residuals

Examples: excess concentration in a fashionable domain; starvation of foundational work; budget consumption without falsifiable outcomes; unauthorized transitions; policies whose consequences diverge from stated intent.

### 6.4 Relay and collective-learning residuals

Examples: derived questions lose provenance; teams repeat the same failed method; counter-evidence does not propagate; a relay is technically accepted but semantically invalid.

### 6.5 Adversarial and negative-case generation

A meta-question may challenge a system's favored assumption: “What evidence would show that this scoring model is merely rewarding network centrality?” Such questions deserve protected exploration capacity when permitted by policy.

## 7. Meta-Question Discovery Operators

The following are **candidate operators**, not a claim of a complete algorithm:

| Operator | Input | Candidate output |
|---|---|---|
| `InspectResidual` | unexplained mismatch | Why did the predicted outcome fail? |
| `ChallengeScorer` | ranking and realized outcomes | Which factor caused miscalibration? |
| `AuditCoverage` | question family / domain map | Which research region is unrepresented? |
| `TraceRelay` | relay lineage | Where was meaning or provenance lost? |
| `ComparePortfolios` | alternative allocations | Which policy produces stronger validated learning? |
| `ProbeTransfer` | UTN cross-domain mapping | Under which constraints does transfer fail? |
| `GenerateCounterexample` | a proposed general rule | What minimal case would falsify it? |
| `QuestionTheQuestion` | an existing QU | Is the formulation answerable, useful, or biased? |

Each operator produces a **candidate QU** and an explanation of its derivation. The operator does not certify the value of its own output.

## 8. First-Order and Higher-Order Questioning

A useful distinction is:

- **Level 0:** domain questions (e.g., “What causes intermittent sensor failures?”).
- **Level 1:** questions about question selection or exploration (e.g., “Which sensor-failure questions were wrongly deprioritized?”).
- **Level 2:** questions about how Level 1 mechanisms are evaluated (e.g., “Does our meta-evaluator systematically favor easy-to-measure corrections?”).

The levels are relative to a given research objective, not a fixed ontology. Unrestricted recursion is neither necessary nor desirable. AQSI should bound meta-question depth, budget, and rate; require measurable hypotheses; and use independent checks before adopting any proposed system changes.

## 9. Historical Question Intelligence for Ecosystem Learning

Let a historical record include:

$$
h_i=(q_i,X_i,\widehat s_i,o_i,c_i,d_i,v_i),
$$

where $\widehat s_i$ is a prior score, $o_i$ the observed outcome, $c_i$ exploration cost, $d_i$ descendant/relay effects, and $v_i$ evaluation context and version.

Historical retrieval may improve candidate screening and meta-question generation, but three biases require explicit controls:

1. **Selection bias:** explored questions are not a random sample of all candidates.
2. **Delayed-value bias:** a question's most useful descendants may appear later.
3. **Novelty suppression:** unfamiliar structures may be rejected for lack of analogues.

Store rejected/deferred candidates and selection propensities where feasible. Use exploration quotas and counterfactual evaluation cautiously; never treat missing outcomes as observed failures.

## 10. Ecosystem-Aware Question Scoring

### 10.1 Baseline directional influence

For a candidate pool $Q$, a goal-open baseline is:

$$
S_{\mathrm{influence}}(q_i)=\sum_{q_j\in Q,\,j\neq i}\widehat I(q_i\!\to\!q_j).
$$

This is a structural heuristic, not a universal measure of research merit. Scores may be biased by pool size, graph density, or duplicated question families.

### 10.2 Distinct assessment dimensions

A proposed scoring record may preserve rather than prematurely collapse:

- estimated enabling influence;
- historical evidence of useful outcomes;
- uncertainty and expected information gain;
- feasibility, cost, and testability;
- potential for cross-domain relay;
- novelty and family coverage;
- policy alignment and eligibility.

Multi-dimensional records support alternative folding policies and make evaluator disagreement inspectable. They do not require separate ad-hoc bonuses for every factor: multi-granularity relations may already encode some effects. Double counting must be audited.

### 10.3 Portfolio-level selection

Given budget $B$, choose an authorized set $P\subseteq Q$:

$$
\max_{P}\; U(P\mid\mathcal E_t,\pi_t)
\quad\text{subject to}\quad
\sum_{q\in P}c(q)\le B,\quad P\in\mathcal C(\pi_t),
$$

where $\pi_t$ is the human-authorized policy and $\mathcal C$ its admissible portfolios. The objective may account for complementarity, redundancy, uncertainty, and portfolio diversity, with all weights and versions recorded. A high score never grants execution authority.

## 11. Meta-Question-to-Improvement Lifecycle

The proposed controlled cycle is:

1. **Observe:** collect outcome, calibration, coverage, relay, and governance residuals.
2. **Generate:** create typed meta-question candidates with explicit provenance.
3. **Screen:** compare with historical meta-questions; preserve cold-start opportunities.
4. **Select:** allocate a bounded meta-research portfolio under policy.
5. **Explore:** test hypotheses with approved methods and independent evaluation.
6. **Propose change:** submit a versioned candidate modification, not a live mutation.
7. **Conformance gate:** check schema, evidence, authorization, regression, and rollback conditions.
8. **Compare:** evaluate against a frozen baseline on held-out or prospective tasks.
9. **Authorize:** obtain the required human or delegated approval.
10. **Relay:** preserve results, failures, new questions, and explicit leftover.

A negative outcome is still a legitimate relay result if it updates evidence or avoids repeated mistakes.

## 12. Illustrative Worked Example: A Misleadingly Central Question

*All entities and numbers in this example are hypothetical.*

Suppose a software reliability AQSI ranks a question about a popular logging framework highest because it shares many terms and methods with other questions. After exploration, the work yields little reusable evidence. Meanwhile, a less connected question about nondeterministic scheduling reveals a testable causal mechanism and generates several useful follow-ups.

A meta-question is created:

> “Does our structural influence scorer overvalue high-degree question families while undervaluing low-degree causal hypotheses?”

The system constructs two pre-registered comparisons:

- **A:** original scorer with historical filtering;
- **B:** degree-calibrated scorer with protected novel-question allocation.

Both receive matched budgets, equivalent candidate pools, blinded outcome adjudication, and identical authority constraints. The meta-question is supported only if B shows a reproducible advantage on pre-specified outcomes. If not, the result is recorded as counter-evidence. No scorer is automatically replaced.

The example illustrates a disciplined *route* from ecosystem observation to meta-question to potential improvement, not proof that the route works.

## 13. Structural Relay and Collective Learning

A useful relay piece may include:

```yaml
relay_id: relay:aqsi:example-001
source_question: qu:aqsi:meta-centrality-bias
relay_kind: evaluator-failure-analysis
claim_status: hypothesis
structural_core:
  type: scoring-bias
  affected_factor_types: [question-family, graph-degree, historical-outcome]
evidence_refs: []
counter_evidence_refs: []
transfer_conditions:
  - comparable_candidate_pools
  - documented_score_normalization
known_limits:
  - no_empirical_validation_yet
provenance:
  source: illustrative-extension-example
  version: 1.0.0
```

Relay should carry semantic preconditions, not just an attractive analogy. Other domains may import a **question about degree bias** without importing the unverified conclusion that such bias exists in their systems. Repeated execution counts as relay when it yields traceable data or reproducibility evidence, but correlated repeats are not automatically independent confirmation.

## 14. UTN and Cross-Domain Meta-Question Transfer

UTN provides candidate mechanisms for stable identity, typing, semantic alignment, and naming across heterogeneous question ecosystems. A meta-question about “false equivalence between intermittent events” might transfer from software tests to sensor networks if the underlying failure modes, observation models, and experimental constraints are aligned explicitly.

A transfer contract should specify:

- source and target domain types;
- shared structural core and target-specific deltas;
- valid and invalid analogy conditions;
- evidence that survives transfer versus evidence requiring re-collection;
- uncertainty and validation obligations.

A successful transfer may suggest new UTN types or relations; such ontology changes require versioning and conformance checks. **AQSI–UTN co-evolution** remains a research hypothesis.

## 15. Governance and Strategic Question Control Planes

A question ecosystem may serve researchers, institutions, or public-interest programs. Human-authorized policies may define strategic areas, budget envelopes, data-access limits, risk tolerances, and protected exploration allocations. AQSI can propose portfolio changes and policy questions, but must not treat its own meta-analysis as permission to override strategic authority.

Keep distinct:

1. **Discovery authority:** permission to generate and evaluate candidate questions.
2. **Selection authority:** permission to allocate research attention within policy.
3. **Execution authority:** permission to perform a particular experiment or tool action.
4. **Policy-change authority:** permission to modify the rules governing the above.

See `AQSI-008-Strategic-Question-Control-Planes.md` and `SPEC-004-Control-Plane-and-Policy-Conformance.md`.

## 16. Minimal Reference Architecture

```text
Domain Knowledge / UTN / Question History / Relay Residuals
                           |
                           v
                 Candidate Question Discovery
                           |
                           v
              Typed Question Units + QDT Views
                           |
                           v
          Multi-Granularity Relation / Influence Store
                           |
                           v
         Historical Scoring + Portfolio Control Plane
                           |
                    Authorized Exploration
                           |
                           v
                Evidence / Counter-Evidence
                           |
                           v
             Structural Relay + Ecosystem Update
                           |
                           v
             Residual Monitor / Meta-Question Discovery
                           |
                           v
           Sandbox Evaluation / Conformance / Approval
                           |
                           +------> Versioned Model or Policy Proposal
```

The diagram is a logical decomposition. A first MVP may implement it with files, a relational database, and a small number of interchangeable evaluators.

## 17. MVP Research Program

### M0 — Observable single-domain ecosystem

Create a versioned Question Unit registry, relation records, history store, and exploration log. Compare against a flat question queue. Measure provenance completeness, deduplication quality, and evaluator agreement.

### M1 — History and multi-granularity influence

Introduce typed factor relations, QDT family views, calibrated historical retrieval, and directional influence scoring. Compare with text-only similarity and history-free ranking under matched budgets.

### M2 — Meta-question generation in a sandbox

Generate meta-questions from documented errors, missed opportunities, and policy residuals. Evaluate their answerability, causal specificity, and downstream improvements; compare against unconstrained LLM meta-prompts.

### M3 — Controlled recursive improvement

Allow the system to *propose* scorer, representation, or discovery changes. Require frozen baselines, held-out evaluations, regression tests, rollback plans, and approval before deployment.

### M4 — Cross-domain and multi-agent relay

Test UTN-aligned transfer and distributed evidence accumulation. Track semantic drift, duplicated work, independence of evidence, and delayed descendant value.

The stages are research milestones, not claims of implemented software.

## 18. Testable Hypotheses and Falsification

| ID | Hypothesis | Primary test | Evidence against |
|---|---|---|---|
| QE-H01 | Ecosystem relations improve useful-question yield over a flat queue | matched-budget prospective comparison | no reliable gain or higher cost |
| QE-H02 | Typed factors improve cross-domain question transfer over text similarity | held-out domain pairs | equal or worse verified transfer |
| QE-H03 | Historical scoring reduces redundant exploration without suppressing valuable novelty | longitudinal screening audit | missed valuable novel questions exceed savings |
| QE-H04 | Residual-driven meta-questions outperform unconstrained meta-prompts | blinded usefulness and testability ratings | no advantage under matched tokens/budget |
| QE-H05 | Portfolio selection improves research coverage and validated yield | pre-registered portfolio trials | centrality bias or lower validated yield |
| QE-H06 | QDT family views improve detection of repeated failures | independent annotation benchmark | no improvement in recall/precision |
| QE-H07 | Relay provenance improves reproducibility and reuse | cross-team transfer study | no gain or unacceptable overhead |
| QE-H08 | Bounded meta-question loops improve system calibration | held-out calibration before/after | drift, overfitting, or no improvement |
| QE-H09 | Explicit negative results reduce repeated dead-end exploration | historical replay and prospective study | no reduction or excessive false negatives |
| QE-H10 | Human-governed recursion preserves conformance better than ungated changes | adversarial policy and regression tests | equivalent failure rates or unacceptable latency |

For all hypotheses, publish denominators, confidence intervals or uncertainty estimates, evaluator procedures, and negative results. Prefer independent validation where feasible.

## 19. Evaluation Metrics

Useful metric families include:

**Scientific utility:** independently adjudicated question usefulness; validated hypothesis yield; reproducible findings per resource unit; descendant research value after a fixed observation horizon.

**Representation quality:** type-alignment accuracy; relation precision/recall; unknown-relation calibration; provenance completeness; semantic drift rate.

**Portfolio quality:** cost-adjusted verified yield; coverage across research families; redundant-exploration rate; concentration and novelty starvation.

**Meta-learning quality:** pre/post calibration; out-of-distribution robustness; improvement attributable to adopted changes; rollback frequency; regressions detected before deployment.

**Governance quality:** unauthorized action rate; policy conformance; audit completeness; approval latency; resource-limit violations.

Avoid optimizing a single composite metric without auditing Goodhart effects and evidence dependence.

## 20. Failure Modes and Safeguards

| Failure mode | Risk | Proposed safeguard |
|---|---|---|
| Endless meta-question recursion | resource exhaustion | depth and budget limits; stop criteria |
| Self-confirming evaluator | false improvement | independent adjudication and held-out data |
| Graph-centrality bias | popular families dominate | normalization and protected exploration |
| History lock-in | genuinely novel questions suppressed | cold-start quotas and reversible deferral |
| Duplicate evidence | inflated confidence | dependency-aware evidence accounting |
| Semantic drift in relay | invalid cross-domain claims | UTN contracts and target-domain verification |
| Question explosion | low-quality volume | deduplication, portfolios, evidence requirements |
| Reward hacking | proxy improvement without research value | outcome audits and adversarial benchmarks |
| Unauthorized self-modification | governance breach | sandbox, conformance gate, explicit approval |
| Premature retirement | delayed discoveries lost | revisit triggers and archived lineage |

## 21. Open Research Questions

1. What is the smallest typed relation vocabulary that preserves meaningful research dependencies?
2. Can question ecosystem growth be measured without rewarding sheer volume or density?
3. How should delayed descendant value be attributed without double counting?
4. Which historical screening models best handle unobserved outcomes and selection bias?
5. When should an unknown relation trigger a new experiment rather than a low score?
6. How can causal influence be separated from textual or graph association?
7. Which meta-question operators produce experimentally useful hypotheses rather than self-referential prose?
8. How should heterogeneous human and AI evaluators reconcile conflicting assessments?
9. What is the right governance boundary for automatically proposed changes to the scorer?
10. Can cross-domain meta-question transfer outperform domain-local discovery on genuinely new tasks?
11. How do we quantify the cost of maintaining rich provenance and UTN contracts?
12. Under what conditions does an ecosystem representation become counterproductive?

## 22. Research Position and Claims Boundary

This document offers a **proposed architecture and research program**. It does not demonstrate that question ecosystems improve scientific discovery, that meta-question loops cause recursive self-improvement, or that the approach leads to AGI/ASI. These claims require prospective experiments, independent outcome evaluation, and robust comparisons. In particular:

- **Structural influence is an estimate, not scientific truth.**
- **Meta-question generation is not verified self-improvement.**
- **A proposed system change is not an authorized deployment.**
- **Collective relay is not collective learning unless useful evidence is retained and reused.**
- **Open-ended exploration does not imply unbounded progress.**

The intended contribution is to make these questions explicit, testable, and suitable for collaborative research.

## 23. Relationship to the AQSI Repository

This extension builds on:

- `AQSI-002-Biomimetic-Question-Discovery.md` — discovery channels and structure-first generation.
- `AQSI-003-Multi-Granularity-Structural-Influence-Factors.md` — typed directional relations.
- `AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md` — history and QDT.
- `AQSI-005-Directional-Question-Scoring-and-Portfolio-Selection.md` — goal-open scoring and portfolios.
- `AQSI-006-Question-Units-and-Exploration-Contracts.md` — portable question objects.
- `AQSI-007-Question-Structural-Relay-and-Collective-Learning.md` — evidence and question relay.
- `AQSI-008-Strategic-Question-Control-Planes.md` — human strategic authority.
- `AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md` — typed cross-domain alignment.
- `AQSI-010-MVP-Architecture-and-Recursive-Evolution.md` — staged evaluation and recursion.
- `SPEC-001` through `SPEC-004` — normative interfaces and governance contracts.

The present extension is **exploratory**; where it suggests future interfaces, those suggestions do not supersede the canonical Specifications.

## 24. Future Directions

Near-term work should prioritize a small, inspectable question corpus; documented historical outcomes; typed influence edges; a transparent question-family view; and one falsifiable meta-question operator. Mid-term work should investigate cross-domain transfer, prospective portfolio evaluation, and reproducibility across independent research teams. Longer-term work may examine co-evolution among question ecosystems, UTN type systems, scoring operators, and Structural Relay networks—but only with strong evidence and controlled change governance.

## Conclusion

AQSI can treat questioning not as a stream of isolated prompts, but as an evolving, typed, evidence-bearing research ecosystem. Meta-questions offer a candidate mechanism for inspecting and improving that ecosystem: they ask why some questions are discovered, others are missed, and certain methods or policies succeed or fail. The essential discipline is to preserve the distinction between **generating a question, validating an answer, demonstrating an improvement, and authorizing a change**. With that distinction intact, Question Ecosystems and Meta-Question Discovery form a coherent, falsifiable extension to AQSI's broader research program.

---

### Suggested citation

*Autonomous Questioning Structural Intelligence (AQSI), EXT-001: Question Ecosystem and Meta-Question Discovery, version 1.0.0.* Cite the repository's canonical `CITATION.cff` and release DOI when available; no DOI is asserted here.
