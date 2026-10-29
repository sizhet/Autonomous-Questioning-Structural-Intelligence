# CONTENTS — Autonomous Questioning Structural Intelligence (AQSI)

**Release:** v1.0.0 — Initial Research Framework  
**Status:** Theory-first research framework; proposed contracts and validation plans, not a claim of demonstrated autonomous scientific discovery.  
**Repository:** `Autonomous-Questioning-Structural-Intelligence`

## Purpose and Navigation

AQSI investigates how AI systems might discover, represent, evaluate, select, explore, and relay research questions, rather than merely answer externally supplied prompts. This index provides the canonical reading order and repository map. All links are relative to the repository root.

**New readers:** begin with [README](README.md) and [START-HERE](START-HERE.md).  
**Researchers:** follow the ten core papers, then the relevant specifications, cases, and extensions.  
**Implementers:** read [AQSI-006](docs/AQSI-006-Question-Units-and-Exploration-Contracts.md), [AQSI-010](docs/AQSI-010-MVP-Architecture-and-Recursive-Evolution.md), and the four specifications before proposing runtime implementations.

## I. Core Research Papers — `docs/`

| ID | Document | Primary focus |
|---|---|---|
| AQSI-001 | [From Answering to Autonomous Questioning](docs/AQSI-001-From-Answering-to-Autonomous-Questioning.md) | Motivation, conceptual scope, five functional domains, scientific boundaries |
| AQSI-002 | [Biomimetic Question Discovery](docs/AQSI-002-Biomimetic-Question-Discovery.md) | Gap-, residual-, association-, and relay-driven question discovery |
| AQSI-003 | [Multi-Granularity Structural Influence Factors](docs/AQSI-003-Multi-Granularity-Structural-Influence-Factors.md) | Typed structural factors, directional influence, cross-granularity folding |
| AQSI-004 | [Historical Question Intelligence and Differential Trees](docs/AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md) | Historical feedback, question families, screening, revisit and delayed value |
| AQSI-005 | [Directional Question Scoring and Portfolio Selection](docs/AQSI-005-Directional-Question-Scoring-and-Portfolio-Selection.md) | Goal-open scoring, uncertainty, budgets, portfolio diversity |
| AQSI-006 | [Question Units and Exploration Contracts](docs/AQSI-006-Question-Units-and-Exploration-Contracts.md) | Persistent question objects, expression adapters, exploration authorization |
| AQSI-007 | [Question Structural Relay and Collective Learning](docs/AQSI-007-Question-Structural-Relay-and-Collective-Learning.md) | Question-to-question relay, evidence, counterevidence, repeated execution |
| AQSI-008 | [Strategic Question Control Planes](docs/AQSI-008-Strategic-Question-Control-Planes.md) | Human strategic authority, resource allocation, policy conformance |
| AQSI-009 | [UTN and Cross-Domain Question Transfer](docs/AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md) | Typed alignment, analogy limits, question and method transfer |
| AQSI-010 | [MVP Architecture and Recursive Evolution](docs/AQSI-010-MVP-Architecture-and-Recursive-Evolution.md) | System integration, M0–M3 validation, controlled recursive improvement |

### Suggested thematic paths

- **Question discovery and learning:** AQSI-002 → AQSI-004 → AQSI-003 → AQSI-005.
- **Structural interoperability:** AQSI-003 → AQSI-006 → AQSI-007 → AQSI-009.
- **Governance and system architecture:** AQSI-008 → AQSI-005 → AQSI-010.
- **Research validation:** AQSI-010 → [TESTABLE-HYPOTHESES](TESTABLE-HYPOTHESES.md) → [VALIDATION-ROADMAP](VALIDATION-ROADMAP.md).

## II. Normative-Style Research Specifications — `specs/`

These are proposed contracts for future conformance testing, not an assertion that a reference runtime has passed them.

| ID | Document | Contract scope |
|---|---|---|
| SPEC-001 | [Canonical Question Unit Contract](specs/SPEC-001-Canonical-Question-Unit-Contract.md) | Identity, typing, provenance, structural representation, lifecycle |
| SPEC-002 | [Structural Influence and Scoring Contract](specs/SPEC-002-Structural-Influence-and-Scoring-Contract.md) | Directionality, unknown values, evidence, folding, scoring interfaces |
| SPEC-003 | [Question Relay and Exploration Lifecycle](specs/SPEC-003-Question-Relay-and-Exploration-Lifecycle.md) | Exploration state, relay operators, evidence and feedback integrity |
| SPEC-004 | [Control Plane and Policy Conformance](specs/SPEC-004-Control-Plane-and-Policy-Conformance.md) | Strategic authority, budgets, authorization, policy and audit trails |

**Contract interpretation:** selecting a question does not authorize an action; an influence estimate is not verified research value; an unknown relation must not silently be treated as zero.

## III. Worked Research Cases — `cases/`

| ID | Document | Scenario |
|---|---|---|
| CASE-001 | [Single-Domain Autonomous Questioning](cases/CASE-001-Single-Domain-Autonomous-Questioning.md) | CI flaky-test research and a minimal question–exploration–relay loop |
| CASE-002 | [Cross-Domain Question Transfer](cases/CASE-002-Cross-Domain-Question-Transfer.md) | From CI intermittent failures to sensor-network anomalies |
| CASE-003 | [Research Portfolio and Multi-Agent Relay](cases/CASE-003-Research-Portfolio-and-Multi-Agent-Relay.md) | Policy-guided research budgets, agent roles, collective learning |

**Evidence status:** illustrative scores, allocations, and outcomes in worked cases are examples, not measured empirical results.

## IV. Research Extensions — `extensions/`

| ID | Document | Research frontier |
|---|---|---|
| EXT-001 | [Question Ecosystem and Meta-Question Discovery](extensions/EXT-001-Question-Ecosystem-and-Meta-Question-Discovery.md) | Questions about question-generating systems and their evolution |
| EXT-002 | [Cross-Structural Co-Evolution](extensions/EXT-002-Cross-Structural-Co-Evolution.md) | Interactions among AQSI, UTN, scoring, SIF, UIERU, and RSI |
| EXT-003 | [Open-Ended Question Intelligence and ASI Boundaries](extensions/EXT-003-Open-Ended-Question-Intelligence-and-ASI-Boundaries.md) | Open-ended exploration, verification limits, governance and ASI claims |

## V. Figures — `figures/`

| Figure | File | Companion text |
|---|---|---|
| Fig-001 | [AQSI Grand Architecture](figures/Fig-001-AQSI-Grand-Architecture.png) | AQSI-001, AQSI-010 |
| Fig-002 | [Sources of Autonomous Questions](figures/Fig-002-Sources-of-Autonomous-Questions.png) | AQSI-002 |
| Fig-003 | [Multi-Granularity Influence Graph](figures/Fig-003-Multi-Granularity-Influence-Graph.png) | AQSI-003 |
| Fig-004 | [Historical Question Intelligence](figures/Fig-004-Historical-Question-Intelligence.png) | AQSI-004 |
| Fig-005 | [Directional Scoring and Portfolio Selection](figures/Fig-005-Directional-Scoring-and-Portfolio-Selection.png) | AQSI-005 |
| Fig-006 | [Question Unit and Structural Relay](figures/Fig-006-Question-Unit-and-Structural-Relay.png) | AQSI-006, AQSI-007 |
| Fig-007 | [Strategic Question Control Plane](figures/Fig-007-Strategic-Question-Control-Plane.png) | AQSI-008 |
| Fig-008 | [UTN Cross-Domain Relay and RSI](figures/Fig-008-UTN-Cross-Domain-Relay-and-RSI.png) | AQSI-009, AQSI-010 |

See [FIGURE-INDEX.md](FIGURE-INDEX.md) for captions, usage and placement guidance.

## VI. Repository-Level Guides and Research Governance

| File | Role |
|---|---|
| [README.md](README.md) | Project introduction and contributions |
| [START-HERE.md](START-HERE.md) | Audience-specific reading paths |
| [CONTENTS.md](CONTENTS.md) | Canonical repository index (this file) |
| [GLOSSARY.md](GLOSSARY.md) | Terms, distinctions, and acronyms |
| [FIGURE-INDEX.md](FIGURE-INDEX.md) | Figure catalog and insertion guidance |
| [FUTURE-DIRECTIONS.md](FUTURE-DIRECTIONS.md) | Future research directions |
| [OPEN-QUESTIONS.md](OPEN-QUESTIONS.md) | Unresolved issues and explicit leftovers |
| [TESTABLE-HYPOTHESES.md](TESTABLE-HYPOTHESES.md) | Falsifiable claims and experimental contrasts |
| [VALIDATION-ROADMAP.md](VALIDATION-ROADMAP.md) | M0–M3 validation milestones |
| [CHANGELOG.md](CHANGELOG.md) | Version history |
| [CITATION.cff](CITATION.cff) | Machine-readable citation metadata |
| [.zenodo.json](.zenodo.json) | Zenodo deposit metadata |
| [LICENSE.txt](LICENSE.txt) | Apache-2.0 licensing text |

Some repository-level publication assets may be prepared after the core papers; links above are the intended canonical paths and should be checked during release review.

## VII. Release and ResearchGate Assets — `release/`

| Asset | Purpose |
|---|---|
| [GitHub-Release-Notes-v1.0.0.md](release/GitHub-Release-Notes-v1.0.0.md) | Initial framework release description |
| [ResearchGate-Description.txt](release/ResearchGate-Description.txt) | Plain-text project description |
| [AQSI-v1.0.0-ResearchGate-Overview.pdf](release/AQSI-v1.0.0-ResearchGate-Overview.pdf) | One-page research overview and navigation |

Do not add a DOI to any of these documents until an actual DOI has been assigned. Do not represent the framework as empirically validated solely because it has been released or archived.

## VIII. Research Lifecycle and Cross-References

```text
Question sources and observed residuals
          ↓
Question discovery (AQSI-002)
          ↓
Typed, multi-granularity question representation (AQSI-003, SPEC-001)
          ↓
Historical assessment and differential trees (AQSI-004)
          ↓
Directional scoring and portfolio selection (AQSI-005, SPEC-002)
          ↓
Human-governed authorization (AQSI-008, SPEC-004)
          ↓
Exploration contracts and evidence collection (AQSI-006, SPEC-003)
          ↓
Structural relay and collective learning (AQSI-007)
          ↓
Cross-domain transfer and system improvement (AQSI-009, AQSI-010)
          ↺
```

The flow is a proposed architecture, not a claim that every module must be implemented as a separate service. It supports multiple representations and alternative scoring or execution mechanisms under explicit contracts.

## IX. Research Principles and Boundaries

1. **Specifications before runtime:** articulate identities, interfaces, conformance tests, and authority boundaries before implementation claims.
2. **Evidence before claims:** separate hypotheses, simulations, illustrative examples, independent observations, and validated results.
3. **Multi-granularity over single-relation assumptions:** allow heterogeneous typed factors and directional influence, with uncertainty and provenance.
4. **History without lock-in:** use past successes and failures to improve prioritization without permanently excluding novel or initially low-scoring questions.
5. **Human strategic sovereignty:** AI-generated recommendations do not grant policy-making or execution authority.
6. **Explicit leftovers and counterevidence:** preserve failures, unresolved questions, alternative perspectives, and delayed value for future relay.
7. **Collective Learning Friendly:** support reproducible critiques, competing methods, interoperable research artifacts, and transparent revision.
8. **Open-endedness is not ASI:** ongoing question generation, useful discovery, verified recursive improvement, and superintelligence are distinct claims requiring distinct evidence.

## X. Release Readiness Checklist

- [ ] All 10 `docs/` papers are present and links resolve.
- [ ] All 4 `specs/` files are present and terminology is consistent.
- [ ] All 3 `cases/` and 3 `extensions/` files are present.
- [ ] Eight *individual* figure PNGs exist under the exact listed names; captions match their content.
- [ ] README, START-HERE, CONTENTS, GLOSSARY and FIGURE-INDEX cross-links work.
- [ ] Research hypotheses, validation plan, and open questions are linked and internally consistent.
- [ ] Apache-2.0 license and citation/deposit metadata are reviewed.
- [ ] Release notes and ResearchGate materials accurately describe evidence status.
- [ ] No unassigned DOI, fabricated benchmark, or unsupported performance claim appears.

---

**AQSI v1.0.0 is a research proposal and specification-oriented framework.** Its scientific value depends on future implementation, comparison with baselines, independent testing, and transparent reporting of both positive and negative results.
