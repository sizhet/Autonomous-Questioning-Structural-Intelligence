# AQSI-007 — Question Structural Relay and Collective Learning

**Project:** Autonomous Questioning Structural Intelligence (AQSI)  
**Version:** 1.0.0 — Initial Research Framework  
**Status:** Research proposal; conceptual architecture and testable specifications, not a validated implementation  
**License:** Apache-2.0 (repository-level)  
**Companion papers:** AQSI-001 through AQSI-006; AQSI-008 through AQSI-010

## Abstract

Autonomous questioning is not merely the repeated generation of prompts. It requires a mechanism by which a question, its exploration, its failures, and its newly exposed uncertainties can become reusable research assets for other questions, agents, domains, and future generations of the system. This paper proposes **Question Structural Relay (QSR)** as that mechanism. QSR treats a question as a typed, provenance-bearing structural unit; treats exploration as an evidence-producing transformation; and treats relay as an explicit, auditable transfer of structure, hypotheses, methods, constraints, and residuals. The resulting question ecosystem can support collective learning without assuming that model agreement constitutes truth, that all question transfers preserve meaning, or that recursive improvement is inevitable.

The paper distinguishes question-to-question, exploration-to-question, cross-domain, cross-agent, and repeated-execution relay. It defines relay operators, compatibility and provenance requirements, a lifecycle, governance boundaries, and an initial experimental agenda. Its central hypothesis is that structured, evidence-aware relay can yield more reusable research progress per unit of exploration cost than isolated prompt-and-answer workflows. That hypothesis remains to be tested.

**Keywords:** autonomous questioning; structural relay; question units; collective learning; provenance; counter-evidence; residual-driven discovery; cross-domain transfer; UTN; recursive improvement

---

## 1. Motivation: Beyond Isolated Question–Answer Transactions

A conventional question-answering system accepts a request and produces a response. A more capable research assistant may also search, plan, invoke tools, and revise its response. Yet the research value of an exploration can be lost when its output is retained only as a transcript or a summary. A transcript does not necessarily preserve which assumption was tested, which evidence supports a conclusion, what failed, or which newly generated questions deserve further investigation.

AQSI proposes a different unit of continuity: a **Question Unit (QU)** linked to exploration contracts, evidence records, and other QUs. The system should be able to answer not only *What did we conclude?* but also:

- Which question and structural context produced this result?
- Which methods were attempted, with what cost and limitations?
- Which claims are supported, contradicted, or still unresolved?
- Which new questions became possible because of the result?
- Can another subject, agent, or domain reuse the result under a valid semantic mapping?
- What changed in the historical scoring and future question portfolio?

**Question Structural Relay** is the proposed mechanism for preserving and transferring these answers.

## 2. Research Position and Scope

This paper addresses the **relay and collective-learning layer** of AQSI. It builds on:

- **AQSI-002:** candidate generation from gaps, residuals, associations, and previous relays;
- **AQSI-003:** multi-granularity, directed structural influence factors;
- **AQSI-004:** historical question intelligence and question differential trees;
- **AQSI-005:** goal-open scoring and research portfolio selection;
- **AQSI-006:** canonical Question Units and Exploration Contracts.

It interfaces with strategic governance in AQSI-008, UTN alignment in AQSI-009, and system evolution in AQSI-010. It does **not** claim to solve general knowledge representation, establish universal semantic equivalence, or guarantee autonomous scientific discovery.

### 2.1 Working definitions

**Question Unit (QU).** A versioned, typed research object containing a question, structural representation, provenance, assumptions, scores, evidence links, status, and relay references.

**Exploration Record (ER).** A record of an authorized investigation under an Exploration Contract, including methods, observations, costs, outcomes, counter-evidence, and explicit leftovers.

**Relay Piece (RP).** A bounded, reusable structural contribution derived from a QU or ER, with a declared type, scope, confidence/evidence status, and compatibility conditions.

**Question Structural Relay (QSR).** A provenance-preserving transformation or transfer in which one or more QUs, ERs, or RPs inform the creation, revision, or evaluation of another research object.

**Collective Structural Learning.** Accumulation and exchange of reusable, scrutinizable research structure across multiple explorers or contexts, rather than mere aggregation of textual outputs.

## 3. Canonical Relay Objects

A minimal QSR ecosystem needs four object classes and explicit references among them.

| Object | Essential content | Main purpose |
|---|---|---|
| Question Unit | ID, UTN typing, structural facets, provenance, hypothesis, state | Stable research identity |
| Exploration Contract | Scope, method, budget, permissions, evidence criteria, termination rules | Bounded investigation |
| Exploration Record | Observations, attempted methods, outcome, counter-evidence, residuals | Reproducible feedback |
| Relay Piece | Source references, transformation, semantic mapping, validity conditions, destination | Portable structural learning |

An RP may represent a new question, a discovered relation, a negative result, a reusable method, a constraint, a partial proof, a counterexample, or an unresolved gap. **A failed exploration may produce a valuable RP** if it identifies a reliable boundary or eliminates an invalid approach.

### 3.1 Minimal relay envelope

The following YAML is **illustrative**, not a finalized machine-readable schema:

```yaml
relay_id: "aqsi:relay:example-042"
relay_type: "residual-to-question"
source:
  question_ids: ["aqsi:question:017"]
  exploration_ids: ["aqsi:exploration:031"]
  evidence_refs: ["aqsi:evidence:112"]
destination:
  question_id: "aqsi:question:088"
structural_transfer:
  unit_types: ["method", "constraint", "unresolved-assumption"]
  alignment_ref: "utn:alignment:example-7"
  transformation: "reformulate unresolved assumption as testable question"
validity:
  domain_scope: "specified-domain"
  evidence_status: "partially-supported"
  uncertainty: "explicit"
  counterevidence_refs: []
governance:
  policy_ref: "aqsi:policy:research-default"
  authorization_status: "permitted"
provenance:
  created_by: "research-agent-example"
  created_at: "illustrative-timestamp"
  parent_relay_ids: []
```

Relay identifiers and timestamps must be generated by the implementation; example values above do not denote actual experiments.

## 4. Five Fundamental Relay Pathways

### 4.1 Question-to-question relay

A source question exposes structural facets relevant to another question. Examples include sharing a hypothesis, transferring a method, or exposing an unanswered dependency. This is not limited to a semantic similarity edge: a method in one question may influence a constraint or evidence need in another.

### 4.2 Exploration-to-question relay

An exploration produces observations or failures that generate or revise questions. A failed experiment may reveal an untested assumption; a successful experiment may expose a boundary condition or a new optimization problem.

### 4.3 Cross-domain relay

A typed relation or method is transferred across domains through an explicit mapping. UTN can help align identity, granularity, semantic contracts, and namespaces. The system must distinguish **analogical suggestion** from **validated transfer**: shared vocabulary alone does not justify reuse.

### 4.4 Cross-agent and cross-subject relay

Different explorers may contribute candidate questions, criticism, evidence, alternative models, or independent replications. Contributions remain attributable. The system should preserve disagreements rather than automatically fold them into a consensus score.

### 4.5 Repeated-execution relay

Repeating the same or closely related exploration can produce a **data-accumulation relay**: new observations, stability estimates, drift detection, and changed confidence. A repeated run is not necessarily redundant, provided it adds identifiable evidence or tests reproducibility. Identical outputs with no new information should not be double-counted as independent support.

## 5. Structural Relay Operators

QSR may be modeled as a family of typed operators. The following are **proposed design primitives**, not proven complete.

| Operator | Input → output | Key condition |
|---|---|---|
| `DERIVE` | QU + ER → descendant QU | Traceable new question |
| `SPLIT` | QU → multiple narrower QUs | Scope partition recorded |
| `COMPOSE` | several QUs → composite QU | Assumptions reconciled |
| `TRANSFER` | RP in domain A → RP/QU in domain B | Explicit semantic alignment |
| `REFUTE` | counter-evidence → revised/invalidated claim | Claim-specific contradiction |
| `REVISIT` | deferred QU + new evidence → updated QU | New trigger documented |
| `REPLICATE` | contract + repeated ERs → evidence aggregate | Independence assessed |
| `GENERALIZE` | several supported instances → candidate principle | Generality remains provisional |
| `LOCALIZE` | broad method/principle → bounded domain adaptation | Applicability checked |
| `FOLD` | related RPs → compact reusable representation | Information loss documented |
| `UNFOLD` | compact RP → candidate variants | Reconstruction uncertainty recorded |

Operators should be replaceable, composable, and subject to conformance tests. A relay may be **informational** without creating a new QU, or **generative** when it creates a new research candidate.

## 6. Multi-Granularity Question Influence as Relay Guidance

Let a Question Unit contain a heterogeneous set of typed structural facets:

$$
H(q_i)=\{h_{i1},\ldots,h_{im_i}\}.
$$

A directed influence estimate from question \(q_i\) to \(q_j\) can be expressed as:

$$
I(q_i\!\rightarrow\!q_j)=operatorname{Fold}_{a,b,r}
\left(w_{abr}\,R_r(h_{ia},h_{jb})\right),
$$

where \(R_r\) is a typed relation scorer and \(w_{abr}\) is a context-dependent weight. This extends beyond concept-to-concept association to methods, constraints, evidence, assumptions, failures, and potential transfer points. Direction matters: a technique from question A may help question B without the reverse being true.

**Unknown is not zero.** Missing relation evidence should be represented separately from an observed weak or negative relation. An influence estimate is also not equivalent to actual scientific value: it is a routing hypothesis to be calibrated by outcomes.

A relay candidate may be ranked by expected benefit, evidence strength, transfer risk, and cost. For example:

$$
U(r\mid\mathcal H,\pi)
=\mathbb E[\Delta V(r)\mid\mathcal H]
-\lambda C(r)-\mu T(r),
$$

where \(\mathcal H\) is historical evidence, \(\pi\) is an authorized policy, \(C\) is resource cost, and \(T\) is semantic or operational transfer risk. This equation is a **candidate objective**, not an established empirical law. Alternative evaluators and non-scalar Pareto selection should remain possible.

## 7. Relay Lifecycle and State Transitions

A proposed lifecycle is:

```text
Candidate Question
      |
      v
Typed / Aligned / Provenance-Checked
      |
      v
Scored / Selected / Deferred
      |
      v
Authorized Exploration
      |
      v
Evidence + Counter-Evidence + Explicit Leftover
      |
      v
Relay Piece Construction
      |
      v
Compatibility / Governance / Quality Review
      |
      +----> Rejected or Quarantined (with reason)
      |
      v
Accepted Relay -> New / Revised / Revisited Questions
      |
      v
Historical Question Intelligence Update
      |
      +----> Re-scoring and Portfolio Reconsideration
```

An accepted relay is not automatically an accepted scientific conclusion. Acceptance may mean only that a candidate relation or question is safe and sufficiently documented for further investigation.

### 7.1 State invariants

1. Every relay has at least one identifiable source and a declared transformation.
2. A destination cannot silently inherit stronger evidence status than its sources justify.
3. Failed, deferred, or rejected relay candidates retain a reason and may be revisited.
4. Contradictory evidence is preserved and linked to the affected claim.
5. Human policy and resource constraints apply before external action.
6. A relay must distinguish original observation from model-generated interpretation.
7. Repeated evidence from the same source is not counted as independent replication.

## 8. From Individual Exploration to Collective Learning

Collective learning requires a **shared structural exchange layer** without forcing all participants to adopt one model, one scoring function, or one ontology. A practical design separates:

- **Local exploration:** agents or teams investigate within their own contexts and permissions.
- **Portable relay pieces:** bounded, typed contributions are exported with evidence and provenance.
- **Compatibility evaluation:** recipients check UTN mappings, contract assumptions, and domain applicability.
- **Local adoption:** recipients may accept, adapt, contest, or reject a relay piece.
- **Feedback relay:** the adoption outcome becomes a new contribution to the shared history.

This architecture supports heterogeneous contributors: LLM-based researchers, symbolic tools, human domain experts, experimental systems, and organizational teams. It does not require identical internal representations, only sufficiently explicit interfaces for each transfer.

### 8.1 A relay graph, not a single linear chain

Let \(G_t=(V_t,E_t)\) be a versioned graph whose nodes include QUs, ERs, RPs, evidence objects, and policies. Edges identify derivation, support, contradiction, analogy, transfer, replication, and supersession. The graph may contain branching and convergence; provenance edges should remain acyclic with respect to creation history, even when semantic influence links form cycles.

A question can contribute to several later discoveries, and several questions can jointly produce one relay piece. This is why **lineage** and **influence** must be modeled separately.

## 9. Question Families, Differential Trees, and Relay Compression

Question Differential Trees (QDTs) can represent shared cores and structured differences among question variants:

$$
q_k = operatorname{Instantiate}(\mathrm{Core},\Delta_k,\mathrm{Context}_k).
$$

Relay may operate at the family level: a reusable method learned for a common core can inform several variants, while an exception discovered in one branch can constrain a narrower subset. Compression should preserve the information necessary to recover validity boundaries, provenance, and uncertainty. A compact representation that erases counterexamples is not an acceptable research relay.

Possible QDT operations include branch creation, sibling comparison, residual extraction, family-level scoring, and selective reopening when new evidence changes the common core. QDTs are one representation option, not a mandatory universal substrate.

## 10. Historical Feedback and Value Attribution

Historical Question Intelligence (HQI) stores the consequences of relay: not only whether an initial question was answered, but whether it enabled useful descendants, exposed invalid assumptions, or reduced repeated effort.

A proposed time-dependent outcome model is:

$$
V_t(q)=V_t^{\mathrm{direct}}(q)
+\alpha\,V_t^{\mathrm{relay}}(q)
-\beta\,C_t(q),
$$

where relay value is estimated from downstream contributions with explicit attribution limits. **This is a bookkeeping proposal, not a claim that all downstream benefit can be causally assigned.** Multiple ancestors, delayed outcomes, selective exploration, and changing evaluation criteria make attribution difficult.

Recommended safeguards include:

- Track observed outcomes separately from predicted scores.
- Record exposure and selection probabilities when available to diagnose selection bias.
- Preserve deferred candidates to avoid training exclusively on previously selected questions.
- Avoid double counting the same evidence along several relay paths.
- Permit retrospective re-evaluation when descendant results arrive.
- Maintain an explicit cold-start path for unfamiliar or weakly represented domains.

## 11. Multi-Agent Exploration and Disagreement Preservation

A proposed collective workflow assigns complementary roles, which may be fulfilled by humans, software agents, or a mixture:

1. **Discoverer:** proposes questions from gaps, residuals, and structural associations.
2. **Mapper:** identifies multi-granularity relations and UTN alignments.
3. **Critic:** searches for counterexamples, hidden assumptions, and invalid transfers.
4. **Experimenter:** executes authorized investigations and records observations.
5. **Evaluator:** updates scores, uncertainty, and evidence status.
6. **Curator:** packages portable relay pieces and maintains provenance.

Role diversity is useful only if it creates independent scrutiny. Multiple agents built from similar models may share correlated errors. The system should record model/tool lineage and should not interpret majority agreement as independent validation.

## 12. Governance, Sovereignty, and Access Boundaries

Question generation may be relatively open-ended; **execution and external effects must remain bounded**. A Strategic Question Control Plane (AQSI-008) can set research priorities, budgets, safety constraints, data permissions, and approval requirements. Relay should respect:

- Source licensing and attribution obligations;
- Confidentiality, privacy, and organizational boundaries;
- Authorized tool and experiment scopes;
- Restrictions on transferring sensitive or proprietary evidence;
- Human control over strategic objectives and consequential actions;
- Auditability of policy changes and exceptions.

A structurally attractive question is not an authorization to act. Cross-organization exchange may share a redacted structural summary while withholding underlying sensitive evidence; the recipient must know that the evidence is unavailable for independent verification.

## 13. A Minimal Relay Protocol

The following conceptual protocol is implementation-neutral:

```text
INPUT: QuestionUnit q, ExplorationRecord e, Policy pi, History H

1. verify_contract(q, e, pi)
2. extract_claims_evidence_counterevidence_residuals(e)
3. construct_typed_relay_candidates(q, e)
4. for each candidate r:
     a. attach provenance and source-specific evidence status
     b. map UTN types / structural facets where applicable
     c. evaluate semantic compatibility and transfer risk
     d. estimate prospective value using historical feedback
     e. enforce policy, budget, and authorization constraints
     f. accept, defer, quarantine, or reject with reason
5. materialize accepted relay pieces and descendant Question Units
6. update lineage graph and historical question intelligence
7. rescore affected candidates and reconsider portfolio
8. record explicit leftovers and unresolved alignment issues

OUTPUT: Versioned relay records, updated question graph, audit trail
```

This is a research-level algorithm sketch. It does not prescribe a specific database, model, or runtime.

## 14. Three Illustrative Research Cases

### 14.1 Case A — Software testing residual to new question

A testing question asks whether a code-generation workflow catches boundary-condition errors. Exploration reveals repeated failures on state transitions. Instead of storing only a failure summary, QSR creates an RP identifying the transition class, affected assumptions, reproduction conditions, and evidence. A descendant QU asks whether state-transition coverage should be a separate evaluation dimension. The proposed benefit is traceable follow-up research; no performance improvement is asserted without measurement.

### 14.2 Case B — Cross-domain transfer of a negative result

A scheduling heuristic performs poorly when constraints change rapidly. A researcher proposes a structurally analogous problem in experiment prioritization. UTN alignment identifies which constraint types match and which do not. The negative result is relayed as a **warning hypothesis**, not a proof that the heuristic will fail in the new domain. A low-cost discriminating test is generated before adoption.

### 14.3 Case C — Collective replication and delayed value

Several teams explore variants of the same research question. Initial outcomes disagree. Rather than averaging away disagreement, the system records environment, method, and evidence differences. A later meta-question asks which contextual variable explains the divergence. Repeated execution contributes observations; the derived question contributes structural growth. The original question's long-term relay value may be updated only after the follow-up investigation yields evidence.

## 15. Failure Modes and Defensive Design

| Failure mode | Consequence | Proposed defense |
|---|---|---|
| Semantic drift during transfer | Misleading analogy | Typed mapping and explicit scope |
| Hallucinated provenance | False confidence | Verifiable source identifiers and audit logs |
| Evidence laundering | Model claim treated as observation | Evidence-type separation |
| Circular reinforcement | Repeated claims appear independent | Lineage-aware deduplication |
| Over-compression | Loss of exceptions | Preserve counterexamples and validity bounds |
| Novelty suppression | Cold-start questions filtered out | Exploration reserve and reversible deferral |
| Relay explosion | Cost and noise growth | Budgets, pruning, quality gates |
| Consensus bias | Shared model errors amplified | Independent critique and replication |
| Policy bypass | Unauthorized execution or disclosure | Contract and control-plane enforcement |
| Metric gaming | High relay counts without discoveries | Outcome-based, multi-metric evaluation |

Relay volume, number of generated questions, and graph density are **not** sufficient measures of research progress.

## 16. Testable Hypotheses

The following hypotheses are proposals requiring controlled evaluation:

**H1 — Reuse:** Structured QSR improves retrieval and reuse of prior research outcomes compared with transcript-only memory under comparable cost.

**H2 — Traceability:** Provenance-bearing relay reduces unsupported evidence inheritance and makes error diagnosis easier than untyped summary exchange.

**H3 — Residual discovery:** Explicit residual-to-question relay yields a higher proportion of independently judged useful follow-up questions than generic follow-up prompting.

**H4 — Cross-domain precision:** UTN-assisted compatibility checks reduce invalid cross-domain transfers relative to semantic similarity alone, without unacceptable loss of useful transfers.

**H5 — Negative knowledge:** Relaying failed approaches and counter-evidence reduces repeated unproductive exploration under matched task distributions.

**H6 — Collective benefit:** Heterogeneous, independently reviewed relay yields greater validated research progress per unit cost than isolated agents or naive majority-vote ensembles.

**H7 — Delayed value:** Incorporating descendant-question outcomes improves question prioritization over immediate-answer success alone, after accounting for selection bias.

**H8 — Repeat execution:** Explicit repeated-execution relay improves uncertainty calibration or drift detection compared with treating reruns as duplicate text.

Each hypothesis can fail; failure should update the architecture rather than be hidden.

## 17. Validation Design and Metrics

### 17.1 Baselines

- **B0:** Standalone LLM answering with no persistent history.
- **B1:** LLM plus transcript retrieval or ordinary summarization.
- **B2:** Question memory with semantic embeddings but no typed relay.
- **B3:** Typed Question Units without cross-question relay.
- **B4:** QSR without historical outcome feedback.
- **B5:** Full proposed QSR with history, UTN alignment, and governance.

Ablations should isolate provenance, residual relay, multi-granularity influence, historical scoring, and cross-domain alignment. Equalize token, tool, human-review, and wall-clock budgets where possible.

### 17.2 Outcome measures

Measure **validated useful descendant questions**, independent reproducibility, rate of invalid transfer, evidence traceability, research cost per useful result, duplicated effort, calibration of predicted value, coverage of novel domains, policy compliance, and time-to-correct a false claim. Human expert judgments should use preregistered rubrics and blinded comparison where feasible.

### 17.3 Experimental stages

**M0 — Single-domain closed loop:** 50–200 historical question records, typed QUs, one exploration tool, residual relay, and a basic audit trail. The range is an experimental planning suggestion, not a dataset requirement.

**M1 — Multi-granularity relay:** add typed facet relations, question families, counter-evidence, and delayed-value feedback.

**M2 — Cross-domain transfer:** evaluate UTN mappings and transfer-risk gates on deliberately mismatched as well as plausible analogies.

**M3 — Multi-agent collective learning:** compare independent reviewers and heterogeneous explorers with isolated or homogeneous-agent baselines.

**M4 — Recursive adaptation:** allow controlled changes to scoring or relay policies in a sandbox, with held-out evaluation and rollback.

## 18. Relationship to the Broader SI Research Program

QSR is intended as a composable interface, not a claim to replace neighboring systems:

| Related research line | Proposed AQSI interaction |
|---|---|
| SIF — Structural Intelligence Framework | Localization, addressing, node intelligence, structural growth |
| UIERU — Universal Intelligence Evolution and Relay Unit | Portable units, multi-trail exploration, portfolio exchange, bidirectional learning |
| UTN — Universal Typing and Naming | Typed identity, semantic contracts, cross-domain alignment |
| UCPSF — Universal Control Planes and Scoring Folding | Multi-perspective scoring and governed folding |
| MDI / BM-ODWEI | Directional intuition and weak/other-than-matching associations |
| SRSI — Structural Recursive Self-Improvement | Evaluator governance, adversarial tests, controlled improvement |
| AQSI-008 | Strategic control, policy and resource allocation |
| AQSI-009 | UTN-based cross-domain question transfer |
| AQSI-010 | MVP integration and recursive evolution |

These are architectural connections proposed for investigation; interoperability and measurable synergy are not yet established.

## 19. Open Questions

1. What is the smallest relay schema that preserves sufficient meaning without excessive annotation cost?
2. How should causal credit be divided among multiple ancestor questions and agents?
3. When should a weak cross-domain analogy be explored rather than rejected?
4. How can a relay graph support efficient retrieval without biasing toward popular question families?
5. What evidence is sufficient to promote a candidate relay piece into a reusable principle?
6. How should contradictory evidence be represented across incompatible measurement regimes?
7. Can historical question intelligence avoid suppressing radically new research directions?
8. Which provenance guarantees are feasible across organizational trust boundaries?
9. How can policy updates propagate without retroactively falsifying historical authorization records?
10. Which collective-learning gains persist when evaluated on genuinely unseen domains?

## 20. Conclusion

Question Structural Relay proposes a path from isolated question-answer exchanges toward a persistent, inspectable **question research ecosystem**. Its essential design commitments are typed Question Units, evidence-aware exploration records, explicit relay transformations, preserved counter-evidence, multi-granularity influence, historical feedback, cross-domain compatibility checks, and human-governed execution boundaries.

The central engineering insight is that **the answer is not necessarily the end product of questioning**. A valuable exploration may also produce a better question, a reusable method, a negative constraint, a new relation, or an explicit leftover that another explorer can investigate. Repeated execution can likewise be a relay when it adds evidence rather than merely repeating text.

Whether this architecture yields better research productivity, stronger collective learning, or reliable recursive improvement remains an empirical question. The appropriate next step is to implement small, contract-driven prototypes and evaluate them against simpler memory and multi-agent baselines.

---

## Appendix A — Relay Quality Checklist

- [ ] Source Question Unit and Exploration Record are identifiable.
- [ ] Transformation type and destination are explicit.
- [ ] Structural facets and UTN alignment are documented where needed.
- [ ] Evidence and counter-evidence are separated from interpretation.
- [ ] Uncertainty, unknowns, and scope restrictions are retained.
- [ ] Duplicate and dependent evidence are not double counted.
- [ ] Policy, licensing, privacy, and execution permissions are checked.
- [ ] Accepted, deferred, rejected, and quarantined states are auditable.
- [ ] Historical scoring updates are attributable and reversible.
- [ ] Explicit leftovers and future revisit triggers are preserved.

## Appendix B — Suggested Cross-References

- `AQSI-001-From-Answering-to-Autonomous-Questioning.md`
- `AQSI-002-Biomimetic-Question-Discovery.md`
- `AQSI-003-Multi-Granularity-Structural-Influence-Factors.md`
- `AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md`
- `AQSI-005-Directional-Question-Scoring-and-Portfolio-Selection.md`
- `AQSI-006-Question-Units-and-Exploration-Contracts.md`
- `AQSI-008-Strategic-Question-Control-Planes.md`
- `AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md`
- `AQSI-010-MVP-Architecture-and-Recursive-Evolution.md`
- `SPEC-003-Question-Relay-and-Exploration-Lifecycle.md`

## Appendix C — Figure Placement

**Fig-006 — Question Unit and Structural Relay** should appear after Section 7 or Section 8. The figure should show Question Units, Exploration Contracts, evidence/counter-evidence, relay pieces, descendant questions, historical scoring feedback, and the governance boundary. It should distinguish provenance edges from influence edges and show repeated-execution relay as an evidence-accumulation path.

---

*AQSI v1.0.0 is a theory-first, open research proposal. No experimental results or universal performance guarantees are asserted in this document.*
