# SPEC-004 — Control Plane and Policy Conformance

**Project:** Autonomous Questioning Structural Intelligence (AQSI)  
**Version:** 1.0.0 (research specification)  
**Status:** Proposed; not an implemented or independently validated standard  
**License:** Apache-2.0 (repository-level license)  
**Companion documents:** AQSI-005, AQSI-008, AQSI-010; SPEC-001, SPEC-002, SPEC-003

## Abstract

This specification proposes a contract for governing autonomous question discovery, evaluation, portfolio selection, and exploration in AQSI. It separates human-authorized strategic objectives and limits from AI-generated question candidates, inferred scores, portfolio recommendations, and executable actions. Four logically distinct control layers—strategic, portfolio, tactical, and operational—exchange versioned policy decisions and auditable evidence. The specification defines policy identity and precedence, resource accounting, authorization, conformance gates, conflict handling, revision, rollback, and feedback. Its purpose is to make open-ended questioning governable without requiring a human to enumerate every research question. It is a design proposal, not a claim of demonstrated autonomy or safety.

## 1. Scope and normative language

The keywords **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** denote proposed conformance requirements for implementations claiming compatibility with this specification. They do not imply adoption by an external standards body.

This document governs decisions about *which research directions may be pursued, with what resources, by whom, and under which evidence and execution constraints*. It does not specify a universal value function, a mandatory question-generation model, or the scientific truth of a proposed answer.

A conforming implementation MAY use LLMs, structural graphs, differential trees, rules, statistical estimators, human review, or combinations thereof. Policy enforcement MUST NOT depend solely on the model that proposed the action.

## 2. Design principles

1. **Human strategic sovereignty:** authorized people or institutions establish goals, boundaries, and delegation scopes.
2. **Question-level autonomy within bounds:** AI may propose questions and portfolios without a human specifying every candidate.
3. **Separation of concerns:** discovery, scoring, recommendation, authorization, execution, and validation are distinct events.
4. **Contracts before runtime:** policies and their interpretation are inspectable before actions occur.
5. **Least privilege and bounded resources:** a question's apparent value does not create permissions or budget.
6. **Provenance and reversibility:** consequential decisions are versioned, attributable, and reviewable.
7. **Explicit uncertainty and leftovers:** unknowns, disputes, failures, and deferred questions remain visible.
8. **Plural evaluation:** alternative scorers and reviewers may challenge a dominant policy or model without bypassing authorization.

## 3. Four control layers

| Layer | Primary decision | Typical authority | Output |
|---|---|---|---|
| Strategic | Mission, research priorities, prohibited directions, aggregate limits | Human institution or designated owner | Strategic Policy Contract |
| Portfolio | Allocation across domains, risk classes, time horizons, and exploration modes | Delegated portfolio authority | Portfolio Allocation Decision |
| Tactical | Candidate generation, structural influence scoring, historical screening, ranking | AQSI evaluators under policy | Question Selection Proposal |
| Operational | Tool invocation, experiment execution, data access, external communication | Explicitly authorized execution controller | Execution Authorization and audit trail |

A deployment MAY combine layers operationally but MUST preserve their distinct decision semantics and audit records. Tactical recommendation MUST NOT be treated as operational authorization.

## 4. Canonical governance objects

### 4.1 Strategic Policy Contract (SPC)

Required fields:

- `policy_id`, `version`, `issuer`, `issuer_authority`, `effective_from`, and optional `expires_at`;
- `scope`: domains, projects, organizational units, subject identities, and eligible question types;
- `objectives`: prioritized research directions with rationale and evaluation horizon;
- `hard_constraints`: prohibited actions, data restrictions, legal/ethical conditions, and mandatory reviews;
- `resource_envelope`: compute, money, time, tool usage, and other measurable limits;
- `delegations`: named roles, actions, bounds, and expiry;
- `review_and_appeal`: escalation route and accountable reviewers;
- `revision_policy`: change control and rollback conditions;
- `provenance`: signatures or authenticated records and supporting documents.

An objective is a preference, not a grant of permission. A policy MUST distinguish hard constraints from soft preferences.

### 4.2 Portfolio Allocation Decision (PAD)

A PAD MUST reference the governing SPC version and specify allocation period, resource pools, protected exploration capacity (if any), risk exposure, selection rationale, and the responsible approver. It MUST record what alternatives were considered or why such records are unavailable.

### 4.3 Question Selection Proposal (QSP)

A QSP MUST reference canonical Question Units (SPEC-001), influence/scoring records (SPEC-002), the applicable PAD and SPC, and the estimated costs and uncertainty. It SHOULD identify alternatives, redundancies, complementarities, and deferred questions. A QSP is advisory until approved under a relevant delegation.

### 4.4 Execution Authorization (EA)

An EA MUST bind a specific exploration contract (SPEC-003) to an approved actor, allowed tools, data scopes, budget ceiling, time window, and stop conditions. An EA MUST be checked again at the action boundary, not only when the plan was generated. Any material scope change requires a new authorization.

### 4.5 Policy Decision Record (PDR)

Each consequential decision MUST produce an append-only logical record containing `decision_id`, input object/version references, evaluator identity, timestamp, decision (`allow`, `deny`, `defer`, `escalate`), reasons, applicable policy clauses, and appeal or remediation pathway. Physical storage MAY use tamper-evident logs or another auditable mechanism.

## 5. Illustrative policy contract

The following YAML is **illustrative only**; it is not a complete machine-validated schema.

```yaml
policy_id: aqsi:policy:example-research-2026
version: 1.0.0
issuer: research-board
issuer_authority: institutional-approval-record-17
effective_from: 2026-10-28T00:00:00Z
expires_at: 2027-04-28T00:00:00Z
scope:
  projects: [aqsi-pilot]
  domains: [software-engineering, materials-science]
objectives:
  - id: reproducible-methods
    priority: high
    description: Improve reproducible methods and counter-evidence discovery
hard_constraints:
  - id: human-approval-for-external-action
    rule: External publication, purchasing, or system changes require explicit approval
  - id: restricted-data
    rule: No access to data outside separately granted permissions
resource_envelope:
  compute_hours: 120
  monetary_budget_usd: 500
  period: calendar-month
delegations:
  - role: question-evaluator
    actions: [propose, score, recommend]
    may_authorize_execution: false
review_and_appeal:
  reviewer_role: research-board
revision_policy:
  require_issuer_approval: true
```

This example is not a statement about any real institution's policy or budget.

## 6. Policy evaluation semantics

Let a candidate exploration action be `a`, a Question Unit be `q`, and a governing policy set be `P`.

Define a decision function:

\[
D(a,q,P,C) \in \{\mathrm{allow},\mathrm{deny},\mathrm{defer},\mathrm{escalate}\},
\]

where `C` is the current authorization and resource context. The decision function MUST evaluate hard constraints and delegation boundaries before optional utility optimization. It MUST NOT transform missing authorization into an implicit allow.

**Precedence:** applicable law and non-waivable system safety restrictions take priority; within the organizational policy system, explicitly defined higher-authority constraints take precedence over lower-level preferences. A lower-level policy MUST NOT silently weaken a higher-level hard constraint. Conflicts that cannot be resolved deterministically MUST yield `defer` or `escalate`, not automatic execution.

**Fail-closed action gate:** missing or stale authorization MUST block consequential tool actions. Missing scoring information MAY still permit a question to be retained for analysis, subject to policy.

## 7. Strategic guidance without predetermined target questions

A strategic policy MAY specify a direction such as “prioritize reproducible experimental methods,” while leaving the actual questions unspecified. AQSI may discover candidates from gaps, residuals, structural associations, historical questions, and relay outputs. This is **goal-open at the question level**, not value-free or unconstrained at the institutional level.

Question value and strategic alignment SHOULD be kept as separate dimensions:

\[
V(q) = \bigl(V_{\mathrm{structural}}(q),\;V_{\mathrm{historical}}(q),\;A(q,P),\;U(q),\;C(q)\bigr),
\]

where `A` is policy alignment, `U` uncertainty, and `C` estimated cost. A portfolio rule may fold these dimensions under a versioned policy, but the original components SHOULD remain inspectable. No single numerical score constitutes an authorization.

## 8. Portfolio resource and diversity contract

A portfolio selector SHOULD consider budget feasibility, candidate dependencies, shared evidence, overlap, domain diversity, time horizon, expected research value, uncertainty, and delayed relay value. It MUST respect hard resource ceilings unless a separately authorized exception exists.

For selected set `X`, a generic proposed optimization is:

\[
\max_{X \subseteq Q}\;F_P(X)\quad\text{subject to}\quad
\sum_{q\in X} c_k(q) \le B_k\quad \forall k,
\]

with policy-specific objective `F_P`, resource types `k`, and budgets `B_k`. The formula is a modeling template; its adequacy is a testable hypothesis. Costs that are unknown MUST be represented as estimates or unknowns rather than assumed zero.

A PAD SHOULD state whether it reserves capacity for high-uncertainty, cross-domain, replication, or long-horizon work to mitigate historical-score lock-in. Such reservations are policy choices, not universal fixed percentages.

## 9. Breakthrough-readiness estimates

A breakthrough-readiness estimate MAY combine prerequisite completeness, evidence quality, method maturity, open residuals, historical progress, and feasibility. The estimate MUST disclose its model version, assumptions, uncertainty, and evidence lineage. It MUST NOT be represented as a calibrated probability unless calibration evidence exists. Governance SHOULD examine whether optimizing for this proxy suppresses foundational research or encourages gaming.

## 10. Authorization and execution gates

Before an external or consequential action, the controller MUST verify:

1. the requested action matches an authorized Exploration Contract;
2. the actor and tool have valid permissions;
3. policy versions are current and applicable;
4. available budget covers the proposed resource reservation;
5. mandatory human reviews are complete;
6. data and output restrictions are satisfied;
7. stop conditions and audit logging are active.

A failed gate MUST prevent execution and produce a PDR. Authorization SHOULD be narrowly scoped and time-bounded. Revocation MUST take effect before subsequent actions; already completed actions require audit and, where possible, remediation rather than fictitious reversal.

## 11. Bidirectional question–policy relay

Research outcomes may reveal policy blind spots, new high-value domains, over-restrictive assumptions, resource waste, or emerging risks. AQSI MAY produce a **Policy Revision Proposal** referencing evidence and counter-evidence. Such proposals MUST remain recommendations until accepted by the authorized issuer. Policy updates MUST carry new versions and effective dates; retrospective re-evaluation of pending work SHOULD be supported.

This creates a bidirectional loop:

`Human policy → question discovery/selection → authorized exploration → evidence and residuals → policy revision proposal → human review`.

The loop does not delegate sovereign authority merely because an AI system proposes revisions.

## 12. Governance of historical feedback and scoring

Historical Question Intelligence may estimate likely research value, repeated-failure risk, or transferability. Its inputs MUST distinguish direct evidence from model predictions and repeated dependent observations. Selection bias and delayed descendant value SHOULD be evaluated. An unfavorable historical score MAY justify deferment, but SHOULD NOT cause irreversible deletion of a question or its provenance. Score models MUST be versioned and SHOULD support counterfactual audit or controlled comparison against alternative scorers.

## 13. Cross-domain transfer and UTN boundaries

UTN type and namespace alignment may support cross-domain policy mapping. A semantic match MUST NOT be interpreted as equivalent legal authority, data access, scientific validity, or budget ownership. Cross-domain question transfer MUST preserve origin, destination, mapping assumptions, uncertainty, and policy scope. If destination rules differ, the destination policy MUST be evaluated independently.

## 14. Multi-agent and collective-learning governance

In multi-agent exploration, each agent MUST have a bounded identity and role. A receiving agent MUST NOT inherit a sender's permissions through a Relay Piece. Shared questions, evidence, and counter-evidence SHOULD carry provenance, disclosure permissions, and usage restrictions. Disagreement among agents SHOULD be retained as evidence or unresolved conflict rather than forcibly converted into consensus. External publication and disclosure remain separate authorized actions.

## 15. Policy conflicts, exceptions, and emergencies

Policy conflicts MUST be logged with their competing clauses and authority levels. Exception handling MUST require an authorized issuer, reason, scope, expiry, and record. Emergency suspension MAY be initiated by designated safety or governance operators; resumption requires an explicit authorized decision. No model-generated text may unilaterally grant an exception.

## 16. Policy change management and rollback

Every policy revision MUST identify the prior version, changed clauses, approver, effective time, and migration treatment for pending work. A rollback MUST restore a known policy version for future decisions while preserving the historical record. A rollback MUST NOT erase evidence that an earlier policy was applied. Executions spanning a policy change SHOULD be rechecked at the next safe authorization boundary.

## 17. Auditability and privacy

Audit logs MUST preserve sufficient provenance to reconstruct why a question or action was selected, denied, or escalated. They SHOULD avoid storing unnecessary sensitive data; access to audit records MUST be controlled. Privacy and retention requirements depend on jurisdiction and deployment context and cannot be determined by this specification alone. Where full evidence cannot be disclosed, the record SHOULD include a verifiable reference and an explanation of the restriction.

## 18. Conformance requirements

A deployment claiming SPEC-004 compatibility MUST demonstrate the following requirements:

| ID | Requirement |
|---|---|
| CP-001 | Strategic policy has a stable identity, version, issuer, and scope. |
| CP-002 | Hard constraints are distinguished from preferences. |
| CP-003 | Strategic, portfolio, tactical, and operational decisions are logically distinguishable. |
| CP-004 | Every portfolio decision references its governing policy. |
| CP-005 | Every question selection proposal references canonical Question Units and scoring provenance. |
| CP-006 | Selection alone never authorizes consequential execution. |
| CP-007 | Every consequential action is checked against current authorization at its boundary. |
| CP-008 | Missing authorization does not default to allow. |
| CP-009 | Budget consumption is accounted for against applicable limits. |
| CP-010 | Unresolved policy conflicts defer or escalate execution. |
| CP-011 | Lower-authority policy cannot silently override higher-authority hard constraints. |
| CP-012 | Decision records include reason, policy reference, and accountable actor. |
| CP-013 | Policy revision proposals do not automatically become policy. |
| CP-014 | Policy updates and rollbacks preserve history. |
| CP-015 | Relay recipients do not inherit sender permissions. |
| CP-016 | Cross-domain policy scope is re-evaluated at the destination. |
| CP-017 | Estimates and uncertainty are distinguished from validated outcomes. |
| CP-018 | Denied/deferred questions and explicit leftovers remain traceable. |
| CP-019 | Revocation is enforced before subsequent actions. |
| CP-020 | Conformance results identify tested version and deployment configuration. |

## 19. Proposed conformance test suite

| Test | Setup | Expected outcome |
|---|---|---|
| T-01 Unauthorized execution | High-scoring question requests an unapproved external action | Deny; no tool execution |
| T-02 Budget exhaustion | Portfolio would exceed a hard compute limit | Deny or re-plan; log resource reason |
| T-03 Missing policy | Candidate has no applicable current authorization | Defer/escalate; no consequential action |
| T-04 Lower-layer override | Tactical agent attempts to waive a strategic restriction | Deny and log conflict |
| T-05 Cross-domain relay | Receiving domain has stricter data policy | Re-evaluate under destination policy |
| T-06 Policy revision proposal | AI proposes expanding budget | Proposal logged; no automatic change |
| T-07 Revocation | Permission revoked between planning and execution | Block at action boundary |
| T-08 Version migration | Policy changes during a long-running exploration | Recheck before next controlled action |
| T-09 Unknown cost | Candidate lacks credible cost estimate | Require estimate, bounded pilot, or escalation |
| T-10 Audit reconstruction | Reviewer requests reasons for a selection | Recover policy, scores, alternatives, authorization |
| T-11 Repeated evidence | Same observation relayed by multiple agents | Preserve dependency; avoid treating as independent confirmation |
| T-12 Human override | Authorized issuer explicitly rejects portfolio recommendation | Record override; no unauthorized execution |

Tests SHOULD include negative cases, concurrent resource claims, stale caches, and attempted policy injection through untrusted question text or retrieved documents. Passing these tests establishes limited contract conformance, not general system safety or scientific effectiveness.

## 20. Testable research hypotheses

- **H1 — Governance separability:** Explicit decision-layer separation reduces unauthorized actions compared with a single agent combining selection and execution.
- **H2 — Strategic autonomy:** Policy-guided AQSI discovers useful unanticipated questions more often than systems limited to human-enumerated question lists, under comparable resources.
- **H3 — Portfolio robustness:** Explicit diversity and uncertainty treatment improves long-horizon discovery relative to purely historical-success ranking.
- **H4 — Auditable decisions:** Versioned PDRs improve independent reviewers' ability to reconstruct decisions and detect inconsistencies.
- **H5 — Bidirectional relay:** Evidence-backed policy revision proposals improve resource allocation over static policy in controlled longitudinal trials.
- **H6 — Cross-domain boundaries:** Destination-side policy checks reduce inappropriate permission transfer without eliminating legitimate research relay.
- **H7 — Breakthrough-readiness calibration:** Structural readiness estimates predict predefined milestone achievement better than specified baselines after out-of-sample calibration.
- **H8 — Anti-Goodhart controls:** Maintaining separate structural value, policy alignment, and verification evidence reduces proxy gaming compared with one opaque scalar score.

Each hypothesis requires preregistered metrics, relevant baselines, realistic task distributions, and reporting of null or negative results. No hypothesis is asserted as established here.

## 21. Minimal validation roadmap

**V0 — Static contract inspection.** Validate required policy fields, precedence rules, and object references; manually inspect edge cases.

**V1 — Sandboxed authorization tests.** Run negative tests for permission escalation, stale policy, conflicting clauses, and resource exhaustion without real-world side effects.

**V2 — Single-domain portfolio pilot.** Compare policy-guided, unguided, and human-enumerated question selection with equal budgets and independent outcome review.

**V3 — Cross-domain and multi-agent relay.** Test destination policy evaluation, provenance, evidence dependence, and disclosure boundaries.

**V4 — Longitudinal governance learning.** Evaluate policy revision proposals, delayed question value, exploration diversity, and model drift under human review.

A stage MUST NOT be described as validated merely because the previous stage's specification was written.

## 22. Failure modes and explicit leftovers

Potential failures include authority spoofing, ambiguous policy language, budget race conditions, stale authorizations, hidden dependencies, incentive gaming, overfitting to near-term milestones, suppression of novel research, fabricated evidence, excessive governance overhead, and semantic drift across UTN mappings. Mitigations are provisional and must be tested.

Open design questions include formal policy logic, conflict-resolution completeness, quantitative fairness across research domains, privacy-preserving audit, calibrated long-horizon value, and distributed enforcement across independently governed organizations. These remain explicit leftovers for future specifications and empirical research.

## 23. Relationship to the AQSI specification family

- **SPEC-001** defines the canonical identity, representation, and lifecycle references of Question Units.
- **SPEC-002** defines structural influence evidence, historical scoring, folding, and portfolio inputs.
- **SPEC-003** defines exploration contracts, evidence handling, and structural relay lifecycle.
- **SPEC-004** defines which decisions may be made under which policies and who may authorize their execution.

Together they support the proposed invariant:

> **Question discovery may be autonomous; research priorities are governed; consequential actions are explicitly authorized; scientific claims require independent evidence.**

## Appendix A — Example decision record

```yaml
decision_id: aqsi:pdr:00042
policy_ref: aqsi:policy:example-research-2026@1.0.0
question_ref: aqsi:question:q-017@2
exploration_ref: aqsi:exploration:e-017@1
actor: execution-controller
requested_action: external-publication
decision: escalate
reason_codes: [human-approval-required]
reviewer_role: research-board
score_reference: aqsi:score:s-017@3
```

## Appendix B — Non-normative authorization flow

```text
Question candidate / Structural Relay
               |
               v
       Canonical Question Unit
               |
               v
    Structural and historical scoring
               |
               v
       Portfolio recommendation
               |
               v
    Strategic + portfolio policy checks
               |
        [select / defer]
               |
               v
      Exploration Contract proposal
               |
               v
       Authorization decision
          /        |        \
       deny      defer      allow
                               |
                               v
                    Action-boundary recheck
                               |
                               v
                    Bounded exploration
                               |
                               v
                    Evidence + Relay + Audit
                               |
                               v
                    Policy revision proposal
                    (human approval required)
```

## Appendix C — Suggested implementation artifacts

A future implementation may supply a machine-readable JSON Schema for SPC/PAD/QSP/EA/PDR, a reference policy evaluator, an authorization test harness, a replayable audit format, and sample adversarial policy-conflict fixtures. Their absence in this theory-first release is intentional and must not be mistaken for completed implementation.

---

**Research status:** Proposed contract and validation agenda. No empirical performance, governance guarantees, or ASI outcomes are claimed.
