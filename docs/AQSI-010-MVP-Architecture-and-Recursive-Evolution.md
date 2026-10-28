# AQSI-010 — MVP Architecture and Recursive Evolution

**Project:** Autonomous Questioning Structural Intelligence (AQSI)  
**Version:** v1.0.0 — Initial Research Framework  
**Status:** Research architecture and testable proposal; not an implemented or validated system  
**Document class:** Core research paper (AQSI-010)  
**License:** Apache-2.0

## Abstract

Autonomous Questioning Structural Intelligence (AQSI) proposes a research architecture in which an AI-supported system discovers, represents, evaluates, explores, and relays research questions rather than merely responding to questions supplied by others. This paper integrates the preceding nine AQSI papers into a minimum viable research architecture and a staged program for recursive improvement. Its principal design choice is to treat questions as typed, persistent, evidence-bearing units whose relationships can be evaluated at multiple structural granularities. Historical question intelligence, directional influence scoring, portfolio selection, exploration contracts, and strategic governance are connected by explicit interfaces and provenance-preserving feedback loops. The architecture distinguishes the evolution of a question portfolio from the evolution of the questioning machinery itself. It proposes measurable experiments, conformance gates, failure criteria, and governance constraints. No claim of autonomous scientific discovery, superior performance, or progress toward artificial superintelligence is established by the architecture alone.

**Keywords:** autonomous questioning; structural intelligence; question units; multi-granularity influence; historical question intelligence; question differential trees; UTN; structural relay; portfolio selection; control planes; recursive self-improvement; conformance.

---

## 1. Purpose, Scope, and Research Position

AQSI asks whether a persistent, structurally organized questioning process can improve the efficiency, diversity, and eventual usefulness of AI-assisted inquiry. A conversational model can propose questions, but a sustained research program additionally requires durable identities, historical comparison, calibrated selection, reproducible exploration, explicit evidence, and mechanisms for carrying unresolved problems forward.

This document specifies a *research architecture*, not a completed product. The minimum viable system (MVP) is intended to test narrower claims before expanding into multi-agent coordination or recursive redesign. In particular:

- A high-scoring question is not necessarily a good question.
- A compelling answer is not equivalent to externally validated evidence.
- Question novelty is not equivalent to knowledge gain.
- Structural similarity is not sufficient to justify cross-domain transfer.
- Recursive iteration does not by itself constitute verified self-improvement.
- Human-defined strategic policy is distinct from AI-selected tactical questions and from authorization to act.

The design follows a **specifications-and-contracts-first** sequence: define what must remain true, then build a minimal execution path, then evaluate it against explicit baselines.

## 2. Integration of the AQSI Research Series

| Paper | Principal contribution | Role in the MVP |
|---|---|---|
| AQSI-001 | From answering to autonomous questioning | Research problem and system boundary |
| AQSI-002 | Biomimetic question discovery | Candidate generation from gaps, residuals, associations, and relay |
| AQSI-003 | Multi-granularity structural influence factors | Typed, directed relationship evidence |
| AQSI-004 | Historical question intelligence and differential trees | Retrieval, experience reuse, and question-family comparison |
| AQSI-005 | Directional scoring and portfolio selection | Goal-open ranking and resource-aware choice |
| AQSI-006 | Question units and exploration contracts | Durable objects and bounded execution |
| AQSI-007 | Question structural relay and collective learning | Provenance-preserving learning across inquiries |
| AQSI-008 | Strategic question control planes | Policy, budgets, permissions, and oversight |
| AQSI-009 | UTN and cross-domain question transfer | Typed alignment and controlled transfer |
| **AQSI-010** | Architecture and recursive evolution | Integration, staged validation, and change control |

These contributions are intended to interoperate through contracts. They need not be implemented by a single model or a single algorithm.

## 3. System-Level Architecture

### 3.1 Functional domains

The proposed system has five functional domains and two cross-cutting planes:

1. **Q1 — Discovery:** generate candidate questions from domain knowledge, unresolved gaps, evidence conflicts, structural residuals, historical questions, and incoming relay pieces.
2. **Q2 — Representation:** normalize candidates as Question Units, attach UTN-compatible types, and record multi-granularity features and question-family deltas.
3. **Q3 — Evaluation and Selection:** retrieve historical analogues, estimate directed influence and uncertainty, and select a budget-constrained question portfolio.
4. **Q4 — Exploration:** translate selected questions into prompts, tool calls, experiments, or other authorized research procedures governed by Exploration Contracts.
5. **Q5 — Relay and Evolution:** preserve findings, counterevidence, unresolved leftovers, derived questions, and evaluation outcomes; update historical models and propose controlled system changes.

The **Strategic Question Control Plane (SQCP)** constrains and steers portfolio objectives, budgets, and permissions. A **Conformance and Evidence Plane** checks object validity, provenance, authorization, evaluation protocols, and reproducibility.

### 3.2 Conceptual dataflow

```text
 Domain Knowledge / Historical Corpus / External Relay / Residuals
                              |
                              v
                  [Q1 Candidate Discovery]
                              |
                              v
              [Q2 Question Unit + UTN Typing]
                              |
                  +-----------+-----------+
                  |                       |
                  v                       v
        [Historical Retrieval]   [Influence Factor Graph]
                  |                       |
                  +-----------+-----------+
                              v
                 [Q3 Scoring + Portfolio]
                              ^
                              |
              [SQCP: policy, budgets, authority]
                              |
                              v
                [Q4 Exploration Contracts]
                              |
                              v
             [Evidence / Counterevidence / Results]
                              |
                              v
                  [Q5 Structural Relay]
                    |         |         |
                    v         v         v
                History   New Questions  Change Proposals
                    |         |         |
                    +---------+         v
                         |        [Conformance + Evaluation]
                         +-----------------+
```

The diagram shows logical responsibilities, not a required deployment topology.

### 3.3 Replaceable implementation strategies

Question generation may use an LLM, graph traversal, differential-tree operations, symbolic rules, or domain-specific analyzers. Historical scoring may use retrieval, statistical models, learned rankers, or ensembles. Exploration may be performed by a model, a human, a simulation, or an external laboratory. Each component should advertise capabilities and limitations rather than assume universal applicability.

## 4. Canonical Objects and Interface Boundaries

The MVP requires six minimal object classes:

| Object | Required purpose | Essential fields |
|---|---|---|
| **Question Unit (QU)** | Persistent research question | `question_id`, version, statement, structural descriptors, provenance, status |
| **Influence Record (IR)** | Directed relation between units or factors | source, target, relation type, evidence, uncertainty, timestamp |
| **Historical Outcome (HO)** | Reusable experience | question reference, procedure, outcome, evaluation rubric, cost, limitations |
| **Portfolio Decision (PD)** | Auditable selection | candidates, scores, policy version, constraints, selection rationale |
| **Exploration Contract (EC)** | Bounded inquiry | question reference, permitted actions, budget, evidence criteria, stop conditions |
| **Relay Piece (RP)** | Transferable research result | source references, claims, counterclaims, residuals, recipient context, lineage |

A seventh object, the **Change Proposal (CP)**, is needed once recursive evolution is attempted. It must specify the component to be changed, rationale, expected benefits, risk, test plan, and rollback conditions.

A minimal Question Unit might be represented as follows. The example is illustrative and not a finalized schema:

```yaml
question_id: aqsi:q:000124
version: 1
statement: "Can historical failure patterns improve selection of cross-domain research questions?"
utn_types:
  - research.question
  - transfer.cross_domain
structural_factors:
  - kind: method
    reference: historical_question_scoring
  - kind: uncertainty
    reference: transfer_validity
provenance:
  discovery_mode: residual_driven
  source_refs: [aqsi:rp:000031]
status: candidate
assessment:
  estimated_value: null
  confidence: unassessed
  unknown_relations: true
```

The explicit unknown fields prevent absent evidence from silently becoming zero influence or false certainty.

## 5. Question Discovery and Candidate Formation

Candidate sources include:

- **Gap discovery:** missing premises, unconnected methods, inconsistent models, or untested predictions.
- **Residual discovery:** failed searches, unresolved contract mismatches, unaddressed counterevidence, and explicit leftovers.
- **Association discovery:** multi-granularity relationships between concepts, attributes, mechanisms, methods, constraints, and evidence.
- **Historical variation:** question differential-tree deltas, successful transformations, and previously deferred questions.
- **Relay discovery:** questions generated by another agent, domain, experiment, or execution cycle.
- **Strategic prompts:** broad directions authorized by a human policy, without prescribing every individual question.

Two complementary generation routes should be preserved:

**LLM-first:** generate candidate statements, then normalize, align, and test their structure.

**Structure-first:** identify a promising relation, mismatch, missing edge, or residual, then synthesize a question statement and exploration plan.

A candidate is not accepted merely because it is grammatically well formed. It must have an intelligible research referent, sufficient provenance, a meaningful uncertainty, and at least a plausible route to exploration or explicit deferral.

## 6. Multi-Granularity Influence and Historical Intelligence

### 6.1 Directed influence

For question units \(q_i\) and \(q_j\), let \(H(q)\) denote the set of structural factors attached to a question. A general directional influence estimate is:

\[
\widehat I(q_i\!\rightarrow\!q_j)
= \operatorname{Fold}_{a\in H(q_i),\,b\in H(q_j)}
\bigl(w_{ab},\,R(h_{ia},h_{jb}),\,E_{ab},\,U_{ab}\bigr).
\]

Here \(R\) represents a typed relation; \(E\) captures supporting or opposing evidence; \(U\) captures uncertainty; and `Fold` is a configurable aggregation operator. No single linear aggregation is presumed universally correct. In general,

\[
\widehat I(q_i\!\rightarrow\!q_j) \neq
\widehat I(q_j\!\rightarrow\!q_i).
\]

Influence should be separated from similarity, causal effect, and realized downstream research value. A relation can be strong as a hypothesis yet weakly supported empirically.

### 6.2 Historical question intelligence

A historical record should preserve at least the question, structural representation, selection context, exploration procedure, observed outcome, evaluation criteria, costs, and delayed relay effects. The resulting scorer can estimate a conditional distribution rather than only a point value:

\[
P(Y_q\mid X_q,\mathcal H_t,\pi_t),
\]

where \(X_q\) denotes structural features, \(\mathcal H_t\) the historical corpus, and \(\pi_t\) the historical selection policy. Conditioning on the selection policy matters because previously explored questions are not a random sample of all candidates.

The MVP should support an explicit **defer/revisit** decision. Low predicted value must not mean irreversible deletion, especially for novel question families with little historical coverage.

### 6.3 Differential trees

Question Differential Trees (QDTs) can encode a shared structural core plus variations:

\[
q_k = \operatorname{Instantiate}(C,\Delta_k,\Gamma_k),
\]

where \(C\) is a shared core, \(\Delta_k\) is a question-specific structural delta, and \(\Gamma_k\) is the relevant domain and evidence context. QDTs may improve retrieval and transfer, but their compression and scoring value must be measured rather than assumed.

## 7. Goal-Open Scoring and Portfolio Selection

A useful baseline, in the absence of a predetermined target question, is the aggregate outgoing influence:

\[
S_{\mathrm{out}}(q_i)=\sum_{j\ne i}\widehat I(q_i\rightarrow q_j).
\]

This is a **baseline hypothesis**, not a proof of research utility. It can favor broadly connected questions, reward inflated relationship estimates, and miss rare but transformative questions. Accordingly, the architecture supports alternative scorers and uncertainty-aware portfolio policies.

A general portfolio decision is:

\[
P_t^* \in \arg\max_{P\subseteq Q_t}
\mathbb E\bigl[V(P\mid \mathcal H_t,\pi_t)\bigr]
\quad \text{subject to } C(P)\le B_t,\;P\in\mathcal F_t.
\]

Here \(B_t\) is the authorized budget and \(\mathcal F_t\) is the set of policy-compliant portfolios. The value function may incorporate expected information gain, structural relay potential, diversity, redundancy, confidence, and deferred exploration opportunities. These are candidate objectives to compare empirically, not mandatory additive bonuses.

A minimal portfolio should include a controlled exploration allocation for uncertain, historically underrepresented question families. Its size is a policy choice, not a universal constant.

## 8. Exploration Contracts and Evidence Discipline

A selected question is converted into an Exploration Contract before execution. Each contract identifies:

1. The question and the current hypothesis or uncertainty.
2. Allowed tools, models, data sources, and external actions.
3. Budget, time, stop conditions, and human-approval requirements.
4. Evidence standards, expected outputs, and negative-result handling.
5. Provenance, privacy, licensing, and reproducibility constraints.
6. Criteria for closure, deferral, revision, or relay.

The system should distinguish:

- **Generated conjecture:** a proposed explanation or answer.
- **Internal consistency check:** whether the proposal follows from stated assumptions.
- **External observation:** a measurement or source-derived fact.
- **Independent validation:** a test not merely repeating the same model judgment.
- **Counterevidence:** observations that weaken or falsify the proposal.
- **Unresolved residual:** what remains unknown after the exploration.

Exploration may produce a useful new question without resolving the original one. That result should be preserved, but not counted automatically as validated progress.

## 9. Structural Relay and Collective Learning

Relay is the persistence and transfer of research-relevant structure, not simply the forwarding of text. A Relay Piece may contain a derived question, a failed method, a reusable test, an influence-factor update, a counterexample, or a new UTN type proposal.

Supported relay operations can include `derive`, `split`, `compose`, `transfer`, `refute`, `revisit`, `replicate`, `fold`, and `unfold`. Their meaning should be specified by contracts and recorded with lineage.

**Repeated execution is also a candidate relay mode.** Repeating an inquiry can accumulate data, assess reproducibility, reveal drift, or quantify uncertainty. Identical repetition without new information is not automatically valuable; the value depends on the evidence gained and its cost.

Collective learning requires attention to attribution, licensing, privacy, conflicting evidence, domain-specific semantics, and the ability to reject an imported relay piece without corrupting local state.

## 10. Strategic Control Plane and Human Sovereignty

The SQCP separates four layers:

| Layer | Governs | Typical decisions |
|---|---|---|
| Strategic | Human-authorized goals and boundaries | Research domains, prohibited actions, acceptable risk |
| Portfolio | Resource allocation | Budget shares, diversity, exploration reserves |
| Tactical | Candidate prioritization | Question scoring, comparison, deferral, revisit |
| Operational | Individual execution | Tool permissions, experiment limits, escalation |

Human stakeholders may change strategic direction; AQSI may recommend policy adjustments using evidence, but must not treat such recommendations as authority to modify its own permissions.

A key invariant is:

> **Question selection is not action authorization.**

Policy versions and decision rationales must be attached to portfolio decisions so that later evaluators can distinguish algorithmic improvements from changes in budget, domain, or strategic priorities.

## 11. MVP Staging: Conformance Before Runtime

### M0 — Single-domain research loop

**Objective:** demonstrate a traceable end-to-end cycle within one bounded domain.

**Minimum components:** candidate generator, Question Unit store, simple typed factors, historical retrieval, one baseline scorer, small portfolio selector, exploration contract checker, evidence store, relay writer.

**Required demonstration:** generate candidates; reject malformed ones; rank or defer them; explore an authorized subset; record outcomes and counterevidence; derive or revisit questions; reproduce the decision trail.

**Exit gate:** schema and lifecycle conformance, no unauthorized actions, traceable provenance, and a repeatable evaluation dataset. An end-to-end demo alone is insufficient.

### M1 — Multi-granularity and historical scoring

**Objective:** test whether structural factors and historical experience improve selection relative to simpler baselines.

**Additions:** typed influence records, question differential trees, historical outcome calibration, uncertainty and missing-relation handling, delayed-value tracking.

**Exit gate:** predefined metrics, statistically interpretable comparisons, and failure analyses showing where the added machinery helps or hurts.

### M2 — Cross-domain and multi-agent relay

**Objective:** test transfer and collaborative question development.

**Additions:** UTN alignment, semantic contract checks, multiple explorer roles, relay import/export, disagreement and evidence reconciliation.

**Exit gate:** measured transfer validity, attribution preservation, explicit handling of semantic drift, and comparisons against unstructured collaboration.

### M3 — Controlled recursive improvement

**Objective:** determine whether the system can propose, test, and retain beneficial changes to its own question-generation and evaluation components.

**Additions:** change proposals, isolated evaluation sandboxes, immutable benchmark suites, deployment approval, rollback, and long-horizon monitoring.

**Exit gate:** independently measured improvement on held-out tasks without unacceptable regression, budget inflation, evidence degradation, or policy violations.

Progression between stages is contingent on evidence, not calendar time.

## 12. Reference MVP Algorithm

The following pseudocode describes the research loop, not a production implementation:

```text
function AQSI_CYCLE(domain_state, history, policy, budget):
    candidates = DISCOVER(domain_state, history, incoming_relay)
    question_units = NORMALIZE_AND_VALIDATE(candidates)

    aligned = UTN_ALIGN(question_units, domain_state)
    relations = ESTIMATE_TYPED_INFLUENCES(aligned, history)
    history_estimates = RETRIEVE_AND_SCORE_HISTORY(aligned, history)

    decisions = SELECT_PORTFOLIO(
        aligned, relations, history_estimates,
        policy=policy, budget=budget,
        preserve_uncertain_exploration=True
    )
    AUDIT(decisions, policy)

    outcomes = []
    for question in decisions.selected:
        contract = BUILD_EXPLORATION_CONTRACT(question, policy)
        if not CONFORMS(contract, policy):
            outcomes.append(DEFER_WITH_REASON(question))
            continue
        result = EXECUTE_WITHIN_CONTRACT(contract)
        outcomes.append(ASSESS_EVIDENCE(result, contract))

    relay = PRODUCE_RELAY_PIECES(outcomes, preserve_leftovers=True)
    updated_history = APPEND_IMMUTABLE_EVENTS(history, decisions, outcomes, relay)
    proposals = PROPOSE_COMPONENT_CHANGES(updated_history)

    return updated_history, relay, proposals
```

The last line does not automatically deploy proposals. Recursive changes enter a separate validation process.

## 13. Recursive Evolution: What Changes, and Who Approves It?

AQSI distinguishes three evolution loops:

**Loop A — Question ecosystem evolution.** New questions, refinements, counterquestions, and residuals expand or reorganize the research portfolio. This is the basic loop and does not imply changes to system algorithms.

**Loop B — Model and structure evolution.** Historical scoring functions, influence-factor taxonomies, differential-tree templates, and UTN alignments are updated using accumulated evidence. These updates require versioning and comparative tests.

**Loop C — Architecture and governance proposals.** The system may propose new discovery operators, portfolio policies, relay contracts, or resource strategies. Adoption requires an authorized evaluator, sandbox testing, and an explicit approval path.

A candidate improvement \(\Delta_t\) is accepted only if its evaluation satisfies predetermined constraints:

\[
\operatorname{Accept}(\Delta_t)=
\mathbf 1\{\Delta \widehat U_{\mathrm{heldout}}>\tau\}
\cdot \mathbf 1\{\operatorname{Conformance}(\Delta_t)=\mathrm{pass}\}
\cdot \mathbf 1\{\operatorname{Risk}(\Delta_t)\le r_{\max}\}.
\]

The notation is illustrative: practical acceptance may require confidence intervals, multiple independent tests, and human approval. It is important to measure **net** gains after accounting for evaluation cost and additional compute.

### 13.1 Anti-Goodhart safeguards

- Freeze held-out evaluation suites before testing proposed changes.
- Keep independent evidence sources where feasible.
- Compare against equal-budget baselines.
- Monitor calibration, diversity, failure rates, and cost—not only a single success score.
- Detect self-reinforcing cycles in which the system generates questions optimized for its own scorer.
- Retain negative results and failed change proposals in the history.
- Require rollback and independent authorization for changes affecting policy or execution permissions.

## 14. Evaluation Framework and Baselines

### 14.1 Research questions

- Does structured historical retrieval reduce redundant or low-value exploration?
- Do multi-granularity factors improve prediction of useful downstream research outcomes?
- Does directed influence provide information beyond symmetric similarity?
- Does portfolio selection outperform top-\(k\) independent question ranking at equal cost?
- Does structure-first generation uncover useful questions missed by LLM-first generation?
- Does typed cross-domain relay improve transfer validity?
- Does controlled recursive evolution yield sustained held-out gains rather than benchmark overfitting?

### 14.2 Baseline systems

| Baseline | Description | Primary comparison |
|---|---|---|
| B0 | LLM-only question brainstorming | Value of persistent structure |
| B1 | LLM + ordinary retrieval | Value of typed question history |
| B2 | Historical scoring without QDT | Value of differential-tree organization |
| B3 | Symmetric similarity graph | Value of directional influence |
| B4 | Single-score top-\(k\) selection | Value of portfolio optimization |
| B5 | Cross-domain transfer without UTN checks | Value of typed alignment |
| B6 | Repeated prompting without relay contracts | Value of structured relay |
| B7 | Self-tuning without held-out gates | Value of controlled recursive improvement |

Baselines should be matched for model access, available information, and total research budget as far as practicable.

### 14.3 Outcome measures

**Primary outcomes:** independently assessed question utility, verified information gain, cost per validated result, and downstream reuse of relay artifacts.

**Secondary outcomes:** candidate diversity, redundancy, calibration error, proportion of deferred questions later recovered, provenance completeness, transfer error rate, and time-to-useful-evidence.

**Governance outcomes:** authorization violations, policy conformance, untraceable evidence, rollback success, and unintended resource use.

Delayed value should be reported at fixed follow-up horizons to avoid selectively crediting only successful descendants.

## 15. Testable Hypotheses and Falsification Conditions

| ID | Hypothesis | Evidence that would weaken or refute it |
|---|---|---|
| H1 | Historical question intelligence improves useful-question selection at fixed budget. | No significant gain versus retrieval-only or random baselines on held-out domains. |
| H2 | Multi-granularity typed influence improves downstream utility prediction. | Equal or worse calibration and ranking than simpler semantic similarity. |
| H3 | Directional influence adds predictive value beyond symmetric relations. | No incremental predictive performance after controlling for graph complexity. |
| H4 | Structure-first generation adds valuable candidates beyond LLM-first generation. | Added candidates are mostly redundant, invalid, or too costly to validate. |
| H5 | Portfolio selection yields better verified outcomes than independent top-\(k\). | No equal-budget gain or excessive diversity-related opportunity cost. |
| H6 | QDTs improve reuse and adaptation of historical question patterns. | No gain in retrieval, transfer, or cost after representation overhead. |
| H7 | UTN alignment reduces harmful cross-domain transfer. | Error rates do not improve, or alignment blocks useful transfer disproportionately. |
| H8 | Explicit relay increases cumulative reusable knowledge. | No measurable downstream reuse or quality advantage over unstructured notes. |
| H9 | SQCP supports controllable research allocation without suppressing useful discovery. | High policy compliance but substantial loss of useful exploration versus matched alternatives. |
| H10 | Gated recursive changes improve held-out performance sustainably. | Gains disappear on new tasks, or costs/risks exceed benefits. |

All hypotheses remain open until tested. Negative outcomes should be published with experimental conditions and limitations.

## 16. Three Illustrative MVP Scenarios

### 16.1 Case A: Single-domain software engineering

A bounded code-analysis corpus yields questions about test gaps, API contracts, and recurring failure modes. AQSI creates typed Question Units, retrieves related historical cases, selects a portfolio under a fixed tool budget, and explores them using read-only analysis or sandboxed tests. Outcomes are independently checked against known issues or newly verified failures. This case can establish basic conformance without asserting autonomous software engineering capability.

### 16.2 Case B: Cross-domain method transfer

A method that helped identify anomalies in one domain is proposed for another domain with different observability and assumptions. UTN-compatible factor alignment records what transfers, what changes, and what remains unknown. A transfer question is explored with matched controls; negative results produce a counterevidence relay piece. Success requires a valid, externally checked transfer, not merely a persuasive analogy.

### 16.3 Case C: Research portfolio governance

A human sponsor allocates a fixed research budget among near-term validation, foundational questions, and exploratory cross-domain work. AQSI selects specific questions subject to those constraints and records the policy version, estimated value, uncertainty, and final evidence. The sponsor may change allocation priorities, but AI-generated policy suggestions do not self-authorize the change.

These scenarios are proposed test designs, not reports of completed experiments.

## 17. Failure Modes and Explicit Leftovers

| Failure mode | Consequence | Proposed mitigation |
|---|---|---|
| Influence inflation | Highly connected but unproductive questions dominate | Calibrated influence, held-out outcomes, uncertainty |
| Historical selection bias | Novel questions are prematurely discarded | Exploration reserve, defer/revisit, propensity-aware analysis |
| Semantic drift | Invalid cross-domain analogy | UTN contracts, domain validation, counterexamples |
| Evidence laundering | Model-generated text appears externally validated | Evidence types, provenance, independent checks |
| Relay explosion | Unmanageable duplicate questions and artifacts | QDT grouping, deduplication, lineage-aware folding |
| Metric gaming | Apparent RSI without real improvement | Frozen benchmarks, independent evaluation, equal-budget tests |
| Over-centralized control | Exploration diversity collapses | Policy-visible exploration allocations and review |
| Under-governed autonomy | Unauthorized actions or resource consumption | Contract checks, approval gates, immutable audit trails |
| Hidden cost | Apparent gains vanish after compute/tool overhead | Net utility and cost reporting |

**Explicit leftovers** for subsequent work include formal semantics of influence, principled treatment of unknown edges, causal attribution of delayed relay value, calibration under domain shift, portfolio regret bounds, privacy-preserving collective learning, and robust human evaluation of question quality.

## 18. Conformance Gates and Proposed Specifications

The architecture is intended to be accompanied by four normative specifications:

- [`SPEC-001-Canonical-Question-Unit-Contract.md`](../specs/SPEC-001-Canonical-Question-Unit-Contract.md): identities, fields, versions, provenance, and lifecycle.
- [`SPEC-002-Structural-Influence-and-Scoring-Contract.md`](../specs/SPEC-002-Structural-Influence-and-Scoring-Contract.md): typed relations, uncertainty, evidence, and scorer interchangeability.
- [`SPEC-003-Question-Relay-and-Exploration-Lifecycle.md`](../specs/SPEC-003-Question-Relay-and-Exploration-Lifecycle.md): exploration state transitions, relay provenance, and leftover handling.
- [`SPEC-004-Control-Plane-and-Policy-Conformance.md`](../specs/SPEC-004-Control-Plane-and-Policy-Conformance.md): policy authority, budget limits, approvals, and auditability.

Before runtime evaluation, an implementation should demonstrate:

1. Stable question identities and versioned state transitions.
2. Reproducible scoring inputs and recorded model/policy versions.
3. Explicit unknown, missing, and counterevidence states.
4. Preservation of source attribution through relay operations.
5. Enforced exploration permissions and budgets.
6. Recoverable deferred questions and explicit leftovers.
7. Immutable evaluation records and repeatable baseline comparisons.
8. Rollback of any recursively proposed system change.

These are proposed gates; the linked specifications will define their exact normative tests.

## 19. Relationship to the Wider Structural Intelligence Research Program

AQSI is intended as a question-centric layer that can interoperate with other structural intelligence research directions:

- **SIF:** problem/capability mapping, localization, and structural control.
- **UTN:** typed identity, cross-domain addressing, and semantic alignment.
- **UCPSF:** configurable scoring, folding, and perspective-aware evaluation.
- **MDI / BM-ODWEI:** directional relations, weak signals, and non-exact structural associations.
- **UIERU:** portable exploration units, multi-trail research, and relay ecosystems.
- **SRSI:** rich evaluators, controlled recursive change, and anti-Goodhart validation.
- **SSI:** explicit subject boundaries, values, and human/AI authority distinctions.

These are proposed interfaces and conceptual connections, not claims that the separate frameworks have already been integrated or independently validated.

## 20. Open Research Directions

Important directions beyond the MVP include causal influence estimation, active-learning selection of questions, formal portfolio guarantees, domain-specific exploration contracts, multi-agent disagreement resolution, question-family evolution, adaptive UTN ontology governance, long-horizon delayed-value accounting, and interoperable relay exchange among independent research organizations.

The broader aspiration of open-ended question intelligence should remain an empirical research direction. Nothing in the present architecture establishes a path to artificial general intelligence or artificial superintelligence.

## 21. Conclusion

AQSI proposes that questions themselves can become durable, typed, evaluated, and transferable units of structural intelligence. The resulting system is more than an automated prompt generator: it is a candidate research loop connecting discovery, representation, directional scoring, historical learning, exploration contracts, strategic control, and structural relay. The proposed MVP deliberately begins with a bounded single-domain system and advances only when conformance and held-out evaluation justify additional complexity. Recursive evolution is treated as a separately governed hypothesis, not as an automatic consequence of iteration.

The central contribution of this paper is therefore an **integrated, falsifiable architecture and staged research program**. Its value will depend on whether implementations produce measurable, reproducible improvements over simpler alternatives while preserving evidence quality, resource discipline, and human authority.

---

## Appendix A. Minimal Research Event Ledger

An append-only event stream can record the sequence of decisions without prescribing a database technology:

```yaml
event_id: aqsi:event:000911
event_type: question.exploration.completed
timestamp: "2026-10-28T00:00:00Z"  # illustrative only
question_id: aqsi:q:000124
question_version: 1
policy_version: sqcp:v1
exploration_contract: aqsi:ec:000043
outcome_ref: aqsi:outcome:000067
evidence_refs:
  - aqsi:evidence:000401
counterevidence_refs: []
leftover_refs:
  - aqsi:residual:000014
```

The event structure should allow reconstruction of a historical score using only information available at the time of the original decision, preventing future-evidence leakage.

## Appendix B. Evaluation Protocol Checklist

- [ ] Define domain, question pool, and authorized resources before evaluation.
- [ ] Freeze primary metrics and test partitions.
- [ ] Compare against matched LLM-only and retrieval baselines.
- [ ] Include directional-versus-symmetric and typed-versus-untyped ablations.
- [ ] Record model versions, prompts, seeds where applicable, and tool budgets.
- [ ] Use independent assessment for claims of verified knowledge gain.
- [ ] Track uncertainty, negative results, and deferred questions.
- [ ] Evaluate transfer on domains absent from training or tuning.
- [ ] Report costs, policy violations, and calibration—not just successes.
- [ ] Publish limitations and failed hypotheses alongside positive findings.

## Appendix C. Publication and Research Integrity Notes

This document is a theory-first research proposal. Illustrative formulas, object schemas, workflows, and examples are candidate designs. They do not constitute evidence of empirical superiority, deployment readiness, or autonomous scientific achievement. Any later implementation should publish versioned specifications, conformance results, reproducible evaluations, and relevant negative findings. External scientific literature and DOI references should be added only after verification; no external experimental findings are asserted here.

---

**Suggested figure placement:** `../figures/Fig-008-UTN-Cross-Domain-Relay-and-RSI.png` after Section 13 or Section 19, with a caption distinguishing proposed architecture from implemented capability. See [`FIGURE-INDEX.md`](../FIGURE-INDEX.md).

**Companion documents:** [`README.md`](../README.md), [`CONTENTS.md`](../CONTENTS.md), [`TESTABLE-HYPOTHESES.md`](../TESTABLE-HYPOTHESES.md), and [`VALIDATION-ROADMAP.md`](../VALIDATION-ROADMAP.md).
