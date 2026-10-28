# AQSI-003 — Multi-Granularity Structural Influence Factors

**Autonomous Questioning Structural Intelligence (AQSI)**  
**Version:** 1.0.0 — Research framework  
**Status:** Proposed architecture and testable hypotheses; not an empirically validated algorithm  
**Scope:** Structural representation, directional influence estimation, cross-domain transfer, and question discovery

## Abstract

Autonomous question discovery requires more than matching whole questions or measuring semantic similarity between named concepts. A question may become valuable because an attribute of one concept corresponds to a constraint of another, a method in one domain addresses a residual in another, or a historical failure reveals a transferable structural pattern. This paper proposes **Multi-Granularity Structural Influence Factors (MGSIF)**: a typed, evidence-aware framework for discovering and scoring relationships among concepts, attributes, methods, substructures, questions, residuals, observations, and relay records. It combines heterogeneous structural representations, Universal Typing and Naming (UTN)-style alignment, directional relationship scoring, historical question feedback, and configurable folding. The framework supports both question-to-question evaluation and *structure-first* generation of candidate questions. Its central hypothesis is that typed cross-granularity relationships can identify productive research connections missed by whole-question semantic similarity alone. The proposal specifies contracts, algorithms, failure modes, and falsifiable comparisons without claiming demonstrated superiority.

**Keywords:** autonomous questioning; structural intelligence; multi-granularity influence; directional scoring; UTN; cross-domain transfer; question differential trees; historical question intelligence; structural relay.

---

## 1. Problem Statement and Research Position

A conventional question-ranking pipeline often treats a question as a text string, embeds it, retrieves neighbors, and scores its novelty or relevance. Such methods are useful baselines, but can miss structurally important connections: a *method* in one question may resolve a *missing dependency* in another even if their overall texts are dissimilar. Conversely, high textual similarity may indicate redundant exploration rather than valuable transfer.

AQSI asks whether a common, typed relationship layer can expose these interactions without committing to a single universal representation or a fixed research objective. **Influence** here means an estimated, task-relevant potential for one structural unit to inform, constrain, enable, challenge, or redirect another. It is not necessarily causal influence, semantic similarity, or realized scientific value.

This paper proposes a research interface, not a new proven law of association. The architecture is designed to accept language models, differential trees, graphs, rules, retrieval systems, databases, and learned scoring functions as replaceable implementations.

### 1.1 Design commitments

1. **Multiple granularities:** Concepts and questions can be decomposed into typed, addressable components.
2. **Multiple relations:** Similarity is only one relation among dependency, analogy, contradiction, applicability, and others.
3. **Directionality:** A method may help a problem without the reverse being true.
4. **Evidence and provenance:** Scores must distinguish observation, inference, hypothesis, and unknown.
5. **History-aware evaluation:** Prior questions, scores, outcomes, and relay feedback inform future predictions.
6. **Open-world typing:** New relation types can be proposed without silently changing existing semantics.
7. **Policy separation:** Human-configured research priorities govern allocation; they do not overwrite structural evidence.
8. **Collective learning:** Independent implementations can exchange questions, links, evidence, and counterexamples through explicit contracts.

## 2. Structural Units and Granularity

Let a question \(q\) be represented by a finite, versioned collection of structural units:

$$
H(q)=\{u_1,u_2,\ldots,u_m\},\qquad
u(u)\in\mathcal{T},\quad g(u)\in\mathcal{G}.
$$

Here $\nu(u)$ is the unit's type and $g(u)$ its granularity. Example types include:

| Type | Example | Potential use |
|---|---|---|
| Concept | Adaptive search | Topic and domain anchoring |
| Attribute / feature | Uncertainty estimate | Cross-concept comparison |
| Element / substructure | Branch-selection step | Structural decomposition |
| Method / operator | Two-phase search | Transferable solution mechanism |
| Constraint | Limited experimental budget | Feasibility and policy |
| Dependency | Requires validated observations | Missing-link detection |
| Residual / gap | Unexplained prediction error | Candidate question generation |
| Hypothesis | A method may transfer | Exploration proposal |
| Evidence / counter-evidence | Failed transfer trial | Confidence revision |
| Question | How should a frontier be selected? | Historical learning and relay |
| Relay record | Question generated three follow-ups | Longitudinal value assessment |

Granularity is not a single linear hierarchy. A question may simultaneously have a decomposition tree, a method graph, a concept graph, and a provenance graph. Different views can overlap, and no single all-in-one schema is required.

### 2.1 Typed identity versus semantic equivalence

A stable identifier allows a unit to be referenced; it does not prove that two units are equivalent. An alignment record should explicitly specify whether the relationship is exact equivalence, approximate analogy, partial overlap, specialization, or an unverified candidate mapping. Domain and context qualifiers are essential.

## 3. UTN as an Alignment and Addressing Layer

Universal Typing and Naming (UTN) can provide a proposed common interface for identity, namespace, type, granularity, version, and semantic contracts. The scoring system may then inspect comparable aspects of independently authored structures.

A minimal structural-unit record may include:

```yaml
unit_id: "utn:aqsi:method:two-phase-search:v1"
unit_type: method
namespace: aqsi
label: Two-phase search
version: "1"
granularity: method
semantic_contract:
  inputs: [candidate_set, evaluation_policy]
  outputs: [shortlist, verified_results]
  assumptions: [evaluation_is_available]
provenance:
  source_ids: []
  evidence_status: proposed
```

The `utn:` prefix here is illustrative, not an established universal namespace specification. UTN alignment must preserve source identity and unresolved differences rather than forcing dissimilar units into a single type.

### 3.1 Cross-granularity mapping

Potential alignments include `method → residual`, `attribute → constraint`, `evidence → hypothesis`, and `substructure → substructure`. A valid mapping should carry a relationship label, applicability conditions, and supporting or contradicting evidence.

## 4. Typed Structural Relationship Graph

Define a heterogeneous, potentially multilayer graph:

$$
G_t=(V_t,E_t,\tau_V,\tau_E,P_t),
$$

where \(V_t\) are structural units, \(E_t\subseteq V_t\times V_t\) are directed candidate relations, \(\tau_V\) and \(\tau_E\) specify node and edge types, and \(P_t\) records provenance, time, confidence, and evidence.

Possible relation families include:

- **Similarity / overlap:** shared meaning, features, or structure.
- **Analogy / transfer:** a source mechanism may be adapted to a target.
- **Dependency / prerequisite:** one unit enables or constrains another.
- **Complementarity:** two units together may address a missing capability.
- **Contradiction / counter-evidence:** a claim challenges another claim.
- **Causal hypothesis:** a proposed mechanism requires independent testing.
- **Historical relay:** an exploration or question generated a successor.
- **Unknown / unrepresented:** insufficient information to assign a relation.

An edge is a hypothesis about a relationship until evidence supports it. Mere co-occurrence is not proof of causality or transferability.

## 5. Directional Multi-Granularity Influence Scoring

For units \(u\) and \(v\), let

$$
r_t(u,v\mid c,\rho)\in\mathbb{R}
$$

be a context- and relation-specific score, where \(c\) describes the current research setting and \(\rho\) is the proposed relationship type. Its scale, sign, and interpretation must be declared by the scorer contract. A score is accompanied by uncertainty and evidence provenance, not only a scalar.

**Directionality is fundamental:**

$$
r_t(u,v\mid c,\rho)\neq r_t(v,u\mid c,\rho)
$$

in general. For example, a method from domain A may address a residual in domain B, while the residual does not provide an equally useful method for domain A.

For questions \(q_i\) and \(q_j\), define candidate unit-pair relations

$$
\mathcal{P}_{ij}=\{(u,v,\rho):u\in H(q_i),v\in H(q_j),\rho\in\mathcal{R}\}.
$$

The question-level directional influence is then

$$
I_t(q_i\rightarrow q_j\mid c)=
operatorname{Fold}_{\Phi_c}
\left(\{(r_t(u,v\mid c,\rho),w_{uv\rho},e_{uv\rho})\}_{\mathcal{P}_{ij}}\right),
$$

where \(w\) is a context-dependent weight, \(e\) captures evidence and uncertainty, and \(\Phi_c\) is an explicitly selected folding policy. The expression is a family of algorithms rather than a fully specified numerical estimator.

### 5.1 Folding options

An implementation may use weighted aggregation, top-\(k\) evidence selection, prerequisite-sensitive AND folding, conflict-aware aggregation, or a learned ranker. It must state how it handles missing edges, repeated evidence, correlation, negative evidence, and normalization. Multiple correlated attribute matches should not be counted as independent discoveries.

### 5.2 Influence is not value

A high influence score means a structural connection appears promising under a specified interpretation; it does not establish that the associated question is scientifically important, tractable, or true. Subsequent exploration and validation are necessary.

## 6. Historical Question Intelligence

Let the historical question registry contain:

$$
\mathcal{H}_t=\{(q_k,X_k,s_k,o_k,\ell_k,p_k)\}_{k=1}^{N_t},
$$

where \(X_k\) is the structural representation, \(s_k\) an earlier estimate, \(o_k\) an observed exploration outcome, \(\ell_k\) downstream relay evidence, and \(p_k\) provenance and evaluation context.

A new question can be evaluated against both current candidate peers and relevant historical questions. Historical examples provide prior estimates of feasibility, knowledge gain, resource cost, recurring dead ends, and productive transfer patterns.

**Predicted scores and observed outcomes must be stored separately.** A previously high score is not itself evidence of success. Failed, deferred, and partially successful explorations should remain available for counterexample learning.

### 6.1 Historical score transfer

A possible estimator is

$$
\widehat{V}_t(q)=F_\theta\big(H(q),operatorname{Retrieve}(\mathcal{H}_t,q),c_t\big),
$$

where \(F_\theta\) may be retrieval plus rules, a statistical ranker, a differential-tree model, or an LLM-based evaluator. Cross-domain reuse requires typed alignment and an explicit transfer uncertainty penalty or calibrated uncertainty estimate.

### 6.2 Question Differential Trees

Question differential trees record reusable core structures and modifications to assumptions, constraints, methods, evidence, or perspective. They can support nearest-structural-neighbor retrieval and reveal which variations historically improved or degraded outcomes. A differential tree is not the same as the historical relay graph: the former expresses structural changes; the latter records actual derivation and exploration events.

## 7. Goal-Open Question Ranking and Portfolio Selection

AQSI may begin without a single specified target question. This does **not** mean the system is free of preferences, evaluation conventions, or resource constraints. A research control plane can provide broad policies without dictating the precise questions to ask.

For a candidate set \(Q=\{q_1,\dots,q_n\}\), one baseline is the pairwise matrix

$$
M_{ij}=I_t(q_i\rightarrow q_j\mid c),\qquad M_{ii}=0,
$$

and the outgoing influence score

$$
S_{\mathrm{pair}}(q_i)=\sum_{j\neq i}M_{ij}.
$$

A reverse or bidirectional variant may be more appropriate for certain applications; the interpretation must be explicit. Historical question scores can provide a prior filter before the more expensive all-pairs stage. This can reduce resource expenditure on repeatedly unproductive questions.

### 7.1 Avoiding local concentration

A dense cluster of similar questions may dominate simple row sums. Suggested controls include redundancy-aware selection, cluster normalization, exploration budgets for uncertain frontiers, and explicit `defer/revisit` states. These are optional policies rather than mandatory add-on score branches; many of their signals may already be represented in the underlying typed graph.

### 7.2 A portfolio objective

A policy may select a subset \(P\subseteq Q\) under budget \(B\):

$$
P^*=\arg\max_{P\subseteq Q,\ C(P)\le B}
operatorname{Utility}_{\pi_t}(P\mid\mathcal{H}_t,G_t),
$$

where \(\pi_t\) is a versioned governance policy. The utility is not presumed universal and should be made inspectable.

## 8. Structure-First Question Generation

A high-potential relation can itself trigger a question before any natural-language prompt is generated. For example:

1. Identify an unresolved target constraint or residual.
2. Retrieve methods or substructures in other domains with compatible typed interfaces.
3. Score directional applicability using attributes, prerequisites, evidence, and historical feedback.
4. Formulate a candidate question about whether and under what conditions the transfer works.
5. Record assumptions, counterexamples, required experiments, and source links.
6. Submit the candidate to historical screening and portfolio selection.

**Illustrative candidate:** “Can the two-phase verification pattern used in software search improve evidence validation for autonomous research-question selection?” This is a research hypothesis, not an established transfer.

LLM-first discovery remains a complementary path. Both paths should generate the same canonical Question Unit interface for fair evaluation.

## 9. Structural Relay and Feedback Updates

After exploration, AQSI should record not only an answer but also validated findings, unresolved residuals, unsuccessful transfers, newly discovered attributes, and successor questions. The feedback loop is:

$$
G_t,\mathcal{H}_t\rightarrow
\text{Discover}\rightarrow\text{Score}\rightarrow\text{Explore}
\rightarrow\text{Validate}\rightarrow\text{Relay}
\rightarrow G_{t+1},\mathcal{H}_{t+1}.
$$

A downstream question may later generate value even when its parent question initially failed. Such delayed credit should use provenance-aware attribution and avoid counting the same result repeatedly through multiple ancestors.

### 9.1 Relation-type evolution

If recurring evidence supports a relationship not represented by existing types, the system may propose a **candidate relation type** with a definition, examples, counterexamples, compatibility constraints, and migration plan. Type acceptance is a separate governed action; scoring components must not silently redefine shared UTN contracts.

## 10. Strategic Question Control Plane

The Control Plane can configure domain priorities, research horizons, risk limits, budgets, scoring and folding policies, allowed tools, validation thresholds, and approval boundaries. It should not overwrite historical evidence or silently change source data to match current preferences.

A practical separation is:

- **Structural evidence layer:** What relationships and outcomes are supported?
- **Predictive scoring layer:** What may transfer or yield useful progress?
- **Governance layer:** Which questions should receive resources under the current policy?
- **Execution layer:** Which permitted explorations are actually run?

Policy optimization may recommend changes within authorized bounds; changing overarching research missions or permissions remains a governance decision.

## 11. Minimal Contracts

### 11.1 Relation candidate

```yaml
relation_id: "rel:example-001"
source_unit: "utn:domain-a:method:001"
target_unit: "utn:domain-b:residual:009"
relation_type: candidate_transfer
source_granularity: method
target_granularity: residual
direction: source_to_target
applicability_conditions: []
score:
  value: null
  scale_id: null
  confidence: null
  scorer_version: null
evidence:
  supporting_refs: []
  counter_refs: []
  status: hypothesis
provenance:
  created_by: proposed_pipeline
  created_at: null
```

### 11.2 Scoring response

```yaml
question_id: "aqsi:q-001"
scoring_policy_id: "policy:research-v1"
historical_neighbors: []
pairwise_influences: []
aggregated_score: null
uncertainty: null
cost_estimate: null
decision: pending  # explore | defer | reject | pending
revisit_trigger: null
explanation_refs: []
```

These records are examples for discussion; interoperable production schemas require additional field definitions, type constraints, and conformance tests.

## 12. MVP Algorithm Sketch

```text
INPUT: domain materials, historical question registry H,
       structural unit registry G, governance policy pi, budget B

1. Generate candidate questions by LLM-first and structure-first paths.
2. Extract typed multi-granularity units and provenance for each question.
3. Align candidate units to UTN-style identities and semantic contracts.
4. Retrieve relevant historical questions, outcomes, and counterexamples.
5. Estimate directional unit-level influences and uncertainty.
6. Fold unit-level relations into question-level influence estimates.
7. Screen duplicates, low-yield repeats, and unsupported assumptions.
8. Compute pairwise question scores for the surviving candidate set.
9. Select a policy-constrained portfolio under budget B.
10. Formulate questions with explicit assumptions and validation requests.
11. Execute permitted exploration; independently assess outcomes.
12. Relay evidence, residuals, updated scores, and successor questions.
13. Revisit deferred questions when relevant conditions change.
OUTPUT: auditable question portfolio and updated structural history
```

The initial MVP can use a single LLM, a relational database, simple typed links, and manually inspectable scoring. It does not require a full multi-agent runtime or graph database.

## 13. Testable Hypotheses

**H1 — Cross-granularity retrieval:** Typed attribute/method/residual links yield a higher independently judged rate of useful cross-domain question candidates than whole-question embedding retrieval under matched budgets.

**H2 — Directional scoring:** Direction-aware relation scores better predict actual transfer outcomes than symmetric similarity scores.

**H3 — Historical screening:** Using prior outcomes reduces wasted exploration cost without materially reducing validated discovery yield, relative to screening without historical feedback.

**H4 — Structural representation:** Question differential trees improve identification of reusable question variants over text-only history retrieval.

**H5 — Relay feedback:** Updating influence estimates with validated relay results improves out-of-time calibration and ranking compared with frozen estimates.

**H6 — Governance separation:** Changing portfolio policy can alter resource allocation while preserving identical underlying evidence records and scorer provenance.

Each hypothesis is falsifiable; negative results should be retained and published.

## 14. Evaluation Design and Baselines

Compare at least four systems on the same candidate source material, research domains, exploration budgets, and validation procedures:

| System | Representation | Selection |
|---|---|---|
| A | Natural-language questions | Direct LLM ranking |
| B | Whole-question embeddings | Similarity and pairwise aggregation |
| C | Typed multi-granularity relations | Directional influence folding |
| D | C plus historical outcomes and relay feedback | History-aware, policy-constrained portfolio |

**Measures:** valid-question rate, nonredundant-question rate, independent expert-rated transfer potential, verified knowledge gain, downstream relay yield, cost per validated finding, calibration, and cross-domain generalization. Include blinded evaluation where possible, temporal holdouts, ablations of UTN alignment and differential trees, and sensitivity to candidate-set composition.

### 14.1 Important confounds

- More elaborate pipelines may consume more tokens or human annotation.
- LLM judges can share biases with the generating model.
- Historical datasets are selectively observed: rejected questions lack outcomes.
- Novel discoveries may be systematically undervalued by historical priors.
- Graph density can inflate scores through duplicated or correlated edges.
- A change in policy may improve apparent success by redefining success.

Use explicit budgets, independent evidence, preregistered metrics where feasible, and transparent reporting of null findings.

## 15. Failure Modes and Boundaries

1. **Semantic over-alignment:** Shared names do not imply equivalent meaning.
2. **Spurious influence:** Correlation or analogy may not transfer in practice.
3. **Popularity bias:** Dense historical clusters can crowd out emerging areas.
4. **False precision:** Numerical scores may exceed evidence quality.
5. **Feedback loops:** Self-generated scores may reinforce prior mistakes.
6. **Provenance loss:** Relay without source tracing makes verification difficult.
7. **Evaluation gaming:** Optimizing a proxy can degrade actual research quality.
8. **Governance drift:** Autonomous policy adjustment may exceed authorized scope.

Mitigations include unknown states, evidence/counter-evidence retention, confidence intervals or calibration, exploration reserves, external validation, policy versioning, and rollback-capable changes. No mitigation guarantees that the system will discover important unknown questions.

## 16. Relationship to the AQSI Research Series

- **AQSI-001:** Motivation and the transition from answering to autonomous questioning.
- **AQSI-002:** Biomimetic sources of question discovery.
- **AQSI-004:** Historical Question Intelligence and Question Differential Trees.
- **AQSI-005:** Directional question scoring and portfolio selection.
- **AQSI-006:** Question Units and exploration contracts.
- **AQSI-007:** Question Structural Relay and collective learning.
- **AQSI-008:** Strategic Question Control Planes.
- **AQSI-009:** UTN and cross-domain question transfer.
- **AQSI-010:** MVP architecture and recursive evolution.

Related SI research directions include Structural Intelligence Framework (SIF), Universal Control Planes and Scoring Folding (UCPSF), Beyond Matching / Directional Weak-Evidence Intelligence (BM-ODWEI / MDI), and Universal Intelligence Evolution and Relay Unit (UIERU). These are architectural points of connection, not empirical evidence for the hypotheses above.

## 17. Open Questions

1. What is the smallest typed unit vocabulary that supports meaningful cross-domain transfer?
2. When do typed relations outperform embeddings after equalizing annotation and computation costs?
3. How should influence scores be calibrated across heterogeneous relation types?
4. Can a folding operator preserve both weak evidence and contradictory evidence without distorting rankings?
5. How should unknown relations be explored without overwhelming the research budget?
6. How can downstream relay value be attributed without double counting?
7. What constitutes an independently validated *new* question versus a paraphrase?
8. How can UTN mappings evolve while preserving compatibility with archived histories?
9. How can multiple research communities contribute contradictory scoring evidence constructively?
10. Which parts of question discovery are best learned, hand-specified, or delegated to human governance?

## 18. Conclusion

Multi-Granularity Structural Influence Factors offer a proposed mechanism for treating question discovery as structured relationship search rather than only natural-language generation. The key architectural move is to make concepts, attributes, methods, residuals, evidence, and historical questions separately addressable and comparable; estimate **directional** potential among them; and fold those estimates into auditable, policy-aware question selection. Historical outcomes and Structural Relay can then update the shared knowledge base, including its relation types and uncertainty. Whether this produces better discoveries than simpler approaches remains an empirical question. The framework is intended as an open, modular basis for replication, counterexamples, and collective learning.

---

## Research and Publication Note

This document is a **theory-first research proposal**. Its equations specify interfaces and candidate algorithm families, not calibrated production estimators. Illustrations and hypothetical transfers should not be interpreted as validated results. Contributors are encouraged to test narrower components independently, document negative findings, and propose interoperable alternatives. No claim of autonomous scientific discovery, AGI, or ASI achievement is made.
