# SPEC-003 — Question Relay and Exploration Lifecycle

**Project:** Autonomous Questioning Structural Intelligence (AQSI)  
**Version:** 1.0.0 (research specification)  
**Status:** Proposed; not an implemented, certified, or empirically validated standard  
**Scope:** Auditable question exploration, evidence and counterevidence capture, structural relay, multi-agent interoperability, and feedback into Historical Question Intelligence (HQI).

## Abstract

This specification proposes an interoperable lifecycle contract for autonomous research questions. It connects the Canonical Question Unit (SPEC-001) and structural influence/portfolio decisions (SPEC-002) to authorized exploration, evidence-preserving outcomes, question-to-question relay, cross-domain transfer, repeated-execution learning, and subsequent reassessment. Its principal invariant is that a research exploration must not be reduced to a generated answer: outcomes include negative findings, contradictory evidence, methodological limitations, unresolved residuals, new questions, and reproducibility records. Relay acceptance certifies contract admissibility, **not scientific truth**. The specification is deliberately independent of a particular LLM, runtime, database, scoring function, or agent framework.

## 1. Purpose, non-goals, and dependencies

AQSI-006 motivates Question Units and Exploration Contracts; AQSI-007 develops Question Structural Relay and Collective Learning; AQSI-010 places both in a recursive architecture. This specification defines the exchange boundaries and required invariants.

**In scope:** exploration authorization and state transitions; typed exploration records; provenance; evidence and counterevidence; residual capture; relay operators; cross-agent transfer; feedback; versioning; and conformance tests.

**Out of scope:** proving that an answer is correct, selecting a universally optimal question, prescribing one experimental methodology, automatically authorizing external actions, or guaranteeing recursive self-improvement.

Dependencies:

- `SPEC-001-Canonical-Question-Unit-Contract.md` — identity, lifecycle vocabulary, UTN typing, governance.
- `SPEC-002-Structural-Influence-and-Scoring-Contract.md` — directional influence, uncertainty, historical assessments, and portfolio selection.
- `AQSI-007-Question-Structural-Relay-and-Collective-Learning.md` — relay research rationale.
- `AQSI-008-Strategic-Question-Control-Planes.md` — human-defined policy and authority boundaries.
- `AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md` — typed cross-domain alignment.

## 2. Normative language and conceptual boundary

**MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** express proposed contract requirements, not an externally ratified standard. A conforming implementation is one that satisfies the declared profile and passes its corresponding checks.

| Term | Meaning |
|---|---|
| Question Unit (QU) | Stable, versioned research proposition with typed structural factors and provenance |
| Exploration Contract (EC) | Authorized scope, methodology, constraints, outputs, and evidence obligations for an exploration attempt |
| Exploration Attempt (EA) | One identifiable execution or investigation under an EC |
| Evidence Record (ER) | Typed support, counterevidence, observation, inference, or unknown tied to a claim |
| Explicit Leftover (EL) | Unresolved residual, limitation, or follow-up opportunity that remains addressable |
| Relay Piece (RP) | Portable, provenance-preserving result of a structural relay operation |
| Relay Decision (RD) | Review outcome determining admissibility of an RP for a destination, not its truth |
| Historical Outcome (HO) | Versioned feedback record used by HQI and later scoring |

A QU is not its prompt; a selected QU is not an authorized exploration; an accepted RP is not a verified result; and an absence of counterevidence is not proof.

## 3. Contract objects and identifiers

Each object MUST carry an immutable identifier, schema version, creation time, producer or actor reference, and provenance reference(s). Implementations SHOULD use UTN-compatible identities and typed references. Logical IDs and content hashes MAY coexist; a content hash MUST NOT be assumed to establish scientific validity.

| Object | Required conceptual fields | Key invariant |
|---|---|---|
| `QuestionUnit` | `question_id`, `version`, `utn_type_ref`, `proposition`, `origin`, `governance` | Identity remains stable across wording-only changes |
| `ExplorationContract` | `contract_id`, `question_ref`, `objective`, `methods`, `evidence_plan`, `limits`, `authorization_ref`, `validity` | Scope and authorization are explicit |
| `ExplorationAttempt` | `attempt_id`, `contract_ref`, `executor_ref`, `started_at`, `status`, `event_refs` | Every run is independently traceable |
| `EvidenceRecord` | `evidence_id`, `claim_ref`, `kind`, `source_ref`, `method_ref`, `epistemic_status`, `limitations` | Claims and evidence strength cannot silently change |
| `ExplicitLeftover` | `leftover_id`, `origin_ref`, `description`, `uncertainty`, `next_action_options` | Unresolved material is retained |
| `RelayPiece` | `relay_id`, `operation`, `input_refs`, `output_refs`, `transformation`, `provenance`, `governance` | Transformation and lineage are recoverable |
| `RelayDecision` | `decision_id`, `relay_ref`, `destination_ref`, `outcome`, `reviewer_ref`, `reasons` | Acceptance is distinct from verification |
| `HistoricalOutcome` | `outcome_id`, `question_ref`, `attempt_refs`, `assessment_refs`, `evidence_refs`, `relay_refs` | Feedback is reproducible and revisable |

Records SHOULD include machine-readable uncertainty, redaction markers, dependency information, and extension namespaces. An implementation MUST document any required extension fields.

## 4. Separation of question and attempt lifecycles

The canonical **question lifecycle** follows SPEC-001:

`candidate → evaluated → selected → exploring → explored → relayed`

Additional states are `deferred`, `blocked`, `revisit_pending`, and `retired`. Implementations MUST preserve the SPEC-001 meaning and its published transition conditions. A question may have multiple exploration attempts, and an attempt may terminate without closing the question.

The **attempt lifecycle** is separately defined:

`proposed → authorized → queued → running → completed`

Alternative outcomes from `queued` or `running` include `paused`, `cancelled`, `failed`, `expired`, and `quarantined`. `paused → queued` requires revalidation; `failed → queued` creates a **new attempt ID**, not an overwrite. `completed` means a process completed its declared reporting obligations, **not** that its hypothesis was confirmed.

| Attempt transition | Required guard | Required event |
|---|---|---|
| `proposed → authorized` | Valid scope-specific approval; policy check | Authorization decision reference |
| `authorized → queued` | Resources and method available; approval unexpired | Scheduling and budget reservation |
| `queued → running` | Approval still valid; tool/data permissions checked | Start event and environment snapshot |
| `running → completed` | Outcome manifest and required evidence/leftover fields present | Completion event and immutable result references |
| `running → paused` | Recoverable interruption or policy hold | Pause reason and checkpoint |
| `running → cancelled` | Explicit cancellation or revocation | Cancellation reason, partial artifacts, cleanup status |
| `running → failed` | Execution error or method failure | Failure type, diagnostics, retained partial observations |
| `any active → quarantined` | Integrity, privacy, or safety concern | Restriction and review reference |
| `paused → queued` | Fresh authorization and validity check | Resume decision; new run segment |

All transitions MUST be append-only events or equivalently auditable. Consumers MUST NOT infer question status solely from one attempt status.

## 5. Exploration Contract (EC)

An EC MUST bind a specific QU version to an exploration purpose and authorization scope. It MUST state:

1. **Research objective:** proposition, subquestions, expected observation types, and falsification conditions where possible.
2. **Method and adapters:** planned LLM prompts, tools, APIs, simulations, SQL, experiments, or human review; permitted substitutions.
3. **Evidence plan:** required records, source classes, reliability criteria, counterevidence collection, and replication conditions.
4. **Governance:** approving authority, allowed actions, data classification, geographic or organizational scope where applicable, validity interval, and revocation semantics.
5. **Resources:** time, compute, monetary and tool-call budgets, and stop thresholds.
6. **Output obligations:** result manifest, evidence/counterevidence, uncertainties, explicit leftovers, and proposed relay candidates.
7. **Review and fallback:** error handling, escalation, safety stop, and minimum reporting after failure.

An EC MAY allow exploratory method adaptation within a documented envelope. Material scope expansion MUST trigger a new authorization decision. A high AQSI score MUST NOT override this rule.

## 6. Authorization and execution sovereignty

The policy control plane determines permissible directions and constraints; a portfolio selector recommends questions; a separate authority approves action. The required order is:

`candidate → assessment → portfolio selection → policy evaluation → authorization → attempt execution`.

Authorization MUST be attributable, scoped, time-bounded or explicitly non-expiring under policy, and revocable. A revocation MUST block new side effects and SHOULD trigger safe cancellation of running attempts. Read-only analysis and external-world actions MAY have different approval profiles. Human reviewers MUST be able to inspect proposed external effects before approval where the governance profile requires it.

Cross-agent delegation MUST carry **no more authority than the delegator possesses**. Relay transfer does not transfer credentials or permissions by default. An agent MUST NOT treat receipt of an RP as permission to execute its suggested follow-up.

## 7. Evidence, counterevidence, and epistemic status

Every substantive outcome claim MUST link to at least one evidence record or explicitly be marked unsupported/unknown. Each ER MUST distinguish `kind` (e.g., observation, source quotation, model suggestion, inference, negative finding, counterexample, replication) from `epistemic_status` (e.g., hypothesis, model_generated, inferred, observed, experimentally_tested, independently_replicated, refuted, unknown).

An LLM-generated assertion MUST NOT be promoted to `observed` or `independently_replicated` without independent supporting records. A repeated run using the same underlying data MUST NOT be labeled independent replication merely because another agent performed it. Conflicting ERs MUST remain linked to the same claim and SHOULD expose scope and conditions of disagreement.

Evidence references SHOULD record source identifiers, collection times, method versions, data or environment fingerprints, applicability assumptions, and access restrictions. Redaction is permitted when necessary, but MUST be explicit. Evidence dependence SHOULD be represented to prevent double-counting in SPEC-002 scoring.

## 8. Explicit Leftover and unresolved outcomes

An exploration MUST report whether it produced unresolved residuals. An EL MAY describe an untested hypothesis, missing measurement, model disagreement, failed transfer assumption, unexpected observation, incomplete proof, insufficient budget, or newly discovered research opportunity.

Each EL SHOULD include `leftover_type`, `origin_attempt_ref`, `affected_claim_refs`, `severity_or_relevance`, `unknowns`, `candidate_next_questions`, `review_trigger`, and `owner_or_destination_ref`. Unknowns MUST NOT be encoded as negative evidence without justification. Failure to answer the original question MAY still yield a useful EL and a valid relay candidate.

## 9. Relay operation contract

An RP MUST contain `operation_id`, `operation_type`, `input_refs`, `output_refs`, `actor_ref`, `timestamp`, transformation description, provenance, and applicable governance restrictions. Proposed operations:

| Operation | Intended transformation | Special check |
|---|---|---|
| `derive` | Source result or question produces a distinct new question | New proposition gets new `question_id` |
| `split` | Decompose a broad question into addressable subquestions | Preserve parent and coverage limitations |
| `compose` | Combine complementary questions or methods | Identify incompatible assumptions |
| `transfer` | Reframe a structure in a target domain | UTN alignment and domain delta recorded |
| `refute` | Attach disconfirming evidence or counterexample | Preserve original claim and evidence |
| `revisit` | Reassess deferred/retired material | Record triggering new evidence or policy |
| `replicate` | Re-execute to test stability or reproducibility | New attempt and dependence disclosure |
| `fold` | Compress a question family or evidence structure | Preserve reversible references or loss ledger |
| `unfold` | Expand a compressed structure into candidate questions | Mark reconstruction assumptions and uncertainty |

A relay MAY be purely informational; it MUST NOT imply execution authority. When the destination cannot interpret a source type, the RP MUST be rejected, quarantined, or accepted with an explicit unresolved mapping—not silently coerced.

## 10. Relay candidate, review, and acceptance lifecycle

The **relay lifecycle** is:

`draft → submitted → checked → accepted`

Alternative outcomes: `needs_revision`, `rejected`, `quarantined`, `superseded`.

`checked → accepted` requires valid schema, traceable inputs, declared transformation, UTN compatibility or a documented mapping, allowed disclosure, and destination-specific acceptance policy. It does **not** require proof of a claim unless that destination explicitly requires such proof. Rejection MUST include a reason and SHOULD preserve a safe reference for later reassessment. Quarantine MUST block onward dissemination to unauthorized destinations.

A relay receiver MUST preserve the source's epistemic status or explicitly weaken it; strengthening requires additional independent evidence and an auditable assessment. The receiver MUST NOT silently erase counterevidence, failed attempts, or material caveats.

## 11. Question-to-question and exploration-to-question relay

Question-to-question relay records a typed relation between distinct QUs, including causal hypothesis, method reuse, decomposition, contradiction, or dependency. Exploration-to-question relay uses an outcome or EL to propose a new QU. The latter MUST record the precise origin attempt and distinguish observations from interpretation.

A derived question's identity MUST be new if its research proposition materially differs; rephrasing alone SHOULD create a revision of the existing QU. A relay graph MAY contain cycles, but lineage traversal MUST use stable event IDs and cycle-safe algorithms. Cyclic ancestry MUST NOT be interpreted as independent corroboration.

## 12. Cross-domain and cross-agent relay

A cross-domain RP MUST identify source and target UTN types, mapped factors, unmapped factors, transformation rules, assumptions, and transfer limitations. A method may transfer even when domain-level concepts do not. Directional transfer score MUST NOT be mistaken for validated transfer success.

Cross-agent RP exchange SHOULD include capability profile, schema compatibility, trust boundary, review policy, and disclosure limitations. Different agents MAY disagree; disagreement SHOULD be recorded as separate assessments rather than resolved by untraceable averaging. Recipients MUST be able to decline or defer an RP without deleting its provenance.

## 13. Repeated-execution relay

Repeated execution is a legitimate relay pathway when it accumulates new observations, tests reproducibility, estimates variability, or detects drift. Each repeat MUST receive a distinct `attempt_id` and link to the same QU or a documented revision. It SHOULD record what was held constant, what changed, and whether evidence is statistically or causally dependent on prior attempts.

A byte-identical rerun with no new recorded observation or diagnostic information MUST NOT be reported as knowledge growth. Negative or null findings SHOULD be retained. Repeat runs MAY trigger re-scoring, but historical updates MUST avoid treating correlated observations as independent successes.

## 14. Historical Question Intelligence feedback

On completion or meaningful termination, the system SHOULD emit an HO record containing outcome class, direct research value assessment, evidence strength, costs, follow-up questions, accepted/rejected relay references, and uncertainty. A later assessment MAY revise value attribution without overwriting the original record.

HQI updates SHOULD distinguish:

- **Immediate outcome:** answer quality, observed evidence, failure, or unknown.
- **Structural contribution:** reusable method, clarified assumptions, EL, or new question.
- **Delayed contribution:** descendant outcomes attributed with a declared attribution policy.
- **Cost and governance:** resources consumed and restrictions encountered.

A historical scorer MUST NOT interpret selection frequency as ground-truth quality. Validation SHOULD address selection bias, delayed rewards, cold-start questions, and cross-domain applicability. Feedback may improve future rankings but is not evidence of general intelligence improvement without controlled evaluation.

## 15. Idempotency, concurrency, and auditability

Event writers MUST supply unique event IDs and SHOULD support idempotent ingestion. Replayed messages MUST NOT create duplicate evidence or duplicate authorizations. Concurrent agents MAY append competing assessments; the store MUST preserve both and declare reconciliation rules.

An event SHOULD contain `event_id`, `object_ref`, `previous_version`, `new_version`, `event_type`, `actor_ref`, `timestamp`, and `reason`. Implementations MAY use an event log, immutable ledger, or versioned database, provided the relevant history can be reconstructed. Corrections MUST be represented as superseding events rather than silent deletion, subject to applicable privacy and retention obligations.

## 16. Reference YAML: authorized exploration and relay

The following is **illustrative schema-like data**, not an executable workflow or a validated research result.

```yaml
schema: aqsi.exploration-relay.v1
question_ref: "utn:aqsi:question:Q-104@2"
exploration_contract:
  contract_id: EC-104-A
  objective: "Test whether a residual-based method transfers to a new domain"
  methods: [literature_review, controlled_comparison]
  evidence_plan:
    require_counterevidence: true
    require_limitations: true
    independence_check: required
  limits:
    compute_units: 50
    max_attempts: 3
  authorization_ref: AUTH-2026-017
  authorization_status: approved
  valid_until: "2026-12-01T00:00:00Z"
attempt:
  attempt_id: EA-104-01
  status: completed
  outcome_class: inconclusive
  evidence_refs: [ER-104-01, ER-104-02]
  counterevidence_refs: [ER-104-02]
  leftover_refs: [EL-104-01]
  limitations: ["Small evaluation sample", "Target-domain assumptions unresolved"]
relay:
  relay_id: RP-104-01
  operation: derive
  input_refs: [EA-104-01, EL-104-01]
  output_refs: ["utn:aqsi:question:Q-105@1"]
  transformation: "Turn unresolved target-domain assumption into a testable question"
  epistemic_status: hypothesis
  decision:
    outcome: accepted
    meaning: contract_admissible_only
    reviewer_ref: REVIEWER-02
historical_feedback:
  outcome_id: HO-104-01
  question_ref: "utn:aqsi:question:Q-104@2"
  outcome_class: inconclusive
  descendant_value: unknown
  assessment_policy_ref: HQI-POLICY-01
```

No sample ID above represents a real authorization, experiment, or dataset.

## 17. Minimal protocol and algorithm sketch

```text
PROPOSE(QU, assessment, portfolio_decision):
    verify QU identity and version
    verify assessment provenance and policy eligibility
    draft EC with evidence, budget, stop, and review obligations
    return EC in proposed state

AUTHORIZE(EC, authority):
    verify authority, scope, validity, resources, and permissions
    append authorization event; never infer approval from score

EXPLORE(EC):
    verify approval at start and before consequential side effects
    create new EA; append start event
    perform only permitted steps; capture method and environment
    record supporting, contradictory, and unknown evidence
    record errors, limitations, costs, and explicit leftovers
    append outcome manifest, including partial or negative outcomes

RELAY(EA, QU):
    construct candidate RPs with typed transformations and lineage
    validate schema, UTN mapping, evidence, and governance
    accept, reject, quarantine, or request revision with reasons
    emit HOs without treating acceptance as truth
    propose derived QUs for later scoring and separate authorization
```

An implementation MUST NOT silently skip authorization or required reporting steps because a runtime adapter cannot support them.

## 18. Conformance profiles

Three incremental profiles are proposed:

- **C0 — Traceable Single-Agent Exploration:** stable IDs, EC, separate authorization, attempt events, evidence/counterevidence, EL, completion manifest.
- **C1 — Structural Relay Interoperability:** C0 plus typed RP operations, destination review, UTN mappings, rejection/quarantine, lineage and epistemic non-escalation.
- **C2 — Collective Learning and HQI Feedback:** C1 plus cross-agent exchange, repeated-execution dependence, versioned HOs, delayed value attribution, and concurrency handling.

Claimed conformance MUST identify the profile, schema version, test results, exceptions, and date. C0 compliance does not imply C1 or C2 compliance.

## 19. Normative conformance requirements

| ID | Requirement | Test intent |
|---|---|---|
| REL-001 | Every QU, EC, EA, ER, RP, and HO has stable ID and version/provenance | Reject anonymous records |
| REL-002 | Question and attempt states are distinct | Multi-attempt question remains consistent |
| REL-003 | Attempt transitions are auditable | Reconstruct state from events |
| REL-004 | Selected QU cannot execute without authorization | Deny selected-but-unapproved run |
| REL-005 | Revoked/expired approval blocks new side effects | Simulate revocation mid-run |
| REL-006 | Every completed attempt has outcome manifest | Reject empty completion |
| REL-007 | Unsupported/model-generated claims are not upgraded to observed | Epistemic non-escalation |
| REL-008 | Counterevidence is retained and linked | Conflict round-trip |
| REL-009 | Unknown and negative evidence remain distinct | Unknown-vs-zero test |
| REL-010 | EL is recorded or explicitly declared absent | Failure and inconclusive cases |
| REL-011 | Relay declares operation and source-to-output transformation | Lineage traversal |
| REL-012 | Materially new proposition receives new question identity | Derive-vs-revise test |
| REL-013 | Cross-domain transfer records mapping and unmapped assumptions | Missing-mapping test |
| REL-014 | Relay acceptance does not promote scientific status | Acceptance semantics test |
| REL-015 | Rejection/quarantine preserves reason and blocks improper dissemination | Quarantine test |
| REL-016 | Repeated attempts use distinct IDs and dependence metadata | Replication test |
| REL-017 | Cross-agent relay does not propagate execution authority | Privilege-escalation test |
| REL-018 | HOs preserve original outcomes under later reassessment | Append-only revision test |
| REL-019 | Duplicate events do not duplicate evidence or authorization | Idempotency test |
| REL-020 | Concurrent assessments remain distinguishable | Conflicting agent updates |
| REL-021 | Privacy redaction is explicit and permission-preserving | Redacted evidence transfer |
| REL-022 | Schema evolution does not silently reinterpret prior records | Version migration test |

## 20. Validation scenarios and negative tests

**Scenario A — Unanswered but productive:** an authorized investigation ends inconclusively, retains counterevidence, and derives a testable EL-based question. Expected: `completed` attempt, unresolved QU, admissible derived RP, no false success claim.

**Scenario B — Failed execution:** a tool error prevents data collection. Expected: `failed` attempt with diagnostics; no invented observation; a retry requires a new EA and fresh authorization check.

**Scenario C — Cross-domain transfer:** a source method is mapped to a target domain with one unmapped constraint. Expected: explicit mapping gap and uncertainty; no automatic claim of successful transfer.

**Scenario D — Replication:** three agents repeat the same test against the same underlying dataset. Expected: three attempts but dependence disclosure; no automatic independent-replication status.

**Scenario E — Governance revocation:** approval is revoked during a running exploration. Expected: no further unauthorized side effects, cancellation or safe pause, partial output retained according to policy.

**Scenario F — Adversarial relay:** an RP contains a forged approval reference or requests that the recipient ignore policy. Expected: refusal/quarantine; RP content treated as untrusted data, never as instructions.

**Scenario G — Conflicting evidence:** two sources support opposite conclusions. Expected: both preserved with scope, confidence, and provenance; no silent overwrite.

**Scenario H — Delayed value:** an initially inconclusive question later generates a successful descendant. Expected: versioned historical reassessment, not retroactive alteration of the original outcome.

## 21. Metrics and proposed research hypotheses

The following are **testable hypotheses**, not established performance claims:

- **H1 — Provenance preservation:** contract-based relay improves reconstructability of question ancestry versus unstructured chat logs.
- **H2 — Epistemic integrity:** explicit evidence-status rules reduce unsupported confidence escalation.
- **H3 — Negative-result reuse:** retaining EL and failed attempts increases later useful question discovery.
- **H4 — Repeated-execution value:** dependence-aware repeated-execution relay improves calibration of reproducibility estimates.
- **H5 — Cross-agent portability:** typed relay reduces loss of critical assumptions during agent handoff.
- **H6 — Governance:** separated authorization reduces unauthorized actions relative to selection-as-approval baselines.
- **H7 — HQI learning:** versioned outcome feedback improves future question prioritization after controlling for selection bias.
- **H8 — Open-ended growth:** relay-based question discovery yields more validated downstream research value per unit resource than answer-only baselines.

Suggested measures: provenance reconstruction accuracy; missing-counterevidence rate; unsupported status-upgrade rate; useful EL reuse; transfer assumption loss; duplicate-evidence inflation; unauthorized-action count; question-family diversity; delayed-value calibration; and validated downstream contribution per cost. Compare against answer-only logs, free-form agent handoffs, no-EL pipelines, and no-history scoring, with blinded adjudication where feasible. Report confidence intervals and negative results.

## 22. Threats, failure modes, and safeguards

- **Prompt injection in source material or relay payloads:** treat external text as data, enforce policy at tool boundary, and require independent authorization.
- **Fabricated citations or evidence:** demand source references and distinguish unverifiable claims.
- **Provenance laundering:** never elevate weak source evidence merely by repeated relay or summarization.
- **Reward hacking / Goodhart effects:** use multiple evaluators, audit outcome attribution, and measure actual downstream research value.
- **Excessive retention:** apply privacy, deletion, access, and retention requirements; append-only audit does not override legal deletion obligations.
- **Schema rigidity:** permit typed extensions and explicit unknown fields rather than forcing false mappings.
- **Relay explosion:** control branching and costs with portfolio policies while retaining deferred candidate references.
- **Premature termination:** preserve review triggers for deferred and retired questions.
- **Overstated autonomy:** human research governance and explicit action authority remain distinct from autonomous question discovery.

## 23. Compatibility, versioning, and extension policy

A minor schema extension MAY add optional typed fields without changing established meanings. A change to required fields, lifecycle semantics, authorization interpretation, or epistemic-status meaning requires a new major contract version. Producers MUST declare versions; receivers MUST either negotiate a supported version or reject with a machine-readable reason. Unknown extension fields MAY be retained opaquely if safe, but MUST NOT be silently interpreted as authorization or evidence.

UTN mappings SHOULD be versioned and reversible where possible. Folding/unfolding transformations SHOULD disclose information loss. Future work may define JSON Schema, event APIs, cryptographic attestations, or formal temporal-logic invariants, but this document does not claim those implementations exist.

## 24. Open questions

1. Which minimal evidence obligations preserve scientific usefulness without overburdening lightweight exploratory work?
2. How should relay lineage be compressed while retaining essential provenance and counterevidence?
3. When is repeated execution informative rather than merely redundant?
4. How should delayed descendant value be attributed without double-counting or retrospective bias?
5. What evidence supports transferring an epistemic status across domains?
6. How should distributed agents reconcile contradictory historical assessments without imposing artificial consensus?
7. Can conformance profiles remain portable across scientific, software-engineering, and organizational research settings?
8. Which governance controls most effectively preserve human strategic authority without suppressing legitimate autonomous discovery?

## 25. Relationship to other AQSI documents

| Document | Interface to SPEC-003 |
|---|---|
| `AQSI-001-From-Answering-to-Autonomous-Questioning.md` | Motivation and limits of autonomous questioning |
| `AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md` | Outcome memory, reassessment, question families |
| `AQSI-006-Question-Units-and-Exploration-Contracts.md` | QU and EC research model |
| `AQSI-007-Question-Structural-Relay-and-Collective-Learning.md` | Relay operations and collective learning rationale |
| `AQSI-008-Strategic-Question-Control-Planes.md` | Policy and authority governance |
| `AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md` | Type alignment and transfer assumptions |
| `AQSI-010-MVP-Architecture-and-Recursive-Evolution.md` | MVP staging, feedback, and recursive improvement |
| `SPEC-001-Canonical-Question-Unit-Contract.md` | Canonical QU and lifecycle vocabulary |
| `SPEC-002-Structural-Influence-and-Scoring-Contract.md` | Assessment, portfolio, and influence records |
| `SPEC-004-Control-Plane-and-Policy-Conformance.md` | Planned policy and authorization conformance |

## 26. Conclusion

AQSI exploration and relay require more than a sequence of prompts and answers. This proposed specification makes research attempts, evidence, counterevidence, explicit leftovers, and derived questions portable and auditable, while preserving the difference between **selection and authorization**, **relay acceptance and scientific verification**, and **repeated execution and independent corroboration**. It defines a contract boundary for future MVP implementations and falsifiable evaluation, not a claim that autonomous research or recursive intelligence improvement has already been demonstrated.

---

## Appendix A — Minimal event envelope

```yaml
schema: aqsi.lifecycle-event.v1
event_id: EVT-104-019
object_ref: EA-104-01
previous_version: 3
new_version: 4
event_type: attempt.completed
actor_ref: AGENT-RESEARCH-01
timestamp: "2026-10-28T18:00:00Z"
reason: "Method ended; outcome recorded as inconclusive"
related_refs: [EC-104-A, ER-104-01, ER-104-02, EL-104-01]
```

## Appendix B — Minimal relay-review response

```yaml
schema: aqsi.relay-decision.v1
decision_id: RD-104-01
relay_ref: RP-104-01
destination_ref: "utn:aqsi:portfolio:research-2026"
outcome: accepted
acceptance_scope: contract_admissibility
scientific_verification: not_established
reviewer_ref: REVIEWER-02
checks:
  schema_valid: true
  provenance_complete: true
  governance_permits_transfer: true
  mapping_assumptions_declared: true
reason: "Sufficiently typed and traceable for further research"
```

## Appendix C — Conformance checklist

A conformance report SHOULD state the target profile, implementation version, schema versions, tests REL-001 through REL-022 that apply, passed/failed/skipped results, known exceptions, sample event traces, and evaluator identity. Passing a checklist establishes only declared contract behavior; it does not establish research quality, scientific truth, or autonomous intelligence capability.
