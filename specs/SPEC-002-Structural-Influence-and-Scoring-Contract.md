# SPEC-002 — Structural Influence and Scoring Contract

**Project:** Autonomous Questioning Structural Intelligence (AQSI)  
**Version:** 1.0.0 (research specification)  
**Status:** Proposed; not an implemented, certified, or empirically validated standard  
**Scope:** Interoperable contracts for multi-granularity directional question influence, historical assessments, score folding, goal-open ranking, portfolio decisions, and evidence-preserving feedback.

## Abstract

This specification defines a proposed contract between AQSI question producers, structural influence estimators, historical question intelligence (HQI) services, scoring/folding engines, portfolio selectors, and structural relay consumers. Its central premise is that influence between research questions may arise from typed relationships among heterogeneous structural factors—concepts, attributes, methods, constraints, evidence, residuals, and transfer points—rather than from concept-to-concept similarity alone. The contract preserves direction, scale, provenance, applicability, uncertainty, unknown relationships, and evaluation perspective. It separates estimates of research potential from verified outcomes and separates portfolio selection from authorization to execute. Normative conformance checks and illustrative records are provided, without asserting empirical superiority over alternative scoring approaches.

## 1. Purpose and scope

AQSI-003 proposes multi-granularity influence factors; AQSI-004 describes historical question intelligence; AQSI-005 develops goal-open scoring and portfolio selection. This specification defines their **interoperability boundary**, not a mandatory scoring algorithm.

A conforming system can exchange:

1. Typed factor and alignment references, including UTN-compatible identifiers.
2. Directed question-pair influence assessments with explicit uncertainty.
3. Historical prior assessments with provenance and outcome distinctions.
4. Documented folding and calibration procedures.
5. Ranking and portfolio decisions with costs, constraints, and audit trails.
6. Subsequent evidence, counterevidence, delayed relay value, and explicit leftovers.

**Out of scope:** a universally correct utility function; a required LLM, embedding model, graph engine, or optimizer; proof of human-level intuition; automatic execution authorization; and claims of recursive self-improvement without measured evidence.

## 2. Normative language and definitions

**MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** indicate requirements for an implementation claiming conformance to this *proposed research contract*.

- **Question Unit (QU):** a persistent research question defined by `aqsi.question-unit/1.0` in SPEC-001.
- **Structural factor:** a typed, identifiable element of a question representation; factor granularity is not restricted to concepts.
- **Directional influence:** an estimate of how exploring one question may affect the potential exploration of another, under an identified perspective and context.
- **Factor relation:** a typed, directed, evidence-qualified relationship between two structural factors.
- **Assessment:** a versioned, provenance-bearing estimate or observation, not an intrinsic immutable property of a QU.
- **Unknown:** an absence of sufficient basis for an estimate; distinct from measured zero.
- **Folding:** a declared transformation from multiple factor-level observations or scores into an aggregate assessment.
- **Goal-open:** no externally specified single target question is required for baseline relational scoring; it does not mean absence of values, budgets, or governance.
- **Portfolio:** a set of selected questions with resource allocations and explicit constraints.
- **Residual/leftover:** a retained uncertainty, unaddressed subproblem, failure, or structural gap.

## 3. Design principles and invariants

**S-INV-01 — Direction is explicit.** `I(q_i → q_j)` and `I(q_j → q_i)` are independent assessments. Symmetry MAY be a tested special case but MUST NOT be assumed.

**S-INV-02 — Unknown is not zero.** Missing, unassessed, and insufficient-evidence relations MUST retain an explicit unknown state. A zero score is valid only when a specified procedure supports it.

**S-INV-03 — Typed multi-granularity input.** A scorer MUST accept, or explicitly declare unsupported, factor kinds beyond concept nodes. Unsupported factors MUST NOT be silently discarded when their omission materially changes interpretation.

**S-INV-04 — Provenance and scale.** Every reported numeric score MUST identify its scale, orientation, method/version, perspective, time, and evidence basis or explicit evidence limitation.

**S-INV-05 — Estimate is not observation.** Predicted influence, historical prior, observed outcome, and independent verification MUST be distinguishable.

**S-INV-06 — No double-counting by default.** A folding implementation MUST document dependencies or shared sources among contributing factors and SHOULD apply a dependency-aware adjustment or report uncorrected overlap.

**S-INV-07 — Selection is not authorization.** Ranking or selection MUST NOT imply permission to perform an experiment, access data, or change policies.

**S-INV-08 — Reversible learning.** Historical negative evidence MAY reduce priority but MUST NOT automatically make a question permanently inadmissible; deferral and revisit conditions SHOULD be retained.

## 4. Logical objects and references

This specification defines logical records, not a mandated serialization. JSON, YAML, relational schemas, and graph records MAY implement them if they preserve semantics.

| Object | Suggested contract identifier | Purpose |
|---|---|---|
| `FactorReference` | `aqsi.factor-ref/1.0` | Link a QU to a typed structural factor |
| `FactorRelation` | `aqsi.factor-relation/1.0` | Record a typed, directed, qualified relationship |
| `InfluenceAssessment` | `aqsi.influence-assessment/1.0` | Evaluate an ordered question pair |
| `HistoricalAssessment` | `aqsi.historical-assessment/1.0` | Estimate prior potential from archived question experience |
| `FoldingManifest` | `aqsi.folding-manifest/1.0` | Declare normalization, aggregation, and dependency handling |
| `QuestionScore` | `aqsi.question-score/1.0` | Aggregate pair influence and other explicitly separated inputs |
| `PortfolioDecision` | `aqsi.portfolio-decision/1.0` | Select questions subject to policy and resources |
| `OutcomeFeedback` | `aqsi.outcome-feedback/1.0` | Feed evidence and relay outcomes back into assessment |

Each object MUST include a contract identifier, a stable record identifier, a revision or immutable version, and provenance. References to QUs MUST resolve to stable `question_id` values as specified in SPEC-001; a consumer MAY operate with unresolved references if it marks them unresolved and does not invent their content.

## 5. Factor references and structural relations

### 5.1 FactorReference requirements

A `FactorReference` MUST identify `factor_id`, `question_id`, `kind`, and `type_ref`; it MUST provide a `value_ref` or an explicitly typed value. It SHOULD carry `granularity`, `domain_ref`, `applicability`, and provenance. Examples of `kind` include `concept`, `attribute`, `method`, `constraint`, `evidence`, `counterevidence`, `residual`, `transfer_point`, `relationship`, and `question`.

A factor's UTN reference SHOULD specify namespace and type semantics. A registry resolution failure MUST NOT be silently converted into a confident semantic match. A factor MAY participate in multiple relations, including relations across kinds and levels of abstraction.

### 5.2 FactorRelation requirements

A relation MUST specify:

- `source_factor_ref` and `target_factor_ref` as an ordered pair;
- `relation_type_ref` with declared semantics (e.g., `enables`, `constrains`, `transfers_to`, `contradicts`, `shares_method_with`);
- `alignment_ref` or `alignment_status` when cross-domain mapping is involved;
- `evidence_refs` or explicit `evidence_status: insufficient`;
- `applicability` and `uncertainty_status`;
- provenance and assessment time.

A relation MAY connect factors of unequal granularity. A proposed analogy MUST NOT be labeled as established equivalence merely because the terms are lexically similar. Contradictory relations SHOULD be retained as separate evidence-bearing records until adjudicated.

## 6. Directional influence semantics

For a question pair `(q_i, q_j)` under context `c` and perspective `p`, define an **illustrative** estimator:

\[
\widehat I_{p,c}(q_i\rightarrow q_j)
=\operatorname{Fold}_{\phi,p,c}\left(\left\{
 w_{ab,p,c}\,R_{p,c}(h_{ia}\rightarrow h_{jb})
\right\}_{(a,b)\in E_{ij}}\right).
\]

Here `h_ia` and `h_jb` are heterogeneous typed factors, `E_ij` is the set of assessed cross-question factor pairs, `R` is a directed relation assessment, and `φ` identifies the folding procedure. This is a **design template**, not a universal metric or a validated equation. Implementations MAY use other estimators if they satisfy the record and audit contracts.

### 6.1 Required semantics

An `InfluenceAssessment` MUST contain:

| Field | Required | Meaning |
|---|---|---|
| `contract`, `assessment_id`, `revision` | Yes | Type and immutable/revisable identity |
| `source_question_id`, `target_question_id` | Yes | Ordered question pair |
| `perspective_ref`, `context_ref` | Yes | Perspective and evaluation context; explicit `unspecified` allowed |
| `status` | Yes | `estimated`, `observed`, `unknown`, `not_applicable`, or `invalidated` |
| `value` | Conditional | Numeric only for a scored assessment |
| `scale_ref`, `orientation` | Conditional | Required when `value` is numeric |
| `uncertainty` | Yes | Interval, distribution, calibrated confidence, or `unquantified` |
| `factor_relation_refs` | Yes | May be empty only with explicit rationale |
| `folding_manifest_ref` | Conditional | Required when multiple factors are aggregated |
| `evidence_refs`, `provenance` | Yes | Empty evidence allowed only when limitation is declared |
| `created_at`, `method_ref` | Yes | Time and scorer version |

`not_applicable` means a relationship was assessed as outside declared scope; it is not equivalent to `unknown` or a numeric zero. An invalidated assessment MUST remain traceable rather than being overwritten without history.

### 6.2 Negative and positive influence

A signed scale MAY represent inhibitory and enabling influence, provided its meaning is declared. A scale in `[0,1]` MAY instead represent nonnegative estimated transfer potential. A consumer MUST NOT combine signed and nonnegative scores without an explicit conversion manifest.

### 6.3 Self-influence and pair coverage

Self-pairs MAY be excluded from a question-group influence sum by default, but this exclusion MUST be declared. Pair coverage MUST be reported: `assessed_pairs`, `unknown_pairs`, `not_applicable_pairs`, and `eligible_pairs`. A sparse graph MUST NOT be presented as a complete influence matrix.

## 7. Historical Question Intelligence contract

Historical assessments refer to outcomes and prior experiences from AQSI-004. They MUST NOT be represented as verified outcomes unless supported by independent observations.

A `HistoricalAssessment` MUST include `target_question_id`, `history_snapshot_ref`, `retrieval_method_ref`, `scorer_version`, `score_status`, `uncertainty`, and `provenance`. Numeric scores MUST additionally specify `value`, `scale_ref`, and `orientation`. It SHOULD identify matched historical question families, differential-tree core/delta relationships, temporal scope, and observed failure/success categories.

### 7.1 Historical outcome categories

Suggested outcome states include `supported`, `partially_supported`, `refuted`, `inconclusive`, `not_executed`, and `unverified_model_output`. An implementation MUST NOT treat `not_executed` as failure or `unverified_model_output` as experimentally supported.

### 7.2 Transfer and selection bias

When a historical score is transferred across domains, the assessment SHOULD record `source_domain_ref`, `target_domain_ref`, `alignment_ref`, `transfer_assumptions`, and a confidence or uncertainty qualification. Training/evaluation procedures MUST identify whether historical labels were collected only from previously selected questions; a validation report SHOULD assess this selection bias and distribution shift.

### 7.3 Deferred and novel questions

A low historical estimate MAY support `defer`, `request_more_evidence`, or `revisit_on_trigger`. A scorer SHOULD provide a cold-start or novelty route for questions unlike its archive. An implementation MUST NOT conflate lack of precedent with evidence of low value.

## 8. Folding and normalization contract

A `FoldingManifest` MUST specify:

1. `manifest_id`, `version`, `operator_ref`, and `operator_parameters`;
2. input score types, expected scales, and score orientation;
3. normalization or calibration transforms and their reference data;
4. treatment of missing, unknown, and not-applicable inputs;
5. weighting, dependency handling, and overlap disclosures;
6. uncertainty propagation or a reason it cannot be quantified;
7. output scale, perspective, and reproducibility metadata.

UCPSF-inspired operators MAY be used, but no specific operator is mandatory. A folding result MUST NOT silently replace unknown inputs with zero. Imputation MAY be used only if marked as imputation and accompanied by sensitivity analysis or a disclosed uncertainty treatment.

### 8.1 Dependency and duplicated evidence

If two factors derive from the same experiment, citation, or relay chain, they are not automatically independent evidence. A folding engine SHOULD identify shared evidence identifiers and document whether it de-duplicates, down-weights, models dependence, or merely reports possible overlap. A result with unresolved overlap MUST be labeled accordingly.

### 8.2 Uncertainty-preserving output

An aggregate MAY be an interval, distribution, ranked category, or point estimate with uncertainty metadata. A point estimate without calibrated uncertainty MUST carry `uncertainty: unquantified`; it MUST NOT be described as statistically confident.

## 9. Goal-open group scoring

A basic AQSI-005 group score is:

\[
S_{\mathrm{out}}(q_i\mid Q,p,c)=\sum_{j\in Q\setminus\{i\}}\widehat I_{p,c}(q_i\rightarrow q_j).
\]

This baseline expresses estimated outgoing structural influence on other questions in a candidate group. It is **not** automatically a measure of truth, scientific importance, or expected breakthrough. A group score MUST identify the candidate-set snapshot `Q`, perspective, normalization/folding manifest, pair coverage, and treatment of unknowns.

Implementations MAY report incoming influence, reciprocal influence, centrality, uncertainty-adjusted scores, or cost-normalized scores as additional metrics. These MUST have distinct metric identifiers; they MUST NOT be substituted for `S_out` without disclosure.

### 9.1 Group-size comparability

Raw sums depend on candidate-set size and coverage. Comparisons across groups SHOULD normalize by a documented denominator or report coverage and group size alongside scores. Unknown pairs MUST remain visible even if a policy chooses to rank only assessed relations.

### 9.2 History and influence are separable

A combined score MAY be defined as an illustrative policy-specific function:

\[
V_p(q_i)=F_p\big(S_{\mathrm{out}}(q_i), H(q_i), C(q_i), U(q_i), R(q_i)\big),
\]

where `H` is historical assessment, `C` cost, `U` uncertainty, and `R` other declared constraints or risks. `F_p` MUST be identified by version and parameters. The component scores SHOULD remain independently inspectable; a combined number MUST NOT conceal incompatible scales or double-counted historical evidence.

## 10. QuestionScore record

A `QuestionScore` MUST contain `question_id`, `candidate_set_ref`, `metric_ref`, `score_status`, `perspective_ref`, `scorer_ref`, `timestamp`, and `provenance`. Numeric scores require `value` and `scale_ref`. It SHOULD include `pair_coverage`, `influence_assessment_refs`, `historical_assessment_refs`, `folding_manifest_refs`, `uncertainty`, `cost_estimate_ref`, and `limitations`.

If any mandatory input is unavailable, the engine MAY return a partial assessment; it MUST mark partial status and enumerate missing inputs. It MUST NOT report a partial aggregate as complete.

## 11. Portfolio selection and policy boundary

A `PortfolioDecision` MUST specify the candidate-set snapshot, selected and deferred question IDs, selection algorithm/version, objective components, resource assumptions, policy references, constraint outcomes, decision timestamp, and rationale or auditable score references.

Illustrative constrained selection:

\[
\max_{P\subseteq Q}\;\operatorname{Value}_{p}(P)
\quad\text{subject to}\quad
\operatorname{Cost}(P)\le B,\;P\in\mathcal F_p.
\]

`B` is a declared budget and `𝔽_p` is the feasible set under policy `p`. `Value_p` MAY account for complementarity, redundancy, diversity, replication, and strategic priorities. No particular objective is mandated. Portfolio selection MUST NOT itself grant execution permission.

### 11.1 Deferral and exploration reserves

A decision SHOULD preserve explicit reasons for deferral, evidence gaps, revisit triggers, and any reserved exploration capacity for uncertain or unprecedented questions. A hard exclusion MUST identify its governing policy or safety constraint rather than presenting exclusion as a scientific score.

### 11.2 Strategic control plane

Human-authorized policy MAY set strategic research directions, budget envelopes, risk boundaries, and portfolio balance. The scoring contract MUST record the active policy version when policy influences ranking or selection. AI-generated policy recommendations MUST be represented as proposals, not as authorized policy changes. See AQSI-008 and SPEC-004.

## 12. Outcome feedback and structural relay

An `OutcomeFeedback` record MUST link `question_id`, `exploration_ref`, `observation_status`, `evidence_refs`, `counterevidence_refs`, `outcome_time`, and `provenance`. It SHOULD identify direct results, newly generated QUs, transferred methods, unresolved leftovers, costs, and delayed downstream value.

Feedback MUST distinguish:

- immediate evidence about the explored question;
- later effects on descendant or neighboring questions;
- replication outcomes, including repeated-execution relay;
- revised scoring-model estimates;
- unsupported claims or unverified model-generated hypotheses.

A scoring model update SHOULD retain the training-data snapshot, update procedure, evaluation report, and rollback reference. Recursive changes to the scorer or folding operator MUST NOT bypass governance and conformance checks.

## 13. Illustrative YAML records (non-normative)

The following examples demonstrate interoperable semantics, not an implemented schema validator. URNs and values are fictional.

```yaml
contract: aqsi.factor-relation/1.0
relation_id: urn:aqsi:relation:demo-17
revision: 1
source_factor_ref: urn:aqsi:factor:q-a:method-1
target_factor_ref: urn:aqsi:factor:q-b:residual-2
relation_type_ref: urn:utn:relation:may-enable-resolution
alignment_status: provisional
applicability:
  domain_refs: [urn:utn:domain:software, urn:utn:domain:research-methods]
evidence_refs: [urn:aqsi:evidence:demo-3]
evidence_status: hypothesis_only
uncertainty_status: unquantified
provenance:
  producer_ref: urn:aqsi:agent:illustrative-scorer
  created_at: '2026-10-28T00:00:00Z'
```

```yaml
contract: aqsi.influence-assessment/1.0
assessment_id: urn:aqsi:assessment:demo-iab
revision: 1
source_question_id: urn:aqsi:question:q-a
target_question_id: urn:aqsi:question:q-b
perspective_ref: urn:aqsi:perspective:method-transfer
context_ref: urn:aqsi:context:demo-portfolio
status: estimated
value: 0.62                # illustrative, not an empirical measurement
scale_ref: urn:aqsi:scale:nonnegative-unit-interval
orientation: higher_means_more_estimated_influence
uncertainty: unquantified
factor_relation_refs: [urn:aqsi:relation:demo-17]
folding_manifest_ref: urn:aqsi:folding:demo-v1
evidence_refs: [urn:aqsi:evidence:demo-3]
method_ref: urn:aqsi:method:illustrative-folding-v1
created_at: '2026-10-28T00:00:00Z'
provenance:
  producer_ref: urn:aqsi:agent:illustrative-scorer
  limitation: hypothesis-based input; not calibrated
```

```yaml
contract: aqsi.influence-assessment/1.0
assessment_id: urn:aqsi:assessment:demo-iba
revision: 1
source_question_id: urn:aqsi:question:q-b
target_question_id: urn:aqsi:question:q-a
perspective_ref: urn:aqsi:perspective:method-transfer
context_ref: urn:aqsi:context:demo-portfolio
status: unknown
value: null
uncertainty: unquantified
factor_relation_refs: []
evidence_refs: []
method_ref: urn:aqsi:method:illustrative-folding-v1
created_at: '2026-10-28T00:00:00Z'
provenance:
  producer_ref: urn:aqsi:agent:illustrative-scorer
  limitation: no assessed reverse-direction relationship
```

```yaml
contract: aqsi.folding-manifest/1.0
manifest_id: urn:aqsi:folding:demo-v1
version: 1
operator_ref: urn:aqsi:operator:weighted-mean
operator_parameters:
  weights: evidence-qualified
input_scale_refs: [urn:aqsi:scale:nonnegative-unit-interval]
orientation: higher_means_more_estimated_influence
normalization: none
unknown_policy: propagate_and_report
not_applicable_policy: exclude_with_coverage
shared_evidence_policy: flag_overlap
uncertainty_policy: unquantified
output_scale_ref: urn:aqsi:scale:nonnegative-unit-interval
perspective_ref: urn:aqsi:perspective:method-transfer
reproducibility:
  procedure_version: illustrative-v1
  data_snapshot_ref: urn:aqsi:data:demo-snapshot
```

## 14. Worked directional scoring example

Consider three hypothetical QUs, `qA`, `qB`, and `qC`, in one candidate-set snapshot. An illustrative scorer returns:

| Ordered pair | Status | Value | Interpretation |
|---|---|---:|---|
| `qA → qB` | estimated | 0.7 | Potential method transfer |
| `qA → qC` | estimated | 0.3 | Potential evidence reuse |
| `qB → qA` | unknown | — | Not assessed; **not** zero |
| `qB → qC` | estimated | 0.5 | Potential constraint insight |
| `qC → qA` | estimated | 0.2 | Possible counterexample transfer |
| `qC → qB` | estimated | 0.4 | Potential residual connection |

Using a simple sum over *assessed* outgoing pairs gives `qA: 1.0 (2/2 assessed)`, `qB: 0.5 (1/2 assessed)`, and `qC: 0.6 (2/2 assessed)`. This is **not** a complete, directly comparable ranking: `qB` has an unknown outgoing pair. A conforming scorer MUST disclose the partial coverage, and a portfolio policy MAY choose additional assessment before ranking. No conclusion about actual scientific value follows from these illustrative values.

## 15. Conformance requirements

A producer claiming `SPEC-002` conformance MUST satisfy applicable requirements below. Consumers MUST preserve the semantics of any records they read or transform. Scorers and selectors are assessed against their respective roles.

| ID | Requirement | Negative test |
|---|---|---|
| S-001 | Ordered source/target IDs for every influence assessment | Pair stored without direction |
| S-002 | Unknown, zero, and not-applicable are distinct | Missing pair silently filled with zero |
| S-003 | Every numeric score declares scale and orientation | Score `0.8` with no scale |
| S-004 | Factor kinds, types, and provenance retained | Method factor collapsed into untyped concept |
| S-005 | Cross-domain alignment status explicit | Lexical similarity asserted as equivalence |
| S-006 | Scorer version, context, perspective, and time retained | Score cannot be reproduced or attributed |
| S-007 | Folding manifest declares normalization and missing-data handling | Hidden averaging with undocumented inputs |
| S-008 | Shared evidence handled or disclosed | Same experiment counted as independent support twice |
| S-009 | Predicted value separate from observed outcome | LLM prediction marked experimentally verified |
| S-010 | Historical retrieval snapshot and selection-bias limits recorded | Archive-based estimate without history provenance |
| S-011 | Partial pair coverage disclosed in group scoring | Sparse matrix labeled complete |
| S-012 | Group-size and candidate-set context reported | Raw sums compared across incompatible sets |
| S-013 | Portfolio decision includes budget, policy, and rationale | Unexplained selected set |
| S-014 | Selection does not imply execution authorization | High-score question triggers unauthorized action |
| S-015 | Deferred questions retain reason and revisit pathway | Low-score item permanently deleted without policy |
| S-016 | Outcome feedback links evidence and relay descendants | Success claim with no source record |
| S-017 | Model updates preserve lineage and validation status | Scorer silently replaced after feedback |
| S-018 | Invalidated or superseded assessments remain auditable | Old score overwritten with no revision history |

### 15.1 Suggested conformance test suite

- **T-DIR:** Reverse an ordered pair and verify no inherited score.
- **T-UNK:** Delete a factor relation and verify `unknown`, not `0`.
- **T-SCALE:** Attempt to fold incompatible scales without a transform; expect rejection or explicit failure.
- **T-DEP:** Supply two factors supported by one evidence record; verify overlap disclosure.
- **T-HIST:** Supply a cold-start question; verify uncertainty and nonpermanent deferral behavior.
- **T-COVER:** Compare sparse and complete influence matrices; verify coverage labels.
- **T-POL:** Select a high-score question under a restricted policy; verify no execution authorization.
- **T-RELAY:** Add a delayed descendant outcome; verify lineage and assessment revision.

A conformance report SHOULD specify test data, procedure, system version, pass/fail status, exceptions, and whether the test was static or executed. **No test results are claimed in this document.**

## 16. Evaluation and falsifiable research hypotheses

The following are hypotheses, not findings:

- **H-S02-01:** Multi-granularity typed factor scoring improves the discovery of useful cross-domain question links relative to concept-only baselines on matched datasets.
- **H-S02-02:** Explicit directional influence outperforms forced-symmetric scoring when ground-truth transfer effects are asymmetric.
- **H-S02-03:** Treating unknown relations explicitly reduces overconfident rankings compared with zero-imputation.
- **H-S02-04:** Historical priors reduce redundant exploration cost without materially suppressing high-value novel questions under a calibrated exploration reserve.
- **H-S02-05:** Dependency-aware folding yields better-calibrated uncertainty than naïve independent-factor aggregation.
- **H-S02-06:** Portfolio selection with complementarity and budget constraints produces more validated downstream research value per unit cost than top-k single-score ranking.
- **H-S02-07:** Evidence-preserving delayed relay feedback improves later question selection versus immediate-outcome-only learning.

A proposed evaluation SHOULD compare: concept-only versus multi-granularity inputs; symmetric versus directional relations; zero-imputation versus unknown-aware scoring; no-history versus HQI; naïve versus dependency-aware folding; top-k versus portfolio optimization; and immediate-only versus delayed-relay feedback. Use temporally separated data, held-out domains, blinded expert review where feasible, calibration measures, cost accounting, and predefined failure thresholds. Report negative results and uncertainty, including sensitivity to question-group construction.

## 17. Security, governance, and research integrity

Question scoring can concentrate attention, shape funding decisions, and create incentives to game a metric. A conforming implementation SHOULD maintain audit trails for policy versions, score overrides, dataset access, and model updates. It SHOULD monitor feedback loops in which previously favored questions dominate the historical archive and thereby receive inflated future scores. Private evidence MUST respect access controls; a score or reference MUST NOT authorize disclosure. Research policies MAY require human review for sensitive domains, costly experiments, or external actions. No model-generated score should be treated as an objective scientific fact.

## 18. Compatibility and versioning

Contract versions MUST be explicit. A minor revision SHOULD preserve the meaning of existing fields; incompatible semantic changes require a new major contract identifier. Extensions MUST be namespaced and MUST NOT redefine core field meanings. When importing legacy scores, an adapter SHOULD identify missing direction, scale, provenance, and unknown semantics; it MUST NOT fabricate absent information. SPEC-001 Question Unit identifiers remain the canonical references; SPEC-003 defines exploration and relay lifecycle interfaces, while SPEC-004 defines control-plane authorization and policy conformance.

## 19. Open questions

1. Which factor relation types generalize across domains without excessive ontology overhead?
2. How can uncertainty be calibrated when influence outcomes are delayed or indirect?
3. How should candidate-set construction affect the interpretation of outgoing influence?
4. Can dependency-aware folding remain computationally efficient on large heterogeneous graphs?
5. Which historical transfer features are robust under domain shift?
6. How can novelty be protected from the self-reinforcing bias of past selection?
7. What measurable downstream outcomes best represent research value without collapsing it into a single proxy?
8. When should an unknown relation trigger further assessment rather than deferral?
9. How should UTN type evolution affect historical score comparability?
10. How can multi-perspective portfolio policies expose conflicts without concealing them in a single aggregate score?

## 20. Relationship to AQSI research and specifications

- **AQSI-003 — Multi-Granularity Structural Influence Factors:** proposed factor-level model and directional relation semantics.
- **AQSI-004 — Historical Question Intelligence and Differential Trees:** historical retrieval, scoring priors, and failure/feedback memory.
- **AQSI-005 — Directional Question Scoring and Portfolio Selection:** goal-open baseline, folding, and portfolio logic.
- **AQSI-006 — Question Units and Exploration Contracts:** separation of question identity, expression, and exploration permission.
- **AQSI-007 — Question Structural Relay and Collective Learning:** evidence, delayed effects, and cross-agent relay.
- **AQSI-008 — Strategic Question Control Planes:** human-directed research policy and resource governance.
- **AQSI-009 — UTN and Cross-Domain Question Transfer:** typed alignment and transfer uncertainty.
- **SPEC-001 — Canonical Question Unit Contract:** authoritative logical QU identity and assessment references.
- **SPEC-003 — Question Relay and Exploration Lifecycle:** proposed downstream lifecycle interface.
- **SPEC-004 — Control Plane and Policy Conformance:** proposed authorization and policy interface.

## 21. Conclusion

This specification proposes a verifiable boundary between structural influence estimation, historical learning, score folding, and research portfolio selection. Its primary contribution is not a claim that one formula finds the best scientific questions; it is an interoperable and falsifiable **contract** that preserves typed multi-granularity structure, direction, uncertainty, provenance, policy context, and delayed relay feedback. That contract permits competing algorithms to be compared without silently changing what their scores mean. Whether it improves autonomous question discovery remains an empirical question for future implementation and evaluation.

---

**Research status:** Proposed specification. Examples and scores are illustrative. No runtime implementation, certification, benchmark result, or scientific breakthrough is asserted.  
**Recommended repository path:** `specs/SPEC-002-Structural-Influence-and-Scoring-Contract.md`  
**License preference for repository:** Apache-2.0.
