# Future Directions

## Autonomous Questioning Structural Intelligence (AQSI)

**Research roadmap — v1.0.0**  
**Status:** Proposed directions, not demonstrated capabilities  
**Orientation:** Theory-first; specifications and conformance before runtime; evidence before claims; collective-learning friendly.

## 1. Purpose and Scope

Autonomous Questioning Structural Intelligence (AQSI) studies how an AI research system might discover, represent, evaluate, select, explore, and relay questions, rather than merely answer questions supplied by others. This roadmap identifies research directions that could make those processes more reliable, useful, interoperable, and governable.

A *direction* here is a candidate research program. It is not an assertion that a corresponding algorithm, implementation, or intelligence gain has been validated. Future work should report null results, negative evidence, costs, and unresolved limitations alongside successes.

The central question is:

> Under what conditions does a structured, historically informed, and governed questioning loop produce more independently verifiable research value per unit of resource than simpler alternatives?

## 2. Research Principles

1. **Separate questions from prompts.** Preserve stable Question Units (QUs) while allowing multiple prompt, API, query, and experimental representations.
2. **Keep relationships directional and multi-granular.** Do not reduce concept, attribute, method, evidence, constraint, and residual relations to a single similarity score without justification.
3. **Preserve unknowns.** An unmeasured relation is not a zero-valued relation; lack of evidence is not counterevidence.
4. **Treat historical outcomes as evidence, not destiny.** Historical scores may improve screening but can suppress genuinely novel questions if used without exploration safeguards.
5. **Distinguish prediction from verification.** Predicted question value, model agreement, and a plausible answer are not independently verified scientific progress.
6. **Keep authority explicit.** Selecting a question, authorizing an experiment, and changing strategic policy are distinct decisions.
7. **Require provenance and conformance.** Relay artifacts should remain inspectable, versioned, and subject to contract checks.
8. **Optimize for net value.** Evaluate research yield, diversity, latency, computational cost, human review burden, and negative externalities.

## 3. Direction A — Question Discovery Beyond Prompt Sampling

### A1. Comparative discovery mechanisms

Compare four primary sources of candidate questions: (i) explicit knowledge gaps, (ii) residuals and failures, (iii) multi-granularity structural associations, and (iv) question-to-question or exploration-to-question relay. Evaluate their complementarity rather than assuming that combining more sources always helps.

**Research tasks:** define a common candidate schema; measure novelty against historical corpora; distinguish merely reworded questions from structurally new questions; test whether source diversity predicts independently verified downstream value.

**Falsifier:** if structured discovery adds no value over budget-matched LLM question sampling, its added complexity is not justified for that setting.

### A2. Structure-first generation

Investigate whether discovering missing or unusual relationships among typed structural factors *before* drafting a natural-language question improves cross-domain hypothesis quality. Compare structure-first, LLM-first, and hybrid pipelines using identical retrieval and evaluation budgets.

**Failure modes:** spurious graph edges, incorrect type alignment, semantically empty novelty, and questions that cannot be operationalized.

### A3. Question differential trees

Explore Core/Delta representations for question families, including versioning, branching, compression, and reversible unfolding. Test whether differential trees reduce duplication while preserving distinctions essential to experimental design.

## 4. Direction B — Multi-Granularity Directional Influence Intelligence

### B1. Typed influence factors

Develop replaceable factor scorers over concept, attribute, method, constraint, evidence, residual, and transfer-point relations. Record direction, evidence basis, confidence, and applicable context for each relation. UTN-based typing and semantic contracts are candidate interoperability mechanisms, not proof of semantic equivalence.

For questions \(q_i\) and \(q_j\), a proposed directional influence model is:

\[
I(q_i\!\rightarrow\!q_j)=\operatorname{Fold}_{a,b}\bigl(w_{ab}\,R(h_{ia},h_{jb})\bigr),
\]

where \(h_{ia}\) and \(h_{jb}\) are heterogeneous structural factors, \(R\) is a typed relation evaluator, and the folding operator is explicitly specified. In general, \(I(q_i\!\rightarrow\!q_j)\neq I(q_j\!\rightarrow\!q_i)\).

### B2. Calibration and uncertainty

Study how to calibrate predicted influence against observed downstream contributions. Record epistemic uncertainty, data sparsity, and disagreements between scoring methods. Separate unknown, absent, contradictory, and low-confidence evidence states.

### B3. Anti-Goodhart evaluation

Compare scoring policies using independent outcome assessors and held-out question families. Test for feedback loops in which a model learns to generate questions that score highly without improving research results.

**Falsifier:** a higher internal influence score that fails to predict held-out downstream value undermines the scoring model, not the held-out evaluation.

## 5. Direction C — Historical Question Intelligence (HQI)

### C1. Outcome-aware memory

Create historical records linking Question Units, structural representations, decisions, exploration contracts, evidence, counterevidence, costs, and descendant questions. Explicitly distinguish unattempted, attempted-but-inconclusive, refuted, partially successful, and independently verified outcomes.

### C2. Learning from failure and delay

Develop screening and revisit policies that can defer expensive or low-potential questions without deleting them. Evaluate delayed relay value: a question may fail to produce an immediate answer yet enable valuable later research.

### C3. Correcting historical bias

Test selection-bias corrections, uncertainty-aware exploration, and cold-start protections. Historical corpora usually contain outcomes for *selected* questions, not a random sample of all generated candidates. Consequently, naive success-rate learning may reinforce earlier selection errors.

**Comparators:** no-history baseline, nearest-neighbor retrieval, rules, learned scorer, and combined methods, all under matched budgets.

## 6. Direction D — Question Portfolio Intelligence

### D1. Goal-open baseline

Evaluate the proposed pairwise influence baseline:

\[
S(q_i)=\sum_{j\ne i}I(q_i\!\rightarrow\!q_j).
\]

This is a candidate ranking rule, not a universal objective. Investigate sensitivity to portfolio size, graph density, score calibration, question duplication, and asymmetric influence.

### D2. Resource-aware portfolio selection

Study portfolios that balance expected research value, complementarity, redundancy, diversity, cost, risk, and uncertainty. Compare greedy selection, constrained optimization, bandit-style allocation, and human-in-the-loop review.

### D3. Breakthrough-readiness hypotheses

Explore whether structural proximity to known methods, evidence, or missing links helps identify research directions with plausible near-term progress. Use retrospective and prospective tests; avoid equating structural proximity with a guaranteed breakthrough.

**Governance boundary:** portfolio recommendations never constitute permission to execute experiments or spend resources.

## 7. Direction E — Question Units, Exploration Contracts, and Conformance

### E1. Canonical interoperability

Refine Question Unit schemas, UTN identity and typing, provenance, versioning, scoring references, evidence references, and lifecycle states. Support loss-aware import/export across repositories and agents.

### E2. Expression adapters

Test conversion of the same QU into prompts, structured API calls, SQL queries, simulation tasks, and human research briefs. Measure semantic preservation and identify what is lost during translation.

### E3. Conformance before runtime

Develop machine-checkable tests for lifecycle transitions, authority checks, evidence provenance, relay lineage, schema compatibility, and reproducible scoring. A successful schema check is necessary but not sufficient for scientific correctness.

**Related specifications:** [SPEC-001](specs/SPEC-001-Canonical-Question-Unit-Contract.md), [SPEC-002](specs/SPEC-002-Structural-Influence-and-Scoring-Contract.md), [SPEC-003](specs/SPEC-003-Question-Relay-and-Exploration-Lifecycle.md), and [SPEC-004](specs/SPEC-004-Control-Plane-and-Policy-Conformance.md).

## 8. Direction F — Structural Relay and Collective Learning

### F1. Relay operators and provenance

Evaluate Derive, Split, Compose, Transfer, Refute, Revisit, Replicate, Fold, and Unfold as proposed operations over questions and research artifacts. Every relay should identify source objects, transformations, assumptions, and unresolved leftovers.

### F2. Repeated-execution relay

Study when repeated experiments add information through independent corroboration, variance estimation, drift detection, or dataset growth. Avoid treating repeated calls to the same model or dependent observations as independent evidence.

### F3. Cross-agent collaboration

Compare independent researchers, role-specialized agents, and structured relay systems. Measure whether explicit artifacts improve error correction, knowledge reuse, and reproducibility compared with unstructured conversation logs.

**Falsifier:** increased message exchange without improved independently assessed research outcomes is collaboration overhead, not demonstrated collective learning.

## 9. Direction G — UTN and Cross-Domain Question Transfer

### G1. Partial structural alignment

Investigate transfers that preserve a limited method, constraint, failure pattern, or evidence relation rather than assuming whole-domain equivalence. Track source-domain assumptions and target-domain mismatches.

### G2. Transfer scoring and negative transfer

Evaluate direction-sensitive transfer proposals with explicit uncertainty. Test whether historical success in one domain predicts utility in another, and measure harmful or misleading transfers.

### G3. Evolving type systems

Study controlled UTN type proposals generated by recurring mismatches or novel question families. Require compatibility reviews, counterexamples, migration plans, and rollback before adopting type-system changes.

**Related research:** [AQSI-009](docs/AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md) and [CASE-002](cases/CASE-002-Cross-Domain-Question-Transfer.md).

## 10. Direction H — Strategic Question Control Planes

### H1. Multi-level governance

Refine four separable layers: Strategic (human research direction and boundaries), Portfolio (resource allocation), Tactical (question evaluation and selection), and Operational (authorized exploration). Specify which decisions may be delegated and which require explicit human approval.

### H2. Bidirectional question–policy relay

Allow evidence and discovered questions to inform *proposed* policy revisions without granting the system unilateral strategic authority. Record rationales, alternatives, dissent, and approval history.

### H3. Governance evaluation

Measure policy conformance, auditability, budget adherence, research diversity, and the cost of oversight. Study conflicts between short-term deliverables and long-term foundational inquiry.

**Related research:** [AQSI-008](docs/AQSI-008-Strategic-Question-Control-Planes.md) and [CASE-003](cases/CASE-003-Research-Portfolio-and-Multi-Agent-Relay.md).

## 11. Direction I — Question Ecosystems and Meta-Question Discovery

### I1. Ecosystem-level measures

Define measures for question lineage depth, structural diversity, unresolved residual coverage, redundancy, verified knowledge gain, and cost-adjusted downstream utility. Avoid using raw question counts as a proxy for progress.

### I2. Meta-questions about the questioning system

Generate questions about failed discovery methods, biased historical scoring, brittle UTN mappings, ineffective exploration contracts, and policy bottlenecks. Evaluate proposals in sandboxes before any deployment.

### I3. Cross-structural co-evolution

Study whether AQSI, UTN, SIF, UIERU, influence scoring, and relay mechanisms can improve one another under independent tests. Co-evolution requires demonstrated, sustained, mutually relevant gains; mere interaction is insufficient.

**Related extensions:** [EXT-001](extensions/EXT-001-Question-Ecosystem-and-Meta-Question-Discovery.md) and [EXT-002](extensions/EXT-002-Cross-Structural-Co-Evolution.md).

## 12. Direction J — Recursive Improvement and Open-Ended Boundaries

A proposed improvement loop is:

1. Detect a measurable limitation in discovery, scoring, selection, exploration, or relay.
2. Form a meta-question with explicit evidence and alternatives.
3. Propose a bounded structural change.
4. Check contracts, permissions, and backward compatibility.
5. Run controlled comparisons against the current baseline.
6. Accept, reject, or defer the change based on independently assessed results.
7. Preserve provenance, counterevidence, and rollback capability.

Distinguish three levels: **question-ecosystem evolution**, **model/algorithm evolution**, and **system-architecture evolution**. None by itself demonstrates general recursive self-improvement, much less ASI. Open-ended generation, sustained capability growth, and superintelligence are separate propositions requiring separate evidence.

**Related extension:** [EXT-003](extensions/EXT-003-Open-Ended-Question-Intelligence-and-ASI-Boundaries.md).

## 13. Proposed Validation Program

| Phase | Focus | Minimum evidence expected | Primary risk |
|---|---|---|---|
| M0 | Single-domain closed loop | Reproducible question records, controlled exploration, evidence/relay lineage | Attractive but unproductive question generation |
| M1 | Historical and multi-granularity scoring | Held-out predictive calibration; budget-matched baselines; ablations | Selection bias and score gaming |
| M2 | Cross-domain and multi-agent relay | Verified target-domain outcomes; negative-transfer accounting; provenance checks | Semantic drift and correlated errors |
| M3 | Controlled meta-question and structural change | Pre-registered comparisons; conformance tests; rollback; sustained net improvement | Self-referential evaluation and unsafe authority expansion |

Each phase should include resource accounting, negative-result publication, and a clear go/no-go decision. Advancement to a later phase should not be inferred merely from successful completion of documentation.

## 14. Priority Experiments

| ID | Research question | Comparator | Observable outcome |
|---|---|---|---|
| FD-01 | Does structure-first discovery improve question quality? | Budget-matched LLM-first sampling | Independently verified valuable questions per unit cost |
| FD-02 | Do multi-granularity directed factors add predictive value? | Text similarity and concept-only graphs | Held-out outcome prediction and calibration |
| FD-03 | Does HQI improve screening without suppressing novelty? | No-history and nearest-neighbor baselines | Cost-adjusted yield, novel discoveries, false rejections |
| FD-04 | Do portfolios outperform top-k question ranking? | Top-k by single score | Verified portfolio yield, diversity, resource efficiency |
| FD-05 | Does explicit relay improve cumulative research value? | Unstructured discussion history | Reuse rate, independent verification, descendant value |
| FD-06 | Does UTN-assisted transfer reduce negative transfer? | Untyped semantic transfer | Target-domain validation success and transfer errors |
| FD-07 | Do control planes improve governance without excessive cost? | Unstructured manual oversight | Policy violations, auditability, review burden |
| FD-08 | Can meta-question proposals improve the system reliably? | Frozen baseline | Repeated, independent net gains after conformance checks |

For each experiment, predefine the evaluation set, budget, independent assessor, uncertainty treatment, stopping rule, and publication criteria. Use multiple domains to reduce overfitting to a single research setting.

## 15. Failure Modes and Explicit Leftovers

The research program should maintain an openly accessible register of unresolved issues, including:

- **Question proliferation:** many plausible questions but little verified knowledge gain.
- **Graph illusion:** attractive structural associations without causal or practical relevance.
- **Historical lock-in:** premature rejection of novel or minority research directions.
- **Feedback contamination:** scores trained on outputs later used to judge those same scores.
- **Evidence dependence:** repeated or multi-agent outputs incorrectly counted as independent.
- **Negative transfer:** source-domain analogies that fail under target-domain constraints.
- **Portfolio capture:** strategic preferences or score artifacts crowding out important foundational work.
- **Governance drift:** research suggestions silently treated as policy changes or execution permission.
- **Metric gaming:** apparent improvement in internal measures without external gains.
- **Unbounded complexity:** overhead exceeding the value of structured questioning.

A failure should produce a documented counterexample, a revised hypothesis, a bounded next experiment, or an explicit decision to stop—not a retroactive claim of success.

## 16. Collective Learning and Contribution Pathways

Researchers may contribute formal counterexamples, alternative scoring operators, typed alignment proposals, benchmark tasks, negative results, exploration contracts, provenance schemas, or independent replication reports. Contributions should identify their target document and version, assumptions, evidence sources, evaluation budget, limitations, and possible effects on existing contracts.

Suggested contribution artifacts include:

- A **Question Unit** with explicit provenance and unresolved assumptions.
- A **Structural Influence Record** with direction, factor types, evidence, and uncertainty.
- A **Relay Piece** with source lineage and transformation details.
- A **Conformance Test** or reproducible negative example.
- A **Structural Change Proposal** with rollback and validation criteria.

The goal is not agreement with the AQSI framework; it is a cumulative, inspectable research process in which useful alternatives and disconfirming results can change the framework.

## 17. Publication and Versioning Outlook

- **v1.0.0 — Initial Research Framework:** theory, proposed contracts, cases, extensions, and falsifiable validation plans; no claim of deployed AQSI performance.
- **Potential v1.1.x — Minimal Evaluation Artifacts:** benchmark definitions, conformance fixtures, and initial controlled experiments, if completed.
- **Potential v1.2.x — Historical/Influence Studies:** calibrated scorers and ablations, if independently supported.
- **Potential v2.x — Cross-Domain/Collective Research:** larger relay studies and controlled structural improvement, contingent on evidence and governance readiness.

These are candidate milestones, not promised releases or claims that the experiments will succeed.

## 18. Navigation and Related Documents

**Foundations:** [AQSI-001](docs/AQSI-001-From-Answering-to-Autonomous-Questioning.md), [AQSI-002](docs/AQSI-002-Biomimetic-Question-Discovery.md), [AQSI-003](docs/AQSI-003-Multi-Granularity-Structural-Influence-Factors.md), [AQSI-004](docs/AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md), [AQSI-005](docs/AQSI-005-Directional-Question-Scoring-and-Portfolio-Selection.md).

**Execution and integration:** [AQSI-006](docs/AQSI-006-Question-Units-and-Exploration-Contracts.md), [AQSI-007](docs/AQSI-007-Question-Structural-Relay-and-Collective-Learning.md), [AQSI-008](docs/AQSI-008-Strategic-Question-Control-Planes.md), [AQSI-009](docs/AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md), [AQSI-010](docs/AQSI-010-MVP-Architecture-and-Recursive-Evolution.md).

**Research program:** [OPEN-QUESTIONS.md](OPEN-QUESTIONS.md), [TESTABLE-HYPOTHESES.md](TESTABLE-HYPOTHESES.md), [VALIDATION-ROADMAP.md](VALIDATION-ROADMAP.md), and [CONTENTS.md](CONTENTS.md).

---

**Closing perspective.** AQSI should be judged by its ability to generate *better-tested research progress*, not merely more questions or more elaborate structures. The strongest future direction is therefore a disciplined combination of structural discovery, historically calibrated evaluation, independent evidence, explicit governance, and open relay of both success and failure.
