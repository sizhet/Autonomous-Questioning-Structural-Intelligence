# AQSI v1.0.0 — Initial Research Framework

**Autonomous Questioning Structural Intelligence (AQSI)**  
*Question Discovery, Multi-Granularity Influence Scoring, Structural Relay, and Research Governance*

**Release type:** Theory-first research framework  
**Version:** v1.0.0  
**Repository:** https://github.com/sizhet/Autonomous-Questioning-Structural-Intelligence  
**License:** Apache-2.0  
**DOI:** Pending Zenodo registration; no DOI is asserted in this release note.

## Overview

AQSI proposes a structural research framework for moving from AI systems that primarily respond to supplied questions toward systems that can **discover, represent, evaluate, select, and explore research questions**, then preserve their outcomes as reusable structural knowledge. The aim is not to maximize question volume, but to investigate whether autonomous questioning can improve *verified research yield*, resource efficiency, cross-domain transfer, and collective learning under explicit human governance.

This initial release presents research hypotheses, conceptual architectures, contracts, worked examples, and validation plans. **It does not claim a deployed AQSI runtime, completed benchmark results, verified recursive self-improvement, or artificial superintelligence.**

## Principal Research Contributions

### 1. Question-centric structural intelligence

AQSI treats a research question as a durable, typed **Question Unit**, distinct from any single natural-language prompt. Question Units can retain provenance, domain context, structural factors, historical assessments, evidence, counterevidence, lifecycle state, and relay links. Questions may originate from gaps, unresolved residuals, conceptual associations, historical experience, or prior research relay.

### 2. Multi-granularity, directional influence scoring

The framework proposes relations among heterogeneous elements—concepts, attributes, methods, evidence, constraints, transfer points, and residuals—rather than limiting association to concept-to-concept edges. Influence is directional: an estimated contribution from question A to question B need not equal the reverse. Unknown relations are not silently treated as zero, and estimated influence is not equated with verified scientific value.

### 3. Historical Question Intelligence

AQSI proposes learning from earlier questions and their successes, failures, partial outcomes, costs, and delayed downstream contributions. **Question Differential Trees** offer one candidate mechanism for representing shared structure and differences among related questions. Historical screening is designed to be revisable, so weak initial predictions do not permanently suppress novel research directions.

### 4. Goal-open scoring and research portfolio selection

A question can be evaluated against the surrounding question ecology without requiring a predetermined target question. Portfolio-level selection then considers complementarity, redundancy, uncertainty, diversity, budgets, and strategic constraints. Scores guide research allocation; they do not themselves authorize execution.

### 5. Question Structural Relay and collective learning

Exploration can yield more than an answer: new questions, methods, evidence, counterevidence, unresolved leftovers, or reproducibility observations. The proposed relay mechanisms include derivation, decomposition, composition, cross-domain transfer, refutation, revisiting, and repeated-execution evidence accumulation. Sharing a result is not the same as independently verifying it.

### 6. Strategic Question Control Planes

AQSI separates human-authorized strategic direction, portfolio governance, tactical question selection, and operational exploration. Human stakeholders can specify priorities, limits, and budgets while leaving individual question discovery to AI systems. **Autonomous question discovery, strategic authority, and action authorization remain distinct.**

### 7. UTN-based cross-domain alignment and controlled evolution

Universal Typing and Naming (UTN) is proposed as an alignment mechanism for heterogeneous research structures and cross-domain question transfer. AQSI also examines meta-question discovery and possible co-evolution with other structural intelligence subsystems. Any claimed improvement must be supported by conformance checks and independent evaluation.

## Included Research Materials

### Core papers — `docs/` (10)

- [AQSI-001 — From Answering to Autonomous Questioning](../docs/AQSI-001-From-Answering-to-Autonomous-Questioning.md)
- [AQSI-002 — Biomimetic Question Discovery](../docs/AQSI-002-Biomimetic-Question-Discovery.md)
- [AQSI-003 — Multi-Granularity Structural Influence Factors](../docs/AQSI-003-Multi-Granularity-Structural-Influence-Factors.md)
- [AQSI-004 — Historical Question Intelligence and Differential Trees](../docs/AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md)
- [AQSI-005 — Directional Question Scoring and Portfolio Selection](../docs/AQSI-005-Directional-Question-Scoring-and-Portfolio-Selection.md)
- [AQSI-006 — Question Units and Exploration Contracts](../docs/AQSI-006-Question-Units-and-Exploration-Contracts.md)
- [AQSI-007 — Question Structural Relay and Collective Learning](../docs/AQSI-007-Question-Structural-Relay-and-Collective-Learning.md)
- [AQSI-008 — Strategic Question Control Planes](../docs/AQSI-008-Strategic-Question-Control-Planes.md)
- [AQSI-009 — UTN and Cross-Domain Question Transfer](../docs/AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md)
- [AQSI-010 — MVP Architecture and Recursive Evolution](../docs/AQSI-010-MVP-Architecture-and-Recursive-Evolution.md)

### Specifications — `specs/` (4)

- [SPEC-001 — Canonical Question Unit Contract](../specs/SPEC-001-Canonical-Question-Unit-Contract.md)
- [SPEC-002 — Structural Influence and Scoring Contract](../specs/SPEC-002-Structural-Influence-and-Scoring-Contract.md)
- [SPEC-003 — Question Relay and Exploration Lifecycle](../specs/SPEC-003-Question-Relay-and-Exploration-Lifecycle.md)
- [SPEC-004 — Control Plane and Policy Conformance](../specs/SPEC-004-Control-Plane-and-Policy-Conformance.md)

### Research cases — `cases/` (3)

- [CASE-001 — Single-Domain Autonomous Questioning](../cases/CASE-001-Single-Domain-Autonomous-Questioning.md)
- [CASE-002 — Cross-Domain Question Transfer](../cases/CASE-002-Cross-Domain-Question-Transfer.md)
- [CASE-003 — Research Portfolio and Multi-Agent Relay](../cases/CASE-003-Research-Portfolio-and-Multi-Agent-Relay.md)

### Research extensions — `extensions/` (3)

- [EXT-001 — Question Ecosystem and Meta-Question Discovery](../extensions/EXT-001-Question-Ecosystem-and-Meta-Question-Discovery.md)
- [EXT-002 — Cross-Structural Co-Evolution](../extensions/EXT-002-Cross-Structural-Co-Evolution.md)
- [EXT-003 — Open-Ended Question Intelligence and ASI Boundaries](../extensions/EXT-003-Open-Ended-Question-Intelligence-and-ASI-Boundaries.md)

### Repository navigation and validation

- [README](../README.md), [START-HERE](../START-HERE.md), [CONTENTS](../CONTENTS.md), and [GLOSSARY](../GLOSSARY.md)
- [FIGURE-INDEX](../FIGURE-INDEX.md) — planned figure descriptions and placements
- [FUTURE-DIRECTIONS](../FUTURE-DIRECTIONS.md) and [OPEN-QUESTIONS](../OPEN-QUESTIONS.md)
- [TESTABLE-HYPOTHESES](../TESTABLE-HYPOTHESES.md) and [VALIDATION-ROADMAP](../VALIDATION-ROADMAP.md)
- [CHANGELOG](../CHANGELOG.md), [CITATION.cff](../CITATION.cff), and [`.zenodo.json`](../.zenodo.json)

The project specifies eight figures (`Fig-001` through `Fig-008`). **Before publishing this release, verify that each individually named PNG exists in `figures/` and that its links resolve.** A composite poster does not by itself satisfy eight separate figure paths.

## Proposed Validation Program

The research roadmap separates four stages:

| Stage | Proposed scope | Illustrative validation objective |
| --- | --- | --- |
| **M0** | Single-domain questioning loop | Trace candidate discovery through selection, authorized exploration, and relay |
| **M1** | Historical intelligence and structural scoring | Compare calibrated utility, resource use, and screening quality against ablations |
| **M2** | Cross-domain and multi-agent relay | Test transfer quality, negative-transfer detection, and independently verified reuse |
| **M3** | Controlled recursive evolution | Evaluate proposed system changes against frozen baselines and governance contracts |

Candidate baselines include LLM-only questioning, history-only retrieval, non-directional scoring, and systems without portfolio or relay mechanisms. Evaluation should report negative findings, uncertainty, compute cost, independent evidence quality, and failure cases—not only favorable examples.

## Research Boundaries

- This is a **theory-first publication**, not a demonstration of a production system.
- Worked examples, sample scores, and schemas are illustrative unless separately supported by experimental evidence.
- Structural similarity does not establish valid cross-domain transfer; directional influence estimates do not establish causality.
- Generated questions, model agreement, and repeated model outputs do not by themselves constitute verified knowledge.
- Multi-agent interaction does not automatically constitute collective learning.
- Open-ended questioning does not establish recursive self-improvement or ASI.
- Strategic priorities, research budgets, data access, and action authorization remain subject to explicit governance.

## Collective Learning and Contributions

The repository is intended to support open research discussion, critical review, reproducible experiments, alternative scoring methods, counterexamples, contract revisions, and cross-domain studies. Useful contributions should identify the relevant AQSI document or contract, state assumptions, provide provenance and reproducible evidence where possible, and distinguish observations from conjectures.

Negative results, failed transfers, and unresolved questions are welcome research outputs when clearly documented.

## Citation and License

Please use the repository's [`CITATION.cff`](../CITATION.cff) for citation metadata. A persistent DOI may be added after a successful Zenodo release and should not be inferred from the version tag alone.

Licensed under **Apache License 2.0**; see [`LICENSE`](../LICENSE).

---

**Release statement:** AQSI v1.0.0 establishes a proposed, testable structural framework for autonomous research-question intelligence. Its central invitation is to examine which mechanisms, if any, produce measurable improvements in verified research outcomes under transparent contracts and human governance.
