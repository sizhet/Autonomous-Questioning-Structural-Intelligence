# START HERE — Autonomous Questioning Structural Intelligence (AQSI)

**Release:** v1.0.0 — Initial Research Framework  
**Status:** Theory-first research proposal; no validated runtime or performance claims  
**Repository:** [Autonomous-Questioning-Structural-Intelligence](https://github.com/sizhet/Autonomous-Questioning-Structural-Intelligence)  
**License:** Apache-2.0

## 1. What Is AQSI?

Most AI workflows begin with a question supplied by a human and end with an answer. **Autonomous Questioning Structural Intelligence (AQSI)** investigates a different research loop: an AI-assisted system discovers potentially valuable questions, represents their structural relationships, estimates which questions merit investigation, explores selected questions under explicit contracts, and relays evidence and unresolved issues into subsequent research cycles.

AQSI is a **proposed architecture and research agenda**, not a claim that autonomous scientific discovery, recursive self-improvement, or artificial superintelligence has been demonstrated.

The core loop is:

> Discover questions → Represent and align structures → Evaluate and select → Authorize and explore → Record evidence and counterevidence → Structural relay → Discover the next questions.

The intended research contribution is not merely generating more prompts. It is the design of a **persistent, inspectable question ecosystem** whose discoveries, mistakes, costs, and follow-on questions can inform future choices.

## 2. Five Ideas to Understand First

### 2.1 Questions are research objects, not just prompts

A **Question Unit (QU)** has an identity, provenance, typed structural factors, hypotheses, evidence references, evaluation history, lifecycle state, and relay links. A prompt or API call is one possible expression of a Question Unit, not its identity. See [AQSI-006](docs/AQSI-006-Question-Units-and-Exploration-Contracts.md) and [SPEC-001](specs/SPEC-001-Canonical-Question-Unit-Contract.md).

### 2.2 Relationships are directional and multi-granular

Questions may connect through concepts, attributes, methods, constraints, evidence, unresolved residuals, or transfer points. Influence from question A to B need not equal influence from B to A. Unknown relationships must not silently be treated as zero. See [AQSI-003](docs/AQSI-003-Multi-Granularity-Structural-Influence-Factors.md) and [SPEC-002](specs/SPEC-002-Structural-Influence-and-Scoring-Contract.md).

### 2.3 History informs new question selection

Previously explored questions, including failed and inconclusive attempts, can help estimate the likely value and cost of new investigations. **Historical Question Intelligence (HQI)** and **Question Differential Trees (QDT)** are proposed mechanisms for transferring such experience while preserving uncertainty and the possibility of revisiting overlooked ideas. See [AQSI-004](docs/AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md).

### 2.4 Research autonomy does not imply unrestricted authority

Human institutions may specify strategic priorities, budgets, safety boundaries, and approval rules while allowing the system to propose specific questions. **Question ranking, portfolio selection, and execution authorization are distinct decisions.** See [AQSI-008](docs/AQSI-008-Strategic-Question-Control-Planes.md) and [SPEC-004](specs/SPEC-004-Control-Plane-and-Policy-Conformance.md).

### 2.5 The research output includes unanswered questions

Answers, negative results, methods, counterevidence, partial progress, and **Explicit Leftover** can all become reusable Structural Relay pieces. Repeated execution can contribute evidence without being mistaken for independent corroboration. See [AQSI-007](docs/AQSI-007-Question-Structural-Relay-and-Collective-Learning.md) and [SPEC-003](specs/SPEC-003-Question-Relay-and-Exploration-Lifecycle.md).

## 3. Recommended Reading Paths

| Reader | Start with | Then read | Goal |
|---|---|---|---|
| New to AQSI | [AQSI-001](docs/AQSI-001-From-Answering-to-Autonomous-Questioning.md) | [AQSI-002](docs/AQSI-002-Biomimetic-Question-Discovery.md), [AQSI-010](docs/AQSI-010-MVP-Architecture-and-Recursive-Evolution.md) | Understand the motivation and overall system |
| Algorithms and scoring | [AQSI-003](docs/AQSI-003-Multi-Granularity-Structural-Influence-Factors.md) | [AQSI-004](docs/AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md), [AQSI-005](docs/AQSI-005-Directional-Question-Scoring-and-Portfolio-Selection.md), [SPEC-002](specs/SPEC-002-Structural-Influence-and-Scoring-Contract.md) | Examine structural influence, historical evaluation, and portfolio selection |
| Systems and interfaces | [AQSI-006](docs/AQSI-006-Question-Units-and-Exploration-Contracts.md) | [SPEC-001](specs/SPEC-001-Canonical-Question-Unit-Contract.md), [SPEC-003](specs/SPEC-003-Question-Relay-and-Exploration-Lifecycle.md), [AQSI-010](docs/AQSI-010-MVP-Architecture-and-Recursive-Evolution.md) | Inspect contracts and the proposed MVP |
| Research governance | [AQSI-008](docs/AQSI-008-Strategic-Question-Control-Planes.md) | [SPEC-004](specs/SPEC-004-Control-Plane-and-Policy-Conformance.md), [CASE-003](cases/CASE-003-Research-Portfolio-and-Multi-Agent-Relay.md) | Understand authority, budgets, and policy conformance |
| Cross-domain learning | [AQSI-009](docs/AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md) | [CASE-002](cases/CASE-002-Cross-Domain-Question-Transfer.md), [EXT-002](extensions/EXT-002-Cross-Structural-Co-Evolution.md) | Examine typed alignment and transfer limits |
| Open-ended research | [EXT-001](extensions/EXT-001-Question-Ecosystem-and-Meta-Question-Discovery.md) | [EXT-002](extensions/EXT-002-Cross-Structural-Co-Evolution.md), [EXT-003](extensions/EXT-003-Open-Ended-Question-Intelligence-and-ASI-Boundaries.md) | Investigate meta-questions and claims boundaries |

For a comprehensive file-by-file index, see [CONTENTS.md](CONTENTS.md). For terminology, see [GLOSSARY.md](GLOSSARY.md).

## 4. A Fast, Six-Document Introduction

Readers with limited time can follow this sequence:

1. **[AQSI-001](docs/AQSI-001-From-Answering-to-Autonomous-Questioning.md):** Why move from answer-centered to question-centered intelligence?
2. **[AQSI-002](docs/AQSI-002-Biomimetic-Question-Discovery.md):** Where can questions originate?
3. **[AQSI-003](docs/AQSI-003-Multi-Granularity-Structural-Influence-Factors.md):** How can questions influence one another across structural granularity?
4. **[AQSI-004](docs/AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md):** How can prior research inform new question choices?
5. **[AQSI-008](docs/AQSI-008-Strategic-Question-Control-Planes.md):** Who controls priorities, resources, and authorization?
6. **[AQSI-010](docs/AQSI-010-MVP-Architecture-and-Recursive-Evolution.md):** How could these ideas be tested in an incremental MVP?

## 5. Research Architecture at a Glance

The five functional domains are:

| Domain | Purpose | Key research artifacts |
|---|---|---|
| Q1 — Discovery | Generate candidates from gaps, residuals, associations, history, and relay | Candidate Question Units |
| Q2 — Representation | Type and align heterogeneous factors using UTN-compatible structures | Question structures, differential trees, relation records |
| Q3 — Evaluation and Selection | Estimate directed influence and historical value; select a constrained portfolio | Scores, uncertainties, portfolio decisions |
| Q4 — Exploration | Express and investigate authorized questions under explicit contracts | Exploration records, evidence, counterevidence |
| Q5 — Relay and Evolution | Preserve results, derive new questions, and propose controlled system changes | Relay pieces, historical updates, change proposals |

The **Strategic Question Control Plane** governs priorities, resources, and permissions across these domains; it does not eliminate question-level autonomy.

## 6. Visual Guide

The planned figure set offers eight complementary views:

- [Fig-001 — AQSI Grand Architecture](figures/Fig-001-AQSI-Grand-Architecture.png)
- [Fig-002 — Sources of Autonomous Questions](figures/Fig-002-Sources-of-Autonomous-Questions.png)
- [Fig-003 — Multi-Granularity Influence Graph](figures/Fig-003-Multi-Granularity-Influence-Graph.png)
- [Fig-004 — Historical Question Intelligence](figures/Fig-004-Historical-Question-Intelligence.png)
- [Fig-005 — Directional Scoring and Portfolio Selection](figures/Fig-005-Directional-Scoring-and-Portfolio-Selection.png)
- [Fig-006 — Question Unit and Structural Relay](figures/Fig-006-Question-Unit-and-Structural-Relay.png)
- [Fig-007 — Strategic Question Control Plane](figures/Fig-007-Strategic-Question-Control-Plane.png)
- [Fig-008 — UTN Cross-Domain Relay and RSI](figures/Fig-008-UTN-Cross-Domain-Relay-and-RSI.png)

See [FIGURE-INDEX.md](FIGURE-INDEX.md) for figure-to-paper placement guidance.

## 7. Start with a Bounded Case, Not a Grand Claim

Three cases illustrate proposed research workflows rather than reporting completed experiments:

- **[CASE-001 — Single-Domain Autonomous Questioning](cases/CASE-001-Single-Domain-Autonomous-Questioning.md):** a bounded software-engineering investigation of flaky tests.
- **[CASE-002 — Cross-Domain Question Transfer](cases/CASE-002-Cross-Domain-Question-Transfer.md):** structural transfer from CI test instability to intermittent sensor-network anomalies.
- **[CASE-003 — Research Portfolio and Multi-Agent Relay](cases/CASE-003-Research-Portfolio-and-Multi-Agent-Relay.md):** strategic allocation, multi-agent research roles, and governed relay.

These examples are **illustrative**. Numerical scores, hypothetical outcomes, and sample resource allocations should not be interpreted as empirical findings.

## 8. MVP and Validation Sequence

The proposed staged path is:

| Stage | Focus | Evidence needed to progress |
|---|---|---|
| M0 | Single-domain, traceable question-to-relay loop | Complete provenance, valid contracts, measurable baseline |
| M1 | Historical intelligence and multi-granularity scoring | Controlled comparisons against simpler ranking approaches |
| M2 | UTN-aligned cross-domain transfer and multi-agent relay | Verified target-domain benefit and reliable cross-agent provenance |
| M3 | Governed meta-questioning and recursive improvement | Independent evaluation, regression checks, authorization, rollback |

A positive demonstration in one stage does **not** establish the success of later stages. Consult [TESTABLE-HYPOTHESES.md](TESTABLE-HYPOTHESES.md) and [VALIDATION-ROADMAP.md](VALIDATION-ROADMAP.md) for proposed tests and criteria.

## 9. What AQSI Does Not Claim

This release does **not** claim that:

- Question novelty reliably predicts scientific value.
- Directed structural influence scores are already calibrated or validated.
- Historical success labels generalize without selection bias or domain shift.
- Cross-domain structural similarity guarantees transferable solutions.
- Multi-agent discussion automatically yields independent evidence.
- Meta-question generation constitutes demonstrated recursive self-improvement.
- Open-ended questioning implies AGI or ASI.

The framework instead provides **hypotheses, interfaces, failure modes, and validation pathways** for studying these questions.

## 10. How to Contribute to Collective Learning

Useful contributions include counterexamples, alternative influence models, typed structural mappings, new historical-question datasets, contract critiques, evaluation protocols, replication attempts, and documented failures. A useful contribution should ideally specify:

1. The precise question, claim, or contract being challenged or extended.
2. Evidence provenance and the distinction between observation and interpretation.
3. Relevant domain, UTN-compatible type information, and assumptions.
4. Proposed tests, falsification conditions, and known limitations.
5. Any derived questions or Explicit Leftover worth relaying.

When proposing system changes, treat **structural change proposals** as reviewable candidates; do not equate a proposal with an authorized deployment.

## 11. Repository Navigation and Publication Notes

- [README.md](README.md) — Project overview and repository entry point.
- [CONTENTS.md](CONTENTS.md) — Complete document map.
- [GLOSSARY.md](GLOSSARY.md) — Shared terminology.
- [FUTURE-DIRECTIONS.md](FUTURE-DIRECTIONS.md) — Potential research extensions.
- [OPEN-QUESTIONS.md](OPEN-QUESTIONS.md) — Outstanding problems.
- [TESTABLE-HYPOTHESES.md](TESTABLE-HYPOTHESES.md) — Falsifiable research propositions.
- [VALIDATION-ROADMAP.md](VALIDATION-ROADMAP.md) — Proposed experimental plan.
- [CHANGELOG.md](CHANGELOG.md) — Version history.
- [CITATION.cff](CITATION.cff) — Citation metadata.
- [.zenodo.json](.zenodo.json) — Zenodo metadata.

A DOI should only be added once one has actually been assigned. This document intentionally does not invent a DOI or claim publication acceptance.

---

**Suggested first step:** Read [AQSI-001](docs/AQSI-001-From-Answering-to-Autonomous-Questioning.md), then examine [CASE-001](cases/CASE-001-Single-Domain-Autonomous-Questioning.md) with [SPEC-001](specs/SPEC-001-Canonical-Question-Unit-Contract.md) open beside it. This connects the research motivation to a concrete, contract-governed example.
