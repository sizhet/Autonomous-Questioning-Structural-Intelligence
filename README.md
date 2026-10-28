# Autonomous Questioning Structural Intelligence (AQSI)

**Question Discovery, Multi-Granularity Influence Scoring, Structural Relay, and Research Governance**

**Version:** v1.0.0 — Initial Research Framework  
**Status:** Theory-first research proposal; no validated runtime implementation is claimed  
**License:** Apache-2.0

## Overview

Most AI assistants are organized around responding to externally supplied questions. **Autonomous Questioning Structural Intelligence (AQSI)** investigates a complementary capability: discovering, representing, evaluating, selecting, exploring, and relaying research questions in a persistent, evidence-aware system. The proposed objective is not to maximize the number of generated questions, but to improve the quality, traceability, and potential cumulative value of inquiry.

AQSI is a **research framework**, not a claim that autonomous scientific discovery, reliable recursive self-improvement, or artificial superintelligence has been achieved. Its architectural claims, scoring mechanisms, and expected benefits require independent empirical validation.

## Research Thesis

An autonomous questioning system may become more useful when it can:

1. Discover questions from knowledge gaps, unresolved residuals, anomalies, historical inquiry, and cross-domain associations.
2. Represent questions as typed, multi-granularity structural objects rather than treating prompt text as the sole source of identity.
3. Estimate **directional** question-to-question influence using concepts, attributes, methods, evidence, constraints, and transfer points.
4. Reuse historical successes, failures, counterevidence, and delayed downstream outcomes to improve question evaluation.
5. Select a **portfolio** of questions under explicit budgets and strategic constraints, rather than simply ranking isolated prompts.
6. Conduct authorized exploration under explicit contracts and relay the resulting evidence, methods, unresolved issues, and successor questions.
7. Treat the questioning system itself as a subject of research, with proposed changes subject to conformance checks, independent evaluation, and human approval where required.

### A foundational distinction

**Goal-open question selection** means that the system need not begin with one predetermined target question. It does **not** mean that evaluation is value-free, unconstrained, or independent of human governance.

## Conceptual Architecture

The proposed system combines five research functions:

| Functional domain | Primary responsibility | Representative artifacts |
| --- | --- | --- |
| Q1 — Discovery | Identify candidate questions and unexplored relationships | Candidate Question Units, gap and residual records |
| Q2 — Representation | Encode question identity, structure, and provenance | Typed Question Units, UTN mappings, Question Differential Trees |
| Q3 — Evaluation and Selection | Estimate influence, uncertainty, historical value, and portfolio fit | Influence records, historical assessments, portfolio decisions |
| Q4 — Exploration | Translate questions into authorized research activities | Exploration contracts, prompts, API tasks, experiments |
| Q5 — Relay and Evolution | Preserve outcomes and generate successor research | Evidence, counterevidence, Explicit Leftover, relay pieces, change proposals |

A **Strategic Question Control Plane (SQCP)** governs the relationship between human research direction and AI autonomy. It separates strategic policy, portfolio allocation, tactical coordination, and operational execution. Selecting a high-scoring question does not grant permission to execute an action.

### Multi-granularity directional influence

For a candidate set \(Q = \{q_1, \ldots, q_n\}\), a baseline goal-open score is:

\[
S(q_i) = \sum_{j \ne i} I(q_i \rightarrow q_j)
\]

where \(I(q_i \rightarrow q_j)\) is an **estimated directional structural influence**, not a proven measure of scientific importance. In general, \(I(q_i \rightarrow q_j) \neq I(q_j \rightarrow q_i)\). Influence can be estimated from multiple typed relations and folded using configurable operators; missing or unobserved relations must not automatically be interpreted as zero influence. Historical estimates, uncertainty, cost, diversity, and strategic constraints may affect subsequent portfolio selection.

## Research Contributions Proposed for Evaluation

- **Question-centric structural intelligence:** persistent Question Units and question-to-question relationships, beyond transient prompt/answer exchanges.
- **Multi-granularity influence scoring:** typed, directional relations among heterogeneous structural factors, with replaceable evaluators and explicit uncertainty.
- **Historical Question Intelligence (HQI):** learning from prior question attempts, including negative outcomes, delayed value, and the possibility of revisiting deferred questions.
- **Strategic Question Control Planes:** human-defined priorities, resources, authority, and safety boundaries with autonomy over specific research-question discovery.
- **Open structural relay and controlled recursive evolution:** interoperable transfer of questions, evidence, counterevidence, methods, and proposed system changes.

These are **design propositions and testable research directions**, not demonstrated performance gains.

## Repository Map

### Core research papers — `docs/`

| Paper | Focus |
| --- | --- |
| [AQSI-001](docs/AQSI-001-From-Answering-to-Autonomous-Questioning.md) | From answering to autonomous questioning |
| [AQSI-002](docs/AQSI-002-Biomimetic-Question-Discovery.md) | Biomimetic question discovery |
| [AQSI-003](docs/AQSI-003-Multi-Granularity-Structural-Influence-Factors.md) | Multi-granularity influence factors |
| [AQSI-004](docs/AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md) | Historical Question Intelligence and differential trees |
| [AQSI-005](docs/AQSI-005-Directional-Question-Scoring-and-Portfolio-Selection.md) | Directional scoring and portfolio selection |
| [AQSI-006](docs/AQSI-006-Question-Units-and-Exploration-Contracts.md) | Question Units and exploration contracts |
| [AQSI-007](docs/AQSI-007-Question-Structural-Relay-and-Collective-Learning.md) | Structural relay and collective learning |
| [AQSI-008](docs/AQSI-008-Strategic-Question-Control-Planes.md) | Strategic Question Control Planes |
| [AQSI-009](docs/AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md) | UTN and cross-domain question transfer |
| [AQSI-010](docs/AQSI-010-MVP-Architecture-and-Recursive-Evolution.md) | MVP architecture and recursive evolution |

### Specifications — `specs/`

| Specification | Scope |
| --- | --- |
| [SPEC-001](specs/SPEC-001-Canonical-Question-Unit-Contract.md) | Canonical Question Unit identity, structure, and lifecycle |
| [SPEC-002](specs/SPEC-002-Structural-Influence-and-Scoring-Contract.md) | Influence records, scoring, folding, and uncertainty |
| [SPEC-003](specs/SPEC-003-Question-Relay-and-Exploration-Lifecycle.md) | Exploration and relay lifecycle |
| [SPEC-004](specs/SPEC-004-Control-Plane-and-Policy-Conformance.md) | Policy authority, allocation, authorization, and audit |

### Research cases — `cases/`

- [CASE-001 — Single-Domain Autonomous Questioning](cases/CASE-001-Single-Domain-Autonomous-Questioning.md): a proposed inquiry loop for flaky software tests.
- [CASE-002 — Cross-Domain Question Transfer](cases/CASE-002-Cross-Domain-Question-Transfer.md): structural transfer from intermittent software failures to sensor anomalies.
- [CASE-003 — Research Portfolio and Multi-Agent Relay](cases/CASE-003-Research-Portfolio-and-Multi-Agent-Relay.md): strategic allocation, multi-agent roles, and collective learning.

The cases are **illustrative research designs**. Their hypothetical scores and outcomes are not experimental findings.

### Extensions — `extensions/`

- [EXT-001 — Question Ecosystem and Meta-Question Discovery](extensions/EXT-001-Question-Ecosystem-and-Meta-Question-Discovery.md)
- [EXT-002 — Cross-Structural Co-Evolution](extensions/EXT-002-Cross-Structural-Co-Evolution.md)
- [EXT-003 — Open-Ended Question Intelligence and ASI Boundaries](extensions/EXT-003-Open-Ended-Question-Intelligence-and-ASI-Boundaries.md)

### Research navigation and publication assets

- [START-HERE.md](START-HERE.md) — suggested reading paths
- [CONTENTS.md](CONTENTS.md) — complete contents
- [GLOSSARY.md](GLOSSARY.md) — terminology
- [FIGURE-INDEX.md](FIGURE-INDEX.md) — diagram guide
- [FUTURE-DIRECTIONS.md](FUTURE-DIRECTIONS.md) — future research
- [OPEN-QUESTIONS.md](OPEN-QUESTIONS.md) — unresolved questions
- [TESTABLE-HYPOTHESES.md](TESTABLE-HYPOTHESES.md) — falsifiable hypotheses
- [VALIDATION-ROADMAP.md](VALIDATION-ROADMAP.md) — evaluation plan
- [CHANGELOG.md](CHANGELOG.md) — release history
- [CITATION.cff](CITATION.cff) and [.zenodo.json](.zenodo.json) — citation and archive metadata
- [release/](release/) — GitHub release notes and ResearchGate materials

## Figures

| Figure | Description |
| --- | --- |
| [Fig-001](figures/Fig-001-AQSI-Grand-Architecture.png) | AQSI grand architecture |
| [Fig-002](figures/Fig-002-Sources-of-Autonomous-Questions.png) | Sources of autonomous questions |
| [Fig-003](figures/Fig-003-Multi-Granularity-Influence-Graph.png) | Multi-granularity influence graph |
| [Fig-004](figures/Fig-004-Historical-Question-Intelligence.png) | Historical Question Intelligence |
| [Fig-005](figures/Fig-005-Directional-Scoring-and-Portfolio-Selection.png) | Directional scoring and portfolio selection |
| [Fig-006](figures/Fig-006-Question-Unit-and-Structural-Relay.png) | Question Unit and structural relay |
| [Fig-007](figures/Fig-007-Strategic-Question-Control-Plane.png) | Strategic Question Control Plane |
| [Fig-008](figures/Fig-008-UTN-Cross-Domain-Relay-and-RSI.png) | UTN, cross-domain relay, and RSI |

> Figure links describe the planned repository layout. Each image should be committed at its exact path before publication.

## Research and Validation Roadmap

The proposed evaluation sequence is deliberately incremental:

1. **M0 — Single-domain loop:** establish Question Unit contracts, candidate generation, baseline scoring, bounded exploration, and provenance-preserving relay.
2. **M1 — Historical and structural evaluation:** compare HQI, Question Differential Trees, directional influence, and portfolio selection against simpler baselines.
3. **M2 — Cross-domain and multi-agent relay:** evaluate UTN-based alignment, transfer reliability, multi-agent disagreement handling, and collective reuse.
4. **M3 — Controlled recursive improvement:** evaluate proposed changes to discovery, scoring, and relay mechanisms under independent tests and governance approval.

Potential evaluation measures include question utility judged by blinded domain experts, validated downstream discoveries, cost-adjusted knowledge gain, calibration, coverage of previously neglected areas, transfer success, reproducibility, and rate of harmful or invalid relay. **Question volume, apparent novelty, and agreement among AI agents are insufficient evidence of scientific progress.**

## Boundaries and Limitations

- The repository presents a **theory-first architecture**; v1.0.0 does not claim an implemented or benchmarked autonomous research system.
- The framework draws inspiration from human questioning but does not claim to model human cognition faithfully.
- Influence scores and historical predictions are estimates subject to confounding, selection bias, data leakage, and domain shift.
- Cross-domain analogies require target-domain verification; structural similarity alone does not establish transfer validity.
- Recursive questioning and recursive self-improvement are different claims. Neither open-ended question generation nor a proposed improvement loop demonstrates ASI.
- Human strategic authority, policy conformance, resource limits, and explicit execution authorization remain required design boundaries.
- Failed, deferred, uncertain, and counterevidential results should remain visible as **Explicit Leftover**, not silently discarded.

## How to Participate

Contributions are welcome in the form of critical reviews, alternative structural representations, competing scoring operators, counterexamples, conformance tests, benchmark proposals, reproducible experiments, and cross-domain case studies. Please distinguish **hypothesis**, **illustrative example**, **implementation**, and **empirical result** when submitting work. Preserve provenance and relevant negative findings, and avoid claims stronger than the available evidence.

## Related Structural Intelligence Research

AQSI is intended to be interoperable, where appropriate, with complementary research on structural intelligence, including:

- **SIF:** capability localization, addressing, and structural growth.
- **UTN:** typed naming, semantic alignment, and cross-domain identity.
- **UCPSF:** configurable scoring, folding, and control planes.
- **UIERU:** portable intelligence units, exploration trails, and relay.
- **SRSI:** evaluator governance and controlled recursive improvement.
- **MDI / BM-ODWEI:** directional relationships and non-exact structural association.

These connections are proposed research interfaces, not claims of existing runtime compatibility.

## Citation and License

Please use [CITATION.cff](CITATION.cff) for the preferred citation metadata once finalized. A DOI should be added only after an actual archive release has assigned one; none is asserted here.

Unless a specific file states otherwise, this repository is intended to be released under the **Apache License 2.0**. See [LICENSE.txt](LICENSE.txt).

---

## 📚 DBM-SI Series Navigation

See:\
[./docs/DBM-SI-Series-of-gitHub-Repositories/DBM-SI-Series-of-gitHub-Repositories.md](./docs/DBM-SI-Series-of-gitHub-Repositories/DBM-SI-Series-of-gitHub-Repositories.md)

---

**Research stance:** Specifications before runtime · Conformance before deployment · Evidence before claims · Human governance over strategic authority · Collective Learning Friendly.
