# AQSI-009 — UTN and Cross-Domain Question Transfer

**Project:** Autonomous Questioning Structural Intelligence (AQSI)  
**Version:** 1.0.0 — Initial Research Framework  
**Status:** Theory-first research proposal; mechanisms and hypotheses are not empirically validated  
**License:** Apache-2.0 (repository-level)  
**Companion papers:** AQSI-001 through AQSI-008; AQSI-010  
**Related specifications:** `SPEC-001-Canonical-Question-Unit-Contract.md`, `SPEC-002-Structural-Influence-and-Scoring-Contract.md`, and `SPEC-003-Question-Relay-and-Exploration-Lifecycle.md` 

## Abstract

Scientific and engineering questions frequently share useful structures without sharing terminology, disciplines, or surface-level semantic similarity. A failure mode in a distributed system may resemble an unresolved issue in biological regulation; an experimental method from one domain may address a measurement gap in another. However, naive analogy can also manufacture false equivalences. This paper proposes a **Universal Typing and Naming (UTN)-mediated cross-domain question transfer** architecture for Autonomous Questioning Structural Intelligence (AQSI). UTN is treated as a proposed family of typed identity, naming, alignment, and semantic-contract services, not as a completed universal ontology. It allows AQSI to address heterogeneous units—questions, concepts, attributes, methods, constraints, evidence, residuals, and historical outcomes—without collapsing them into one representation. The proposed architecture distinguishes discovery of candidate correspondences from validation of their applicability, supports asymmetric and partial transfer, and preserves provenance, uncertainty, counterevidence, and explicit leftovers. It connects multi-granularity influence factors (AQSI-003), historical question intelligence (AQSI-004), portfolio selection (AQSI-005), exploration contracts (AQSI-006), structural relay (AQSI-007), and strategic governance (AQSI-008). We provide provisional contracts, algorithms, worked examples, ablation studies, and falsifiable hypotheses. No claim of improved discovery performance is made before evaluation.

**Keywords:** UTN; universal typing and naming; cross-domain question transfer; structural analogy; multi-granularity alignment; directional influence; question differential trees; historical question intelligence; structural relay; semantic contracts; collective learning.

---

## 1. From Domain-Specific Questions to Portable Research Structures

A research question is more than its natural-language sentence. It may contain a target phenomenon, a measurable attribute, an intervention method, assumptions, evidence requirements, constraints, and unresolved residuals. Two questions from distant domains may have a useful relationship at the level of one such component while differing at nearly every other level.

For example, an engineering question about detecting drift in distributed service behavior and a biomedical question about detecting changes in physiological regulation may share a *change-point detection method*. This does not imply that their causal models, data quality, or interventions are equivalent. Transfer may be justified for the method, yet unjustified for the interpretation of its output.

AQSI therefore separates three tasks:

1. **Discoverability:** find potentially relevant correspondences across domain boundaries.
2. **Applicability:** determine which components of a candidate correspondence can actually transfer under stated conditions.
3. **Accountable exploration:** formulate and test a new question, retaining evidence, failure records, and provenance.

The central proposal is that UTN-style typing and naming can make these tasks more systematic and auditable than relying exclusively on text embeddings or unconstrained LLM analogy.

### 1.1 Research question

> Can typed, multi-granularity structural alignment improve the precision, usefulness, and auditability of cross-domain question discovery while preserving open-ended exploration?

This is an empirical question. The architecture below is a candidate answer, not a demonstration.

### 1.2 Scope and non-claims

This paper does **not** claim that every domain can be reduced to a single canonical ontology; that type matches imply causal or scientific equivalence; that UTN alone discovers useful questions; that a transfer score proves research value; or that recursive question transfer guarantees open-ended improvement or ASI.

---

## 2. UTN as an Interoperability Layer, Not a Universal World Model

We use **Universal Typing and Naming (UTN)** as the name for a proposed interoperability discipline with four separable capabilities:

- **Identity:** stable, resolvable identifiers for research entities and artifacts.
- **Typing:** explicit descriptions of what a unit is, including its granularity and role.
- **Semantic contracts:** declared meaning, units, assumptions, validity range, and permissible operations.
- **Alignment and evolution:** versioned mappings between domain-specific schemas, with reviewable changes.

A UTN identifier is not itself a guarantee of truth. It identifies a claim or unit whose content and evidence must be assessed independently.

### 2.1 Example names and typed roles

The following illustrative identifiers are *not* claims about an existing deployed UTN registry:

```text
utn:aqsi/question/temperature-drift-detection@1
utn:engineering/method/change-point-detection@2
utn:biology/attribute/regulatory-stability@1
utn:aqsi/residual/unobserved-confounders@1
utn:aqsi/evidence/experiment-record-021@1
```

A useful registry must allow domain-local names and aliases. A cross-domain system should not require a biological researcher to rename every biological object according to a computer-science vocabulary.

### 2.2 Structural role and semantic type are different

A unit may have both a domain type and a research role:

| Unit | Domain type | AQSI role | Example question relevance |
|---|---|---|---|
| Change-point detector | Statistical method | Candidate transferable method | Can detect a distribution shift |
| Service latency | Engineering measurement | Observed attribute | Requires time-series monitoring |
| Physiological response | Biological measurement | Observed attribute | May contain regime shifts |
| Unmeasured confounder | Domain-specific uncertainty | Residual | Limits causal interpretation |
| Replication study | Research protocol | Evidence generator | Tests transfer robustness |

This dual description supports useful alignment without asserting that the measured phenomena are identical.

### 2.3 Minimum semantic contract

A typed unit should declare, where relevant: identity and version; type and granularity; domain and perspective; natural-language definition; measurable inputs/outputs; units or value domains; preconditions; prohibited inferences; evidence links; uncertainty; and revision history. Missing fields should remain explicitly **unknown**, not silently default to a match.

---

## 3. A Multi-Granularity Structural Model

Let a question be represented as a collection of typed, possibly nested units:

$$
Q_i = (\mathrm{id}_i, D_i, \mathcal{U}_i, \mathcal{R}_i, E_i, H_i, P_i),
$$

where \(D_i\) denotes domain context, \(\mathcal{U}_i\) typed structural units, \(\mathcal{R}_i\) relations among those units, \(E_i\) evidence, \(H_i\) historical links, and \(P_i\) provenance and permissions. This is a *logical interface*, not a requirement to materialize a complete graph.

A structural unit may be a concept, attribute, method, constraint, hypothesis, evidence item, failure mode, research question, or entire subgraph. Implementations may use LLM-extracted records, differential trees, knowledge graphs, relational tables, rule engines, or hybrid stores.

### 3.1 Typed structural correspondence

For source unit \(u \in \mathcal U_s\) and target unit \(v \in \mathcal U_t\), a candidate mapping is

$$
 m=(u,v,r,\phi,\kappa,\epsilon),
$$

where \(r\) is a proposed relation (analogy, method applicability, constraint correspondence, contradiction, etc.), \(\phi\) is a transformation or adapter, \(\kappa\) is its stated applicability contract, and \(\epsilon\) records evidence and uncertainty.

Mapping is often **partial**: only some source units have target correspondences. One-to-many, many-to-one, and hierarchical mappings should be allowed when their contracts are explicit.

### 3.2 Granularity mismatch is normal

A source *method* may align with a target *subprocedure*, while a source *failure mode* may align with a target *system-level residual*. A rigid same-level matching rule would miss both. Conversely, cross-level matching without role constraints can create arbitrary analogies. UTN provides the vocabulary for stating and testing such constraints.

### 3.3 Identity versus equivalence

Distinguish:

- `same-identity`: references to one versioned artifact;
- `equivalent-under-contract`: interchangeable for a stated purpose and conditions;
- `analogous`: shares a pattern without guaranteed interchangeability;
- `applicable-method`: a method may operate on a target with adapters;
- `incompatible`: a known constraint rules out transfer;
- `unknown`: insufficient evidence.

Treating all five as a generic similarity edge is an avoidable source of false transfer.

---

## 4. Directional Transfer and Influence

Cross-domain transfer is generally asymmetric. A method validated for one data regime may be useful in another, while the reverse mapping is invalid. A question in domain A may reveal a missing assumption in domain B without B offering a useful solution to A.

Let \(I_{s\rightarrow t}\) denote the *estimated research influence* of a source question or structural unit on a target. In general,

$$
I_{s\rightarrow t}\neq I_{t\rightarrow s}.
$$

For candidate mappings \(\mathcal M_{s,t}\), one possible score is

$$
\widehat I_{s\rightarrow t}=operatorname{Fold}_{m\in\mathcal M_{s,t}}
\bigl(w_m\,a_m\,e_m\,g_m\bigr),
$$

where \(a_m\) estimates alignment quality, \(e_m\) evidential support, \(g_m\) expected target usefulness under the declared contract, and \(w_m\) is a calibrated, policy-appropriate weight. **Fold** is a configurable aggregation operator, not necessarily a sum. Correlated evidence and duplicate mappings must be accounted for; otherwise the score can be inflated by representational redundancy.

A separate uncertainty record \(U_{s\rightarrow t}\) should accompany the estimate. Unknown mappings should not be assigned a fabricated numerical zero. Implementations may use intervals, confidence categories, probability distributions, or explicit missingness, but must state what those values mean.

### 4.1 Transfer is not merely similarity

A target question may benefit from a source *counterexample*, *failed method*, or *missing dependency*. Consequently, a low semantic similarity score does not preclude high influence; nor does high similarity imply valuable transfer. This motivates relation-specific scoring rather than a universal embedding threshold.

### 4.2 Historical calibration

The historical corpus described in AQSI-004 can provide outcomes for mappings with comparable contracts:

$$
\widehat V(q_t\mid m,\mathcal H)
=F_\theta(X_t,m,\mathcal H),
$$

where \(X_t\) is target structure and \(\mathcal H\) contains prior questions, attempted transfers, outcomes, costs, and delayed relay effects. This is a prediction to be calibrated, not an observed value. The model must account for selective exploration: historically untried transfers are not known failures.

---

## 5. Cross-Domain Question Transfer as a Lifecycle

We propose eight stages. Each stage emits a reviewable artifact and may stop, defer, or return an explicit leftover.

1. **Source registration:** identify a source question, method, residual, or evidence record and its UTN contract.
2. **Target discovery:** retrieve domains or questions with potentially compatible structural roles, including weak or unexpected matches.
3. **Candidate alignment:** propose typed mappings, adapters, and relation labels at appropriate granularities.
4. **Contract checking:** verify known preconditions, incompatible assumptions, measurement units, and authorization boundaries.
5. **Influence estimation:** score directional utility and uncertainty, using history when available.
6. **Question synthesis:** formulate a new target-domain Question Unit with falsifiable hypotheses and required evidence.
7. **Exploration:** execute under an Exploration Contract, with explicit permission for tools, data, and resource consumption.
8. **Relay and learning:** archive outcomes, counterevidence, failed alignments, unresolved residuals, and reusable mappings.

The pipeline is not necessarily linear. A failed mapping can trigger a new question about why the assumptions differ, and an exploratory result can change the type system itself.

### 5.1 Structure-first and LLM-first discovery

**Structure-first:** identify a high-potential method-to-residual or attribute-to-constraint mapping, then ask an LLM or domain expert to formulate a precise question.  
**LLM-first:** generate a candidate analogy, then require UTN mapping, contract checks, and evidence review before it is selected for expensive exploration.

Both paths should be supported. Neither is automatically more reliable.

---

## 6. Question Differential Trees and Transferable Delta

AQSI-004 proposes Question Differential Trees (QDT) for representing related questions using shared structure and differences. A cross-domain pair may be expressed provisionally as

$$
Q_s=C_s\oplus\Delta_s,\qquad
Q_t=C_t\oplus\Delta_t,
$$

where \(\oplus\) denotes a representation-specific composition operator. Cross-domain alignment attempts to identify a transferable substructure \(C^*\) and the adaptations needed to apply it in the target:

$$
T_{s\rightarrow t}=(C^*,\Delta_{s\rightarrow t},\kappa,E,U).
$$

The transfer delta \(\Delta_{s\rightarrow t}\) should explicitly include changed assumptions, new measurements, incompatible dependencies, and missing evidence. It is not simply a textual paraphrase.

### 6.1 Differential reuse and caution

If two question families share a reliable method-level Core, historical experiments on that method can guide new questions. But results on the source domain's Delta cannot be presumed to hold in the target. AQSI should learn which substructures transfer, under what conditions, and with what failure rates.

### 6.2 Residual-driven discovery

A source failure may expose a target opportunity. For instance, a method that fails under nonstationarity might prompt a new question about detecting nonstationarity before using the method. Failure records therefore constitute reusable *negative knowledge* and candidate question generators, not merely low scores.

---

## 7. A Canonical Transfer Record

The following YAML is illustrative and non-normative. It defines an auditable transfer candidate rather than a claim that the mapping is correct.

```yaml
transfer_id: "aqsi-transfer:example-001"
version: "0.1"
status: "candidate-unvalidated"
source:
  question_id: "utn:engineering/question/service-drift@1"
  unit_id: "utn:engineering/method/change-point-detection@2"
  role: "method"
target:
  question_id: "utn:biology/question/regulation-shift@1"
  unit_id: "utn:biology/attribute/regulatory-stability@1"
  role: "measurement-target"
relation:
  kind: "method-applicability-hypothesis"
  direction: "source-to-target"
  mapping_granularity: "method-to-attribute"
  adapter: "define observable time-series and sampling assumptions"
contract:
  required_conditions:
    - "target signal has interpretable temporal observations"
    - "sampling and noise assumptions are assessed"
  prohibited_inferences:
    - "change-point implies biological causation"
  unknowns:
    - "target-domain sensitivity and specificity"
evidence:
  supporting: []
  counterevidence: []
  evidence_status: "not-yet-tested"
score:
  predicted_influence: null
  uncertainty: "unquantified"
  scoring_model_version: null
provenance:
  proposed_by: "illustrative-example"
  source_license: "review-required"
  created_at: null
lifecycle:
  next_action: "domain-review-and-feasibility-test"
  authorized_to_execute: false
```

A production contract should also define data sensitivity, permitted sharing, retention, jurisdiction, and license compatibility when relevant. UTN identity must not bypass access control.

---

## 8. Three Worked Research Scenarios

These scenarios illustrate *candidate* transfer mechanisms; none represents a completed experimental result.

### 8.1 Engineering drift detection → biological regulation

**Source:** a time-series change-point detector used to identify service-performance regime changes.  
**Target:** a question about identifying shifts in a physiological measurement.  
**Transferable unit:** statistical detection method.  
**Required adaptation:** sampling frequency, noise model, baseline definition, missingness, and domain-specific interpretation.  
**Non-transferable claim:** a detected statistical change is not evidence of a specific biological mechanism.  
**New question:** *Under which measurement and sampling conditions can a change-point detector reliably flag shifts in the target signal without unacceptable false alarms?*

The value of this transfer depends on empirical detection quality and comparison with domain-native methods.

### 8.2 Software dependency graphs → research-method dependencies

**Source:** dependency analysis used to identify missing prerequisites in software builds.  
**Target:** research workflows with methods, datasets, assumptions, and evidence requirements.  
**Transferable unit:** dependency and prerequisite reasoning.  
**Limitation:** scientific evidence dependencies can be probabilistic, contested, and non-monotonic, unlike many build dependencies.  
**New question:** *Can a typed dependency representation reveal missing evidential prerequisites in a research plan more reliably than a checklist or language-model-only review?*

The transfer should be evaluated against expert-annotated omissions, not by the apparent elegance of the graph.

### 8.3 Failed optimization → strategic portfolio questioning

**Source:** repeated failures of a local optimizer under changing constraints.  
**Target:** AQSI research portfolio selection under uncertain strategic priorities.  
**Transferable unit:** the failure pattern of optimizing a proxy while neglecting constraint changes.  
**New question:** *Which observable signals should trigger reallocation from exploitation to exploratory questions when historical scores become unreliable?*

This is a failure-to-question relay. It illustrates how negative historical experience can generate useful research hypotheses without assuming that the domains have identical objective functions.

---

## 9. Cross-Domain Historical Question Intelligence

History-aware transfer should record more than a binary success/failure label. A historical transfer outcome can include:

$$
h_k=(m_k,\kappa_k,c_k,o_k,e_k,r_k,\tau_k),
$$

where \(m_k\) is the mapping, \(\kappa_k\) its contract, \(c_k\) exploration cost, \(o_k\) observed outcome, \(e_k\) evidence, \(r_k\) downstream relay, and \(\tau_k\) evaluation horizon.

A successful source-to-target transfer may be informative for another target only when the relevant applicability conditions align. UTN facilitates *conditional reuse* rather than unrestricted propagation of scores.

### 9.1 Cold start and novelty

Novel domains may have no reliable transfer history. AQSI should retain an exploration budget for uncertain mappings rather than filtering them out as low quality. Distinguish *no evidence*, *evidence of failure*, and *inapplicability*.

### 9.2 Delayed value and repeated execution

An initially unsuccessful transfer may generate a valuable residual or a later successful descendant question. Repeated experiments may also produce new reliability evidence. Historical records should therefore support delayed outcome attribution and repeated-execution relay, while avoiding double counting the same evidence.

### 9.3 Avoiding historical lock-in

Historical scores may reproduce past institutional priorities, data availability, or disciplinary biases. Calibration must include exploration propensity, subgroup/domain analysis, and tests on genuinely held-out domains.

---

## 10. Cross-Domain Scoring and Portfolio Integration

AQSI-005 considers goal-open question scoring and portfolio selection. UTN-mediated transfer contributes new candidate relations and evidence, but should not silently replace the broader portfolio objective.

For candidate target question \(q\), one illustrative decomposition is:

$$
\widehat S(q)=operatorname{Fold}\bigl(
S_{\mathrm{local}}(q),
S_{\mathrm{cross}}(q),
S_{\mathrm{history}}(q),
U(q),C(q)
\bigr),
$$

where \(S_{\mathrm{cross}}\) is a transfer-informed score, \(U\) captures uncertainty, and \(C\) captures expected exploration cost. This is a design space, not a universal additive scoring law. Any implementation must state whether its fold represents utility, ranking, risk, or a multi-objective comparison.

### 10.1 Diversity and redundancy

A portfolio may include multiple target domains but still rely on the same underlying untested method. UTN can identify that shared dependency, preventing superficial domain diversity from masquerading as methodological diversity. Conversely, the same method independently tested in distinct conditions may be valuable for robustness.

### 10.2 Strategic governance

Under AQSI-008, a Strategic Question Control Plane may set priorities, budgets, forbidden actions, evidence thresholds, and approval requirements. It can encourage transfer into a strategic domain without predetermining which specific question is discovered. A promising score does not confer authority to access restricted data or execute experiments.

---

## 11. Proposed Algorithms

### 11.1 Candidate transfer discovery

```text
function DISCOVER_TRANSFERS(source_unit, target_index, policy, history):
    source_contract = resolve_UTN(source_unit)
    candidates = retrieve_by_multiple_views(
        target_index,
        semantic_text=source_contract.description,
        typed_roles=source_contract.roles,
        structural_features=source_contract.features,
        historical_patterns=history
    )
    outputs = []
    for target_unit in candidates:
        target_contract = resolve_UTN(target_unit)
        mappings = propose_typed_mappings(source_contract, target_contract)
        for mapping in mappings:
            check = verify_known_preconditions(mapping)
            if check.has_proven_incompatibility:
                record_counterevidence(mapping, check)
                continue
            estimate = estimate_directional_influence(mapping, history)
            outputs.append({
                "mapping": mapping,
                "contract_check": check,
                "estimate": estimate,
                "unknowns": check.unresolved,
                "provenance": collect_provenance(mapping)
            })
    return rank_or_diversify(outputs, policy)
```

The `verify_known_preconditions` step may return *unknown*, not merely pass/fail. An unknown condition should be surfaced as a prerequisite question, a human review request, or a low-cost feasibility test.

### 11.2 From mapping to Question Unit

```text
function SYNTHESIZE_TARGET_QUESTION(transfer_candidate, target_domain):
    assumptions = transfer_candidate.mapping.contract.required_conditions
    unknowns = transfer_candidate.unknowns
    question = formulate_falsifiable_target_question(
        mapping=transfer_candidate.mapping,
        target_domain=target_domain,
        assumptions=assumptions,
        unknowns=unknowns
    )
    question_unit = create_question_unit(
        question=question,
        source_mapping=transfer_candidate.mapping,
        evidence_requirements=derive_evidence_requirements(question),
        provenance=transfer_candidate.provenance,
        status="candidate"
    )
    return question_unit
```

### 11.3 Learning after exploration

```text
function UPDATE_TRANSFER_HISTORY(question_unit, exploration_result):
    verify_evidence_and_permissions(exploration_result)
    record_observations_and_counterevidence(exploration_result)
    update_mapping_applicability_contracts()
    preserve_unresolved_conditions_as_explicit_leftovers()
    create_derived_questions_with_provenance()
    recalibrate_scores_only_on_eligible_evidence()
    propose_UTN_schema_revisions_for_review_if_needed()
```

These routines describe logical responsibilities. They do not prescribe a programming language, storage technology, or autonomous execution privilege.

---

## 12. UTN Evolution and Cross-Structural Co-Evolution

Cross-domain research may discover a useful relation for which no current type exists. This creates a second-order research question: *Should the typing and naming system evolve?*

A proposed loop is:

$$
\text{AQSI question discovery}
\rightarrow \text{candidate mapping}
\rightarrow \text{exploration evidence}
\rightarrow \text{UTN revision proposal}
\rightarrow \text{improved structural retrieval}.
$$

This is **cross-structural co-evolution**, a hypothesis explored further in `EXT-002-Cross-Structural-Co-Evolution.md`. It could involve UTN, differential trees, multi-granularity influence scoring, historical learning, structural relay, and governance. Benefits are not automatic: unchecked type proliferation could reduce interoperability and destabilize historical scores.

### 12.1 Type-evolution governance

A proposed new type or relation should carry a motivation, definition, examples, counterexamples, compatibility analysis, migration plan, and rollback path. Versioned mappings must preserve old research records and allow scores to be recomputed or explicitly marked incomparable after a schema change.

### 12.2 No forced ontology convergence

Distinct domains may retain incompatible but useful conceptualizations. UTN should support perspective-indexed mappings and explicit non-equivalence. Preserving plural representations is often more scientifically honest than prematurely declaring a universal Core.

---

## 13. Security, Sovereignty, and Data Governance

Cross-domain transfer creates governance risks that are not solved by typing:

- **Privacy and confidentiality:** a resolvable identifier must not expose restricted evidence or patient, enterprise, or personal data.
- **License and provenance:** reuse of methods or records must respect original licenses and attribution requirements.
- **Authority:** proposed mappings do not authorize new tool calls, data access, or external actions.
- **Adversarial mappings:** malicious or low-quality records may introduce misleading analogies or contaminate historical scoring.
- **Sensitive-domain validation:** safety-critical transfers require domain expertise, independent evidence, and appropriate oversight.
- **Human sovereignty:** institutional priorities and action boundaries remain governed by authorized actors, not inferred from similarity scores.

A transfer record should distinguish *visible metadata* from *accessible content*. The fact that a target question can be named does not imply that its underlying data may be read or relayed.

---

## 14. Failure Modes and Countermeasures

| Failure mode | Why it matters | Proposed countermeasure |
|---|---|---|
| False semantic equivalence | Similar labels conceal different mechanisms | Typed roles, preconditions, explicit non-equivalence |
| Granularity collapse | Whole-question match misses useful substructure | Multi-granularity mapping and partial transfer |
| Direction reversal | Source method may not work backward | Directional edges and separate reverse tests |
| Unsupported causal inference | Statistical pattern is mistaken for mechanism | Prohibited-inference clauses and domain review |
| Score inflation | Duplicate or correlated mappings appear independent | Evidence deduplication and dependency-aware folding |
| Unknown-as-zero | Novel domains are unfairly rejected | Explicit unknown state and exploration reserve |
| Schema drift | Historical mappings become semantically unstable | Versioning, migration, and conformance checks |
| Feedback contamination | LLM-generated assertions are treated as verified outcomes | Evidence-type separation and independent evaluation |
| Strategic capture | High scores override human authorization | SQCP policy gates and audit trails |
| Negative transfer | Adaptation costs exceed benefits | Feasibility checks, stopping criteria, and relay of failures |

Failures are not merely exceptions to hide. When documented with sufficient context, they can become reusable counterevidence and new question candidates.

---

## 15. MVP Architecture and Experimental Program

The initial implementation should be intentionally small. The research objective is to determine whether typed alignment contributes measurable value, not to deploy a universal semantic infrastructure.

### 15.1 MVP-0: Two domains, limited type vocabulary

Choose two domains with accessible, non-sensitive benchmark questions. Define a compact vocabulary for `question`, `method`, `attribute`, `constraint`, `evidence`, and `residual`. Build a small, human-reviewed mapping corpus. Compare generated questions against domain-expert judgments and actual feasibility checks.

### 15.2 MVP-1: Historical transfer memory

Add prior attempted mappings, outcomes, costs, and counterevidence. Evaluate whether history-aware screening improves useful question yield per unit cost while retaining genuinely novel candidates.

### 15.3 MVP-2: Multi-granularity and differential transfer

Enable attribute-to-method, method-to-residual, and subgraph-to-subgraph mappings. Compare with whole-question and concept-only baselines. Include partial transfers and explicit incompatibility records.

### 15.4 MVP-3: Collective relay and governed portfolio

Introduce multiple proposing/evaluating agents, versioned UTN contracts, exploration contracts, and strategic policy envelopes. Measure auditability, duplication, negative transfer, and cross-domain discovery under budget constraints.

### 15.5 Dataset and evaluation hygiene

Separate training, calibration, and evaluation by **domain family**, not just by random question split, to reduce leakage from near-duplicate examples. Keep expert evaluators blinded to system identity where feasible. Pre-register scoring criteria and report unsuccessful as well as successful transfers.

---

## 16. Baselines, Metrics, and Ablations

### 16.1 Required baselines

1. **LLM-only analogy:** prompt a language model to propose cross-domain research questions without explicit UTN mapping.
2. **Embedding retrieval:** use text similarity to retrieve candidate source questions or methods.
3. **Concept graph:** use concept-level relationships without multi-granularity roles.
4. **Typed alignment without history:** use UTN-style contracts but no learned transfer outcomes.
5. **History without typed alignment:** use historical examples and scores without UTN mapping.
6. **Full proposed pipeline:** typed multi-granularity alignment, history, contracts, and relay.

Additional ablations should remove directionality, uncertainty handling, counterevidence, and contract checks one at a time.

### 16.2 Evaluation metrics

- **Transfer precision:** fraction of proposed transfers judged applicable under predefined criteria.
- **Useful-question yield:** independently accepted, testable target questions per candidate and per exploration budget.
- **Novelty with validity:** novel questions that also meet feasibility and evidence standards; novelty alone is insufficient.
- **Negative-transfer rate:** fraction of attempted transfers that fail due to incompatible assumptions or harmful misapplication.
- **Contract violation rate:** rate of unsupported inferences, missing prerequisites, or unauthorized operations.
- **Calibration:** agreement between predicted usefulness/confidence and observed outcomes.
- **Diversity and redundancy:** distinct structural methods and target questions, adjusted for shared dependencies.
- **Delayed relay value:** useful descendant questions or reusable evidence over a declared time horizon.
- **Human review burden:** expert time required per accepted question or transfer.

Report distributions and uncertainty intervals, not only mean scores. Include computational and annotation costs.

---

## 17. Testable Hypotheses

**H1 — Multi-granularity retrieval.** Typed substructure retrieval yields more expert-accepted cross-domain transfer candidates than whole-question embedding retrieval at comparable review cost.

**H2 — Contract validity.** Explicit semantic preconditions and prohibited-inference clauses reduce negative-transfer and unsupported-equivalence rates relative to unconstrained analogy.

**H3 — Directionality.** Separately modeling source-to-target and target-to-source influence improves prediction calibration compared with symmetric relationship scoring.

**H4 — Historical reuse.** Contract-conditioned historical transfer outcomes improve question-yield-per-budget compared with an otherwise identical system lacking historical feedback.

**H5 — Novelty preservation.** Explicit unknown states and an exploration reserve recover more useful novel transfers than aggressive history-based pruning, at a stated budget cost.

**H6 — Differential transfer.** Representing transferable Core and target-specific Delta improves expert-rated applicability explanations compared with undifferentiated question rewriting.

**H7 — Provenance and auditability.** UTN-identified mappings and exploration contracts reduce the time required to trace claims to supporting or contradicting evidence.

**H8 — Co-evolution.** Governed type-revision proposals improve later transfer retrieval on held-out tasks without unacceptable schema complexity or regression in existing mappings.

**H9 — Portfolio quality.** Transfer-aware dependency detection reduces redundant research spending relative to selecting questions by independent question scores alone.

**H10 — Collective relay.** Portable transfer records improve cross-agent reuse and lower repeated unsuccessful exploration compared with free-form discussion logs.

Each hypothesis should be tested with prespecified datasets, baselines, success thresholds, and failure criteria. A null or negative result should be preserved as a research output.

---

## 18. Open Research Questions

1. What is the smallest useful UTN type vocabulary for cross-domain question discovery?
2. How can partially aligned structures be scored without overstating evidence?
3. Which relation types generalize across domains, and which must remain local?
4. Can applicability contracts be learned safely from sparse historical data?
5. How should unknown mappings be prioritized against well-supported local questions?
6. How should contradictory domain perspectives be represented and reconciled, if at all?
7. When does type-system evolution help, and when does it cause ontology fragmentation?
8. How can delayed question value be attributed across long chains of structural relay?
9. Which evaluation designs best separate genuinely useful analogies from persuasive but invalid narratives?
10. What governance prevents a cross-domain transfer service from becoming an unauthorized data bridge?

These questions connect to the repository-level `OPEN-QUESTIONS.md` and `VALIDATION-ROADMAP.md`.

---

## 19. Relationship to the AQSI Research Series

| Paper | Relationship to AQSI-009 |
|---|---|
| `AQSI-001-From-Answering-to-Autonomous-Questioning.md` | Motivates autonomous question discovery as a research direction |
| `AQSI-002-Biomimetic-Question-Discovery.md` | Supplies association-, gap-, residual-, and relay-driven candidate sources |
| `AQSI-003-Multi-Granularity-Structural-Influence-Factors.md` | Supplies typed, directional, multi-granularity influence mechanisms |
| `AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md` | Supplies historical feedback and differential representation |
| `AQSI-005-Directional-Question-Scoring-and-Portfolio-Selection.md` | Uses transfer-informed relations in question ranking and portfolio choice |
| `AQSI-006-Question-Units-and-Exploration-Contracts.md` | Defines portable question artifacts and authorized exploration |
| `AQSI-007-Question-Structural-Relay-and-Collective-Learning.md` | Carries transfer records, outcomes, and explicit leftovers across agents |
| `AQSI-008-Strategic-Question-Control-Planes.md` | Governs priorities, resources, and authority for cross-domain research |
| `AQSI-010-MVP-Architecture-and-Recursive-Evolution.md` | Integrates the mechanisms into staged system evaluation and recursive improvement |

The proposed interfaces also relate to the broader SI research vocabulary—SIF localization, UCPSF scoring and folding, MDI directional intuition, UIERU portable relay units, and SRSI evaluator governance—without presuming those projects already provide validated interoperable runtimes.

---

## 20. Conclusion

UTN-mediated cross-domain question transfer is proposed as a bridge between heterogeneous domain knowledge and accountable autonomous research exploration. Its central design choice is to transfer **typed, partial, directional structural relationships** rather than to treat whole questions as interchangeable strings. This enables a research system to ask not merely whether two domains *sound similar*, but whether a particular method, constraint, residual, or evidence pattern may be applicable under explicit conditions.

The architecture combines multi-granularity mapping, semantic contracts, historical transfer outcomes, question differential trees, directional scoring, and structural relay. It also insists on uncertainty, counterevidence, policy conformance, and human review where appropriate. The expected benefits—better question discovery, more efficient reuse, and more reliable collective learning—remain hypotheses. The next step is controlled experimentation against simpler retrieval and analogy baselines, with negative results and explicit leftovers treated as valuable research artifacts.

**The goal is not universal equivalence across domains. It is disciplined discovery of where, how, and under which conditions knowledge can travel.**

---

## Appendix A. Minimal UTN Alignment Conformance Checklist

A transfer candidate is *record-complete* only if it has:

- [ ] Source and target identifiers, types, granularity, and versions.
- [ ] A directional relation label and mapping rationale.
- [ ] A declared transformation or explicit `none`/`unknown`.
- [ ] Required preconditions, known incompatibilities, and unresolved assumptions.
- [ ] Evidence provenance and counterevidence links, even when empty.
- [ ] A scoring model identifier or explicit unscored status.
- [ ] An uncertainty representation with documented semantics.
- [ ] Data-access, license, and authorization constraints.
- [ ] A lifecycle state and next review or exploration action.
- [ ] A revision trail for mappings and type changes.

Record completeness does not imply scientific validity.

## Appendix B. Suggested Transfer-Relation Vocabulary

| Relation | Directional? | Key validation question |
|---|---|---|
| `method-applicable-to` | Yes | Does the target satisfy method preconditions? |
| `constraint-maps-to` | Usually | Are the constraints semantically comparable? |
| `attribute-corresponds-to` | Context-dependent | Are definitions, units, and measurement regimes compatible? |
| `residual-suggests-question` | Yes | Is the derived question testable and relevant? |
| `counterexample-to` | Yes | Does the counterexample challenge the target claim? |
| `evidence-supports` | Yes | Is the evidence admissible for the target inference? |
| `analogous-under-contract` | Often | What is shared, and what is explicitly not shared? |
| `equivalent-under-contract` | Usually symmetric only within a contract | Are substitutions valid for the specified operation? |
| `unknown-relationship` | Unresolved | What minimal evidence would clarify it? |

This vocabulary is provisional and intentionally extensible.

## Appendix C. Publication and Validation Notes

- **Theory-first release:** this paper specifies research interfaces and hypotheses, not an executable UTN service.
- **No fabricated validation:** worked scenarios and algorithms are illustrative; no benchmark results are asserted.
- **No invented DOI or external citations:** publication identifiers and formal references should be added only after verification.
- **Collective Learning Friendly:** implementations should publish schemas, evaluation protocols, negative results, and reusable transfer records when permissions permit.
- **Suggested figure:** `figures/Fig-008-UTN-Cross-Domain-Relay-and-RSI.png`, illustrating source structures, typed alignment, contract checks, target question synthesis, exploration, and feedback into UTN and AQSI.
