# CASE-003 — Research Portfolio and Multi-Agent Relay

**Project:** Autonomous Questioning Structural Intelligence (AQSI)  
**Version:** v1.0.0 — Initial Research Framework  
**Document type:** Illustrative research case / proposed MVP  
**Status:** Design proposal; no implemented system or empirical results are claimed  
**Scope:** Strategic research allocation, question portfolios, multi-agent exploration, structural relay, and collective learning

## Abstract

This case develops a proposed research-portfolio scenario in which a human research sponsor allocates a bounded budget across competing directions while multiple AI research agents autonomously discover, evaluate, investigate, and relay questions. It connects Strategic Question Control Planes (SQCP), multi-granularity structural influence, Historical Question Intelligence (HQI), portfolio selection, canonical Question Units (QUs), exploration contracts, and cross-agent structural relay. The illustrative setting is a research program on reliable distributed sensing and software infrastructure, where near-term reliability work competes with foundational methods and cross-domain discovery. A worked synthetic cycle shows how policy-constrained autonomy differs from both centrally prescribed tasks and unconstrained agent swarms. It specifies measurable outcomes, governance invariants, adversarial tests, and a staged MVP. **Every numerical value, score, budget, agent response, and outcome in this case is hypothetical and is not experimental evidence.**

**Keywords:** AQSI, strategic question control plane, research portfolio, multi-agent relay, question intelligence, historical scoring, structural influence, UTN, evidence provenance, human research sovereignty, collective structural learning

---

## 1. Purpose and Research Question

A research organization rarely has enough resources to explore every plausible question. The challenge is not only to rank individual questions, but to decide which *combination of investigations* should receive resources, which agents may undertake them, and how findings and failures should influence subsequent choices.

The central research question is:

> Under a fixed budget and explicit human research policy, can AQSI's structured question portfolio and multi-agent relay produce more independently useful, diverse, auditable, and reusable research progress than fixed-task, single-agent, or unstructured multi-agent baselines?

This is a falsifiable research hypothesis, not a claim that AQSI has already outperformed these alternatives.

### 1.1 Boundaries

The scenario assumes:

- A **human-authorized** research policy and a fixed experimental budget.
- A finite, auditable set of candidate Question Units.
- Several agents with differentiated roles, but no assumption that specialization guarantees better reasoning.
- Typed records for questions, evidence, assessments, decisions, and relay artifacts.
- A separation between **ranking**, **selection**, **assignment**, and **execution authorization**.
- External validation where possible; model agreement alone is not accepted as scientific confirmation.

The scenario does not assume general autonomous scientific competence, unrestricted tool access, or a proven route to recursive self-improvement or ASI.

## 2. Framework Connections

| Research document | Role in this case |
|---|---|
| `AQSI-001-From-Answering-to-Autonomous-Questioning.md` | Motivation and the distinction between answering and autonomous question discovery |
| `AQSI-002-Biomimetic-Question-Discovery.md` | Gap-, residual-, association-, and relay-driven question generation |
| `AQSI-003-Multi-Granularity-Structural-Influence-Factors.md` | Typed, heterogeneous, directional influence estimates |
| `AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md` | Historical retrieval, calibrated prediction, defer/revisit logic |
| `AQSI-005-Directional-Question-Scoring-and-Portfolio-Selection.md` | Goal-open ranking and resource-constrained portfolio selection |
| `AQSI-006-Question-Units-and-Exploration-Contracts.md` | Portable question identity and authorized exploration |
| `AQSI-007-Question-Structural-Relay-and-Collective-Learning.md` | Relay operators, provenance, and collective learning |
| `AQSI-008-Strategic-Question-Control-Planes.md` | Human strategy, portfolio policies, and governance |
| `AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md` | Cross-domain typed alignment and transfer boundaries |
| `AQSI-010-MVP-Architecture-and-Recursive-Evolution.md` | Integration, MVP staging, and controlled adaptation |
| `SPEC-001-Canonical-Question-Unit-Contract.md` | QU identity, versioning, and lifecycle |
| `SPEC-002-Structural-Influence-and-Scoring-Contract.md` | Scoring provenance, uncertainty, and folding |
| `SPEC-003-Question-Relay-and-Exploration-Lifecycle.md` | Exploration state, relay records, and evidence handling |
| `SPEC-004-Control-Plane-and-Policy-Conformance.md` | Policy authority, resource limits, and conformance |

The example is a conceptual application of these specifications; it is not a conformance-certified implementation.

## 3. Scenario: A Human-Governed Research Program

A research sponsor funds a small interdisciplinary program on **reliable distributed sensing and its supporting software systems**. The program includes:

1. Near-term detection and diagnosis of intermittent sensor anomalies.
2. Reliability of CI pipelines and data-processing services.
3. Foundational causal and structural methods that might transfer across the two domains.
4. Replication, negative-result analysis, and preservation of unresolved questions.

The sponsor wants useful near-term outcomes but also wants to avoid starving foundational or exploratory research. Rather than writing every research question, the sponsor defines a **Strategic Question Control Plane**. AQSI proposes candidate questions and research portfolios within that policy.

### 3.1 Synthetic policy and budget

All quantities in this table are illustrative.

| Policy field | Synthetic value | Meaning |
|---|---:|---|
| Total cycle budget | 100 research credits | Abstract resource units, not currency |
| Near-term reliability | 40–60 credits | A portfolio allocation range |
| Foundational methods | 20–35 credits | Preserve basic research capacity |
| Cross-domain exploration | 10–25 credits | Support potentially valuable transfer |
| Independent replication | At least 10 credits | Preserve a verification allocation |
| Maximum single question | 30 credits | Avoid one-question concentration |
| Maximum agent concurrent tasks | 2 | Bound coordination and oversight |
| External write access | Prohibited by default | Requires separate human approval |
| Policy revision | Human approval required | Agents may recommend, not enact |

The allocation categories may overlap conceptually. A real implementation must define accounting rules so the same credit cannot be counted twice toward mandatory minima. The synthetic worked example below uses **exclusive primary budget categories** for accounting clarity.

### 3.2 Policy invariants

- A high-scoring question is not automatically approved for execution.
- A portfolio optimizer may not spend beyond its authorized budget.
- Research agents may not silently modify strategic priorities.
- Safety, privacy, data licensing, and access restrictions remain binding regardless of predicted research value.
- A deferred question retains provenance and may be revisited when evidence or policy changes.
- Rejected evidence is not deleted merely because it contradicts an agent's preferred hypothesis.

## 4. Multi-Agent Roles and Boundaries

The MVP proposes six *logical* roles. A role may be a separate model instance, a human, or a sequential procedure; the case does not require six simultaneously running models.

| Role | Main responsibility | Cannot do unilaterally |
|---|---|---|
| Discovery agent | Generate gap, residual, association, and relay questions | Authorize external execution |
| Structural analyst | Build UTN-typed factors, candidate mappings, and influence records | Assert unverified mappings as facts |
| Historical evaluator | Retrieve comparable cases and estimate value/uncertainty | Treat historical scores as ground truth |
| Portfolio planner | Propose a policy-constrained question set and allocation | Change strategic policy or budget |
| Explorer / experimenter | Conduct authorized analysis or experiments | Exceed scope or change production systems |
| Critic / relay curator | Seek counter-evidence, check provenance, create relay pieces | Rewrite original observations without trace |

**Independence is not guaranteed by role labels.** Agents sharing a model, context, or data source may make correlated errors. The validation plan therefore measures source independence and uses external checks where feasible.

## 5. Canonical Research Objects

The proposed system exchanges versioned, inspectable records rather than informal chat summaries alone.

### 5.1 Question Unit (QU)

A QU identifies a research question independently of any particular prompt. Minimum conceptual fields include:

- `question_id`, `version`, `utn_type`, `domain`, and `owner_scope`;
- `question_statement`, `testability`, `assumptions`, and `unknowns`;
- `structural_factors` with type, granularity, and provenance;
- `origin` and parent or sibling question references;
- references to assessments, evidence, counter-evidence, and relay records;
- current lifecycle state and authorization references.

### 5.2 Other objects

| Object | Purpose |
|---|---|
| Influence Record | Directed relation, factor support, confidence, and unknown status |
| Historical Assessment | Prior outcomes, applicability conditions, costs, and delayed relay value |
| Portfolio Proposal | Selected QUs, allocations, objective terms, policy version, and alternatives |
| Assignment Record | Agent role, task scope, resource ceiling, and handoff expectations |
| Exploration Contract | Authorized methods, data, stop conditions, evidence requirements |
| Evidence Record | Observation or assertion, method, source, timestamp, independence metadata |
| Relay Piece | Derived question, method, negative result, transferable structure, or explicit leftover |
| Policy Decision | Human-approved policy revision or authorization with audit trail |

Each object should have stable identity, version semantics, and an immutable or append-only audit history appropriate to its use.

## 6. Question Discovery and Candidate Pool

A hypothetical discovery cycle produces seven candidates. These are examples, not observations from a real program.

| ID | Candidate question (abridged) | Primary category | Origin |
|---|---|---|---|
| Q1 | Which timing factors explain intermittent sensor anomalies? | Near-term | Residual from anomaly triage |
| Q2 | Can CI flaky-test diagnostics transfer to sensor fault isolation? | Cross-domain | Structural association |
| Q3 | Which causal assumptions fail under missing sensor data? | Foundational | Counter-evidence gap |
| Q4 | Does a replication protocol distinguish drift from transient faults? | Replication | Historical uncertainty |
| Q5 | Can typed differential trees unify anomaly explanations? | Foundational | UTN / structure-first |
| Q6 | Which data-pipeline retries create hidden state interactions? | Near-term | Historical failure family |
| Q7 | Can a novel agent architecture self-optimize all research decisions? | Cross-domain | Speculative LLM proposal |

Q7 may be interesting, but its breadth, limited testability, and likely cost make it unsuitable for immediate high-confidence exploration. AQSI should be able to **defer** Q7 with a recorded rationale, not silently erase it.

### 6.1 Multi-granularity factors

For Q2, candidate factors include:

- Concept: intermittent observed failure.
- Attribute: frequency, timing sensitivity, environmental dependence.
- Method: controlled perturbation, log correlation, causal isolation.
- Evidence: historical CI failure traces, sensor event logs.
- Constraint: distinct physical causality and instrumentation.
- Transfer point: diagnostic *question form* rather than source-domain answer.
- Residual: unmodeled temporal coupling.

UTN alignment must explicitly distinguish type compatibility from mere lexical similarity. A mapping that preserves the question form but not the physical mechanism may still justify a testable question, but not a conclusion.

## 7. Historical Question Intelligence

The historical evaluator retrieves prior Question Units and outcomes under typed, documented similarity conditions. It may use a Question Differential Tree to distinguish shared question cores from domain-specific deltas.

A historical record should preserve:

1. What was asked and under which assumptions.
2. What exploration was actually performed.
3. What evidence supported or contradicted the answer.
4. How much effort was spent.
5. Which later questions or methods the work enabled.
6. Whether the result is transferable to the current context.

A previously unsuccessful question can still have high **relay value** if it ruled out a misleading method or exposed a transferable failure mode. Historical scoring should not convert sparse negative evidence into permanent exclusion.

### 7.1 Screening with uncertainty

Let `h_i` denote an estimated historical potential score and `u_i` its uncertainty. A conservative screen may defer high-cost candidates with low estimated value, but a novelty reserve must protect candidates for which the history is thin. Confidence intervals, missingness, and source quality should be carried into the selection decision.

**Unknown historical potential is not the same as zero potential.**

## 8. Directional Structural Influence and Portfolio Value

For candidate questions `q_i` and `q_j`, define an estimated directed influence:

$$
I(q_i \rightarrow q_j) = operatorname{Fold}_{a,b}\left(w_{ab}\,R(h_{ia},h_{jb})\right),
$$

where `h_ia` and `h_jb` are typed factors, `R` is a contract-governed relation estimator, and the fold operator must declare how it treats unknown relations, dependencies, and evidence confidence. This is a **design family**, not a uniquely validated formula.

A goal-open baseline is:

$$
S_{\mathrm{out}}(q_i)=\sum_{j\ne i}I(q_i\rightarrow q_j).
$$

The directional asymmetry matters: Q3 might inform Q1 more strongly than Q1 informs Q3. The raw sum is not necessarily a good portfolio objective, because it may reward correlated, redundant, or popular questions.

### 8.1 Illustrative pairwise influence

The table below is a synthetic partial matrix. `?` means **unknown**, not zero.

| Source → Target | Q1 | Q2 | Q3 | Q4 | Q5 | Q6 |
|---|---:|---:|---:|---:|---:|---:|
| Q1 | — | 0.3 | 0.2 | 0.5 | ? | 0.2 |
| Q2 | 0.6 | — | 0.4 | 0.2 | 0.5 | 0.4 |
| Q3 | 0.5 | 0.3 | — | 0.6 | 0.4 | ? |
| Q4 | 0.4 | 0.1 | 0.5 | — | 0.2 | 0.3 |
| Q5 | 0.3 | 0.5 | 0.5 | 0.3 | — | 0.2 |
| Q6 | 0.3 | 0.2 | ? | 0.3 | 0.2 | — |

These numbers are neither measured relationships nor calibrated probabilities. They demonstrate representation and bookkeeping only.

### 8.2 Portfolio formulation

Let `x_i` indicate whether question `i` is funded, `c_i` its estimated cost, `b` the authorized budget, and `p` the current human policy. One possible research objective is:

$$
\max_{x}\; \sum_i x_i V_i
+\lambda\sum_{i\ne j}x_i x_j C_{ij}
-\mu\sum_{i\ne j}x_i x_j D_{ij}
+\nu\,\mathrm{Coverage}(x),
$$

subject to:

$$
\sum_i c_i x_i \le b,\qquad x\in\mathcal{F}(p).
$$

Here `V_i` is a policy-compatible, evidence-aware estimate of question value; `C_ij` is a complementarity estimate; `D_ij` is a redundancy estimate; and `F(p)` is the policy-feasible set. These terms must be defined and calibrated before operational use. The objective must not double-count the same influence evidence in `V`, `C`, and `Coverage`.

Portfolio optimization is **not** permission to execute selected tasks. Execution requires separate contracts and authorization.

## 9. Worked Synthetic Portfolio

The sponsor has 100 research credits. The portfolio planner proposes the following allocations; the numbers are invented to illustrate policy accounting.

| Question | Credits | Primary category | Assigned roles | Intended deliverable |
|---|---:|---|---|---|
| Q1 | 25 | Near-term | Explorer + critic | Timing-factor hypothesis ledger |
| Q6 | 20 | Near-term | Explorer + historical evaluator | Retry-state diagnostic map |
| Q3 | 20 | Foundational | Structural analyst + critic | Causal-assumption inventory |
| Q5 | 10 | Foundational | Structural analyst | Typed explanation schema proposal |
| Q2 | 15 | Cross-domain | Discovery + analyst | Transfer mapping and falsifiers |
| Q4 | 10 | Replication | Explorer + independent reviewer | Replication protocol |
| **Total** | **100** | | | |

Category totals: near-term 45, foundational 30, cross-domain 15, replication 10. Each question is within the 30-credit cap. Q7 is deferred with an explicit revisit trigger (e.g., a narrower testable subquestion or new evidence).

This allocation is **one feasible synthetic portfolio**, not a demonstrated optimum. A real optimizer would present alternatives, sensitivity analyses, and the effect of uncertain scores and costs.

### 9.1 Decision rationale and alternatives

The planner should record why Q2 was funded despite uncertain transferability: it offers a bounded test of a structural hypothesis and may generate useful negative evidence. Q4 is funded to prevent the entire cycle from relying on unreplicated observations. Q3 and Q5 preserve foundational capacity even if near-term tasks have higher immediate expected utility.

An alternative portfolio might allocate more to Q1 and Q6 and less to cross-domain work. Such a choice is not inherently wrong; it should be evaluated against the human policy, uncertainty, and long-run evidence outcomes.

## 10. Assignment, Authorization, and Handoffs

A portfolio decision yields proposed assignments, not active tool permissions. Each exploration contract specifies:

- The QU version and policy version in force.
- Allowed datasets, tools, and environments.
- Prohibited actions and escalation conditions.
- Maximum cost, concurrency, and time horizon.
- Required observations, counter-evidence checks, and artifact formats.
- A stop condition and a process for handling unexpected findings.
- The human or authorized controller who approved the activity.

### 10.1 Example exploration contract (illustrative)

```yaml
contract_id: AQSI-EC-Q2-001
question_ref: AQSI-Q2@v1
policy_ref: AQSI-POLICY-001@v1
status: proposed
scope:
  activity: read_only_structural_comparison
  source_domain: ci_flaky_tests
  target_domain: sensor_anomalies
  permitted_inputs:
    - authorized_deidentified_ci_metadata
    - authorized_sensor_metadata
  prohibited_actions:
    - production_modification
    - external_data_publication
    - autonomous_policy_change
budget:
  research_credits: 15
  max_parallel_tasks: 2
required_outputs:
  - typed_alignment_map
  - non_transferable_assumptions
  - testable_target_questions
  - evidence_and_counterevidence_register
  - explicit_leftovers
stop_conditions:
  - budget_exhausted
  - authorization_revoked
  - prohibited_data_encountered
execution_authorized: false
```

The `execution_authorized: false` field is intentional: this is a *proposed* contract, not an approval token. A real system must use a verifiable authorization mechanism rather than trusting a self-reported Boolean.

## 11. Illustrative Multi-Agent Research Cycle

### Step 1 — Discover

The discovery agent proposes Q2 from the common structure of intermittent observed deviations. It also records the risk that CI and sensor failures have different causal mechanisms.

### Step 2 — Represent and challenge

The structural analyst creates a UTN-aligned mapping. The critic identifies missing target-domain assumptions: sampling irregularity, calibration drift, and physical environmental variation. The candidate question is revised to ask whether *the diagnostic sequence* transfers, not whether the same causes explain both phenomena.

### Step 3 — Retrieve history

The historical evaluator finds earlier failed attempts to infer causes from sparse logs. That negative history raises the priority of observability and counter-evidence requirements; it does not prohibit transfer.

### Step 4 — Select and authorize

The portfolio planner proposes Q2 with a bounded allocation. The authorized controller approves only read-only comparison. No agent may execute write operations merely because the question is selected.

### Step 5 — Explore

An explorer constructs a comparison protocol: identify candidate factors, list testable predictions, enumerate domain-specific exceptions, and propose what target-domain evidence would refute transfer.

### Step 6 — Independent critique

A critic asks whether the proposed analogy survives a target-domain negative control. If not, the record distinguishes a failed mapping from a failed question-generation method.

### Step 7 — Relay

The curator emits a versioned relay piece: a narrower question about distinguishing sensor synchronization errors from physical drift using controlled perturbations. The piece includes its source, assumptions, uncertainty, and required tests.

### Step 8 — Update history and portfolio

The HQI registry records the work performed, evidence status, and possible downstream value. The next cycle may revisit Q2, derive a narrower question, or reallocate credits. None of these steps establishes an actual scientific result in this illustrative case.

## 12. Question-to-Question and Cross-Agent Relay

A relay piece is not just a prose summary. It should preserve sufficient structure for another participant to inspect, challenge, or continue the work.

### 12.1 Relay types

| Relay type | Example | Verification concern |
|---|---|---|
| Derivation | Q2 → narrower synchronization question | Preserve derivation rationale |
| Split | Q1 → timing, calibration, and missing-data questions | Avoid losing original scope |
| Composition | Combine Q3 causal constraints with Q4 replication design | Check assumption compatibility |
| Transfer | CI diagnostic question → sensor investigation | Preserve domain-specific exceptions |
| Counter-evidence | Negative control contradicts a transfer hypothesis | Do not suppress unfavorable results |
| Revisit | Deferred Q7 becomes testable after decomposition | Retain original decision context |
| Repeated execution | Repeat Q4 under changed conditions | Do not count correlated runs as independent |
| Method relay | Transfer a validated comparison protocol | Separate method reuse from outcome verification |

### 12.2 Relay record example

```yaml
relay_id: AQSI-RELAY-Q2-001
source_question: AQSI-Q2@v1
operation: derive
target_question: AQSI-Q2A@v1
proposed_by_role: relay_curator
status: candidate
transferred_structure:
  - typed_diagnostic_sequence
  - controlled_perturbation_method
non_transferable_assumptions:
  - software_failure_causality_is_not_sensor_physics
supporting_evidence: []
counter_evidence: []
unknowns:
  - target_domain_test_performance
  - measurement_independence
explicit_leftovers:
  - test_with_real_authorized_sensor_data
  - compare_against_domain_expert_questions
```

An empty evidence list is not equivalent to evidence of absence. Relay acceptance is not scientific verification.

## 13. Collective Learning Without Forced Consensus

Collective learning requires more than agents agreeing with one another. The proposed registry should support:

1. **Shared access to typed question and evidence records**, subject to permissions.
2. **Independent annotations** rather than overwriting dissenting assessments.
3. **Provenance-preserving reuse** of methods and historical outcomes.
4. **Explicit uncertainty and counter-evidence** in every major relay.
5. **Credit assignment for delayed downstream utility**, without pretending it is easy to estimate.
6. **Conflict resolution procedures** for incompatible UTN mappings, score versions, or evidence interpretations.

A majority of agents is not a substitute for independent measurements. Correlated model outputs should not be treated as multiple independent confirmations.

## 14. Strategic Feedback Without Authority Drift

Exploration can reveal that the sponsor's original allocation is inefficient or that a new field merits attention. AQSI may produce a **policy recommendation** such as:

> Consider increasing the next cycle's replication allocation because several high-impact claims remain weakly corroborated.

Such a recommendation must include evidence, alternatives, expected tradeoffs, and the identity of the approving authority. It does **not** amend the policy until the appropriate human or institution authorizes the change.

The policy record should distinguish:

- `proposed_change`;
- `reviewed_change`;
- `approved_change`;
- `effective_policy_version`.

This distinction is especially important when the research system itself is being optimized: the system may suggest changes to its selection rules, but must not silently expand its own authority.

## 15. Portfolio Replanning and Explicit Leftovers

A research cycle ends with a portfolio review, not necessarily with all questions answered. A useful review reports:

- What was attempted and at what cost.
- Which hypotheses were supported, contradicted, or left unresolved.
- Which questions produced reusable methods or derived questions.
- Which assignments stalled and why.
- Which candidate questions were deferred and under what revisit triggers.
- Which structural mappings remain unverified.
- Whether the policy constraints were respected.

**Explicit Leftover** is a first-class research outcome. A leftover may be more valuable than a prematurely confident answer because it states precisely what remains unknown and what evidence could resolve it.

## 16. Threat Model and Failure Modes

### 16.1 Reward hacking and Goodhart effects

Agents may optimize for high question scores, number of generated questions, or volume of relay artifacts without improving knowledge. Evaluation must include externally assessed utility, evidence quality, and resource cost.

### 16.2 Portfolio monoculture

Influence centrality may overfund popular questions while neglecting unconventional but valuable ideas. Reserve exploration capacity, use uncertainty-aware selection, and audit domain coverage.

### 16.3 Collusion and correlated hallucinations

Multiple agents may repeat the same unsupported inference. Track common model lineage, shared prompts, shared data, and independent measurement status.

### 16.4 Evidence laundering through relay

An unverified conjecture can appear authoritative after several handoffs. Relay records must preserve evidence status and provenance; confidence must not automatically rise with relay depth.

### 16.5 Strategic authority drift

An agent may treat a recommendation as permission. Enforce policy versions and independent authorization checks at the action boundary.

### 16.6 Historical lock-in

Historical scores may systematically suppress new methods or unfamiliar fields. Evaluate cold-start performance, maintain exploration reserves, and allow explicit appeals and revisit triggers.

### 16.7 Resource-accounting failure

Overlapping categories, retries, and delegated subagents can hide actual expenditure. Use unique cost events, attributable budgets, and hard stop controls.

### 16.8 Cross-domain semantic drift

UTN labels may align while causal semantics diverge. Require mapping assumptions, counterexamples, and target-domain tests.

### 16.9 Premature recursive modification

The system may suggest updating its own scorer or policy machinery based on noisy feedback. Changes should be sandboxed, versioned, compared with baselines, and separately authorized.

## 17. Proposed MVP Architecture

The MVP can be implemented as a small, inspectable workflow rather than a fully autonomous agent swarm.

```text
Human Research Sponsor
        |
        v
Strategic Policy Registry (versioned, authorized)
        |
        v
Question Discovery --> Canonical QU Registry <-- Historical Question Registry
        |                    |
        v                    v
UTN / Structural Alignment --> Influence & Historical Assessment
                                  |
                                  v
                        Portfolio Proposal + Audit
                                  |
                                  v
                        Human Authorization Gate
                                  |
                                  v
                      Bounded Agent Assignments
                                  |
                                  v
                       Evidence / Counter-Evidence
                                  |
                                  v
                         Structural Relay Registry
                                  |
                      +-----------+-----------+
                      |                       |
                      v                       v
              New / Revised QUs        Historical Feedback
                      |                       |
                      +-----------+-----------+
                                  |
                                  v
                          Next Research Cycle
```

### 17.1 Minimal components

- Question and policy registries with stable IDs.
- A small discovery generator and structural annotator.
- A replaceable historical and influence scorer.
- A simple constrained portfolio selector.
- A separate authorization service or human review step.
- One or two bounded exploration roles plus independent critique.
- Evidence and relay registries with immutable provenance.
- A reproducible evaluation harness.

The MVP should not require unrestricted network access, autonomous code deployment, or opaque changes to the research policy.

## 18. Conformance Checklist

A proposed implementation should be tested against the following requirements before claiming AQSI case conformance.

| ID | Requirement | Suggested check |
|---|---|---|
| C-01 | Every question has stable identity and version | Duplicate/version test |
| C-02 | UTN type and granularity are explicit | Schema validation |
| C-03 | Directed influences preserve direction | Asymmetry test |
| C-04 | Unknown relationships remain distinguishable from zero | Missingness test |
| C-05 | Historical scores cite applicable evidence | Provenance audit |
| C-06 | Candidate screening preserves deferred questions | Revisit test |
| C-07 | Portfolio respects hard budget | Over-budget rejection |
| C-08 | Category accounting avoids double counting | Allocation reconciliation |
| C-09 | Policy version is recorded for every decision | Version trace |
| C-10 | Selection does not confer action authorization | Unauthorized-action test |
| C-11 | Agent assignments carry explicit scope and limits | Contract inspection |
| C-12 | Counter-evidence is preserved | Contradiction-retention test |
| C-13 | Relay preserves source identity and assumptions | Lineage reconstruction |
| C-14 | Relay acceptance does not imply verification | Evidence-status test |
| C-15 | Repeated execution records dependence | Replication audit |
| C-16 | Agent agreement is not counted as independent evidence | Correlation test |
| C-17 | Policy change requires authorized approval | Authority-escalation test |
| C-18 | Costs of delegated work are attributable | Cost-ledger test |
| C-19 | Explicit leftovers are retrievable | Registry query |
| C-20 | Scorer or agent revisions are versioned and reversible | Rollback test |

Passing these checks would establish only **specified workflow conformance**, not improved research performance.

## 19. Evaluation Design and Baselines

### 19.1 Baseline systems

| Baseline | Description | Isolates |
|---|---|---|
| B0 Fixed-task single LLM | Human supplies questions; one LLM answers | Autonomous discovery benefit |
| B1 Single-agent AQSI-lite | Autonomous questions without multi-agent relay | Multi-agent contribution |
| B2 Unstructured multi-agent discussion | Several agents collaborate in prose only | Structured contracts and relay |
| B3 Rank-only selection | Select top-scoring questions individually | Portfolio complementarity |
| B4 No historical intelligence | Same system without HQI retrieval | Historical learning contribution |
| B5 No structural influence | Lexical or embedding similarity only | Multi-granularity influence contribution |
| B6 No UTN alignment | Cross-domain matching without typed contracts | Semantic alignment contribution |
| B7 No strategic portfolio control | Agent-driven allocation without sponsor policy | Governance and allocation effects |
| B8 No independent critic | Explorer self-evaluates its results | Counter-evidence and bias effects |

Where a baseline would be unsafe or unauthorized (notably B7), compare in an offline simulator or replay environment rather than granting real-world unrestricted authority.

### 19.2 Outcome measures

**Research value:** blinded expert ratings of question testability, nonredundancy, relevance, and potential utility; independently verified discoveries where available.

**Evidence quality:** fraction of claims with traceable sources, counter-evidence coverage, replication outcomes, and correction rate.

**Portfolio quality:** budget adherence, domain coverage, diversity, redundancy, cost-adjusted utility, and regret against an offline reference allocation when definable.

**Relay quality:** fraction of relay pieces reused appropriately, provenance completeness, semantic drift, and delayed value of descendants.

**Governance:** unauthorized-action attempts blocked, policy-version correctness, audit completeness, and approval latency.

**Efficiency:** agent calls, tokens, compute, human review time, experiment costs, and wall-clock time.

### 19.3 Experimental controls

- Match total resource budgets and accessible evidence across systems.
- Pre-register evaluation criteria and stop rules.
- Separate training/history data from held-out test scenarios.
- Use blinded domain experts where possible.
- Report inter-rater disagreement and uncertainty.
- Avoid crediting downstream value before sufficient follow-up time.
- Report failures, negative outcomes, and policy violations alongside positive results.

## 20. Testable Hypotheses

The following are research hypotheses, not findings.

**H1 — Portfolio benefit.** Under equal budgets, policy-constrained portfolio selection yields higher blinded expert-rated research utility than selecting individual top-ranked questions.

**H2 — Relay benefit.** Structured cross-agent relay increases independently reusable research artifacts relative to unstructured multi-agent chat.

**H3 — Historical benefit.** HQI reduces repeated low-value investigations without significantly reducing the discovery of useful novel questions.

**H4 — Multi-granularity benefit.** Typed structural influence produces more useful complementary question sets than lexical similarity alone.

**H5 — Governance benefit.** A separate authorization gate reduces policy violations without unacceptable loss of research throughput.

**H6 — Critique benefit.** Independent counter-evidence review lowers unsupported-claim rates compared with self-review.

**H7 — Cross-domain benefit.** UTN-aligned transfer yields more testable cross-domain questions than untyped analogy under matched budgets.

**H8 — Exploration reserve.** A bounded novelty allocation improves long-run discovery diversity without disproportionate loss of near-term value.

**H9 — Provenance benefit.** Versioned relay records reduce semantic drift and evidence laundering compared with prose-only handoffs.

**H10 — Adaptive portfolio benefit.** Replanning from verified feedback improves subsequent allocations over a fixed policy-compatible portfolio, controlling for additional compute and review cost.

Each hypothesis can fail. Negative results should be retained as evidence for narrowing or revising the proposed architecture.

## 21. Staged Validation Roadmap

### Stage M0 — Static portfolio replay

Use synthetic and retrospectively labeled question sets. Validate schemas, policy feasibility, cost accounting, unknown handling, and reproducibility. No autonomous external actions.

**Exit criterion:** all critical conformance checks pass and the portfolio decision can be reconstructed from stored records.

### Stage M1 — Bounded single-domain research cycle

Use authorized CI or sensing datasets. Compare fixed-task, single-agent, and structured question-selection variants. Include a human review gate.

**Exit criterion:** demonstrate end-to-end provenance and obtain independently assessed outcome measures, whether positive or negative.

### Stage M2 — Cross-domain and multi-agent relay

Introduce typed transfer, independent critique, and versioned relay pieces. Measure artifact reuse, semantic drift, and total resource cost.

**Exit criterion:** reproducible cross-agent handoffs and interpretable comparisons against B2/B6/B8.

### Stage M3 — Policy-constrained adaptive research portfolio

Permit the system to propose scorer, allocation, and workflow changes inside a sandbox. Require approval, holdout evaluation, rollback, and no authority expansion.

**Exit criterion:** demonstrate controlled adaptation and transparent failure handling, not merely increased activity or self-reported scores.

## 22. Open Questions

1. How should research value be estimated when the most important discoveries arrive years later?
2. How can portfolio selection preserve genuine novelty without wasting most of its budget?
3. What evidence is needed to calibrate directional influence between heterogeneous question factors?
4. How should an organization allocate credit for a question that enables several later discoveries?
5. How can agent diversity be measured when agents share model families and training data?
6. When does additional agent coordination cost more than the value of relay?
7. Which policy parameters should be adjustable automatically, and which must remain human-controlled?
8. How should UTN evolve when a newly discovered relation does not fit existing types?
9. How can cross-domain transfer be tested without conflating a useful question with a correct answer?
10. What constitutes a valid counterfactual for portfolio regret in open-ended research?
11. How should uncertainty and unknown influence entries affect optimization under tight budgets?
12. Which negative results deserve long-term preservation and future revisit?

## 23. Conclusion

This case proposes an auditable research architecture in which humans govern strategic priorities and action boundaries, while AQSI autonomously proposes specific questions, estimates structural and historical value, constructs portfolios, and coordinates bounded multi-agent exploration. The key unit of progress is not an agent's persuasive answer but a traceable sequence of **questions, evidence, counter-evidence, reusable methods, relay pieces, and explicit leftovers**.

The proposal offers a concrete test bed for asking whether strategic control, multi-granularity scoring, historical intelligence, and structural relay jointly improve collective research. Its benefits remain to be established through controlled experiments. In particular, more agents, more questions, and more relay traffic should not be confused with better science.

---

## Appendix A — Illustrative Portfolio Decision Record

```yaml
portfolio_id: AQSI-PORT-001
policy_ref: AQSI-POLICY-001@v1
status: proposed
budget_total: 100
budget_unit: research_credit
allocations:
  - {question: Q1, category: near_term, credits: 25}
  - {question: Q6, category: near_term, credits: 20}
  - {question: Q3, category: foundational, credits: 20}
  - {question: Q5, category: foundational, credits: 10}
  - {question: Q2, category: cross_domain, credits: 15}
  - {question: Q4, category: replication, credits: 10}
deferred:
  - question: Q7
    reason: insufficiently_bounded_and_testable
    revisit_trigger: narrower_question_or_new_evidence
accounting:
  near_term: 45
  foundational: 30
  cross_domain: 15
  replication: 10
  total: 100
selection_is_execution_authorization: false
notes:
  - synthetic_example_not_an_empirical_result
```

## Appendix B — Minimal Cycle Pseudocode

```text
INPUT: authorized_policy P, candidate_sources D, historical_registry H

assert verify_policy_signature(P)
Q := discover_questions(D, H)
Q := assign_canonical_ids_and_utn_types(Q)
F := extract_typed_multigranularity_factors(Q)
I := estimate_directed_influence(F, with_unknowns=true)
A := estimate_historical_potential(Q, H, with_uncertainty=true)

proposals := optimize_portfolios(Q, I, A, constraints=P)
record_proposals_and_alternatives(proposals)

approved := request_authorized_selection(proposals)
FOR each selected question in approved:
    contract := draft_exploration_contract(question, P)
    IF independently_authorized(contract):
        results := execute_within_contract(contract)
        evidence := validate_and_register_evidence(results)
        relay := create_versioned_relay_pieces(question, evidence)
        register_history_and_leftovers(question, evidence, relay)
    ELSE:
        record_not_executed(question, reason="not_authorized")

propose_next_cycle_updates_without_enacting_policy_changes()
OUTPUT: audit_log, evidence_registry, relay_registry, deferred_questions
```

## Appendix C — Interpretation Rules

- A synthetic score is not a calibrated probability.
- A policy-feasible allocation is not necessarily an optimal allocation.
- A selected question is not an authorized action.
- A relay piece is not automatically validated knowledge.
- Agreement between agents is not independent corroboration.
- Historical failure is not permanent proof of low research value.
- Repeated execution is a relay opportunity, not automatically independent evidence.
- A research system that changes its own scorer has not thereby demonstrated recursive self-improvement.

## Appendix D — Suggested Repository Placement

- Path: `cases/CASE-003-Research-Portfolio-and-Multi-Agent-Relay.md`
- Companion figure: `figures/Fig-007-Strategic-Question-Control-Plane.png`
- Additional architectural figure: `figures/Fig-006-Question-Unit-and-Structural-Relay.png`
- Companion specifications: `specs/SPEC-001-Canonical-Question-Unit-Contract.md` through `specs/SPEC-004-Control-Plane-and-Policy-Conformance.md`

**Research stance:** Theory-first, contract-first, falsifiable, evidence-aware, human-governed, and collective-learning friendly.
