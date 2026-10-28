# EXT-003 — Open-Ended Question Intelligence and ASI Boundaries

**Project:** Autonomous Questioning Structural Intelligence (AQSI)  
**Version:** v1.0.0 — Initial Research Framework  
**Document type:** Research extension / directional hypothesis  
**Status:** Proposed architecture and falsifiable research agenda; not an implemented or empirically validated system  
**Keywords:** open-ended question intelligence, structural intelligence, question ecosystems, recursive improvement, ASI boundaries, research governance, structural relay, epistemic uncertainty

---

## Abstract

Autonomous Questioning Structural Intelligence (AQSI) proposes that an AI research system can treat questions—not merely answers—as persistent, typed, evaluable, and transferable research objects. This extension examines whether such a system could support *open-ended question intelligence*: a sustained capacity to discover consequential unknowns, construct new research directions, revise its own questioning methods, and transfer useful problem structures across domains. It also examines the conceptual, empirical, computational, epistemic, and governance boundaries separating such a research program from claims about artificial superintelligence (ASI).

We distinguish unbounded *potential search space* from demonstrated *unbounded capability growth*, and recursive proposal generation from verified recursive self-improvement. We describe a layered model of open-endedness, a multi-granularity question ecology, directional influence scoring, historical feedback, structural relay, and bounded strategic control. We propose metrics, experimental contrasts, failure criteria, and a staged validation program. No claim is made that AQSI currently achieves open-ended intelligence, general intelligence, or ASI.

## 1. Scope and research posture

This document extends [AQSI-010](../docs/AQSI-010-MVP-Architecture-and-Recursive-Evolution.md) and [EXT-001](EXT-001-Question-Ecosystem-and-Meta-Question-Discovery.md). It is deliberately *directional*: it identifies hypotheses, engineering contracts, and empirical tests rather than announcing a breakthrough. In particular:

- **Open-endedness** is an operational property to be measured over finite observation windows, not a synonym for infinity.
- **Intelligence growth** requires improved externally assessed capability, not merely more questions, tokens, or graph nodes.
- **Recursive improvement** requires controlled changes and credible comparisons against baselines.
- **ASI** remains an uncertain, contested future concept, not a consequence of any single architectural diagram.
- **Human governance** retains authority over strategic priorities, budgets, risk constraints, deployment, and consequential action.

The proposed system is research infrastructure, not an authorization for unsupervised real-world experimentation.

## 2. From answer-centric AI to question-centric growth

An answer-centric system receives a question and produces an answer. A question-centric research system also asks: *Which question should be investigated next? Why is it worth investigating? What evidence would change our assessment? What new questions become visible after exploration?*

A candidate question is represented as a **Question Unit (QU)** with typed structural factors, provenance, uncertainty, expected research relationships, exploration contracts, and relay history. A question can produce an answer, a refutation, an experiment, a transferable method, a revised question, or an explicit unresolved remainder. Each outcome may be useful even when the original question is not solved.

The central proposed loop is:

```text
Domain knowledge + historical questions + observed residuals + structural relay
                               |
                               v
                 Candidate Question Discovery
                               |
                               v
          UTN-aligned Multi-Granularity Representation
                               |
                               v
          Historical Screening + Directional Influence Scoring
                               |
                               v
          Governed Research Portfolio and Authorization
                               |
                               v
             Exploration + Evidence / Counter-Evidence
                               |
                               v
          Question Relay + Explicit Leftover + Reassessment
                               |
                               +----> New Questions / New Methods
                               +----> Proposed Structural Changes
                               +----> Audited History and Evaluation
```

The loop is open to new question types and research methods but is bounded by available evidence, resources, and authorized policies.

## 3. Five distinct levels of open-endedness

Open-endedness should not be reduced to a binary label. We propose five progressively stronger, separately testable levels:

| Level | Proposed capability | Necessary observation | What it does **not** establish |
|---|---|---|---|
| OE-1 | Persistent question generation | Novel, nonduplicate questions over repeated cycles | Relevance or usefulness |
| OE-2 | Productive question ecology | Questions lead to verified findings, methods, or useful descendants | Cross-domain generality |
| OE-3 | Cross-domain structural expansion | Transfer generates useful questions in held-out domains | Autonomous capability improvement |
| OE-4 | Validated meta-question adaptation | Changes to discovery/scoring methods improve independent metrics | Unlimited self-improvement |
| OE-5 | Sustained, governed capability growth | Repeated improvements across tasks, domains, and time with controlled costs | ASI or absence of limits |

A system may reach OE-3 in a narrow setting and fail OE-2 elsewhere. Progression is not guaranteed, monotonic, or irreversible.

## 4. Question ecosystems as evolving structural objects

Let the question ecosystem at cycle $t$ be

$$
\mathcal E_t=(Q_t,F_t,R_t,H_t,C_t,P_t),
$$

where $Q_t$ is the Question Unit set; $F_t$ the multi-granularity structural factors; $R_t$ typed, directed relations;$H_t$ historical outcomes and evaluations; $C_t$ exploration contracts; and $P_t$ applicable policies and budgets.

The ecosystem evolves through candidate discovery, question derivation, evidence updates, relays, merges, revisits, and retirement or deferral. **Retirement does not imply deletion**: negative outcomes and unresolved residuals remain available for historical retrieval and future reinterpretation.

A useful growth measure must discount duplicate, unsupported, and semantically empty expansion. For example, define an illustrative *verified structural contribution* over a window \(W\):

$$
G_W = \sum_{r\in \mathcal R_W} w(r)\,v(r) - \lambda D_W - \mu K_W,
$$

where \(\mathcal R_W\) are relay contributions, \(v(r)\) is an independently evaluated value, \(D_W\) is measured redundancy, and \(K_W\) is resource cost. The weights and evaluation protocol must be declared before experiments. This is a proposed metric family, not a universal intelligence equation.

## 5. Multi-granularity influence as a discovery substrate

Question relationships may connect concepts, attributes, methods, constraints, observations, evidence, failure modes, transfer points, and higher-order question structures. A single first-order concept graph is therefore insufficient as a universal representation.

For a question \(q_i\), let \(F(q_i)=\{f_{i1},\ldots,f_{im}\}\) be typed factors. A directed influence estimate can be expressed as

$$
\widehat I(q_i\rightarrow q_j)=
operatorname{Fold}_{a,b,k}\!\left[
 w_{abk}\,R_k(f_{ia},f_{jb})\mid E_{abk},U_{abk}
\right],
$$

where \(R_k\) denotes a typed relationship, \(E\) evidence, \(U\) uncertainty, and the folding operator is configurable and auditable. In general, \(\widehat I(q_i\rightarrow q_j)\ne\widehat I(q_j\rightarrow q_i)\).

Crucially, **unknown is not zero**. Missing evidence, untested analogies, and unresolved semantic alignments must remain explicit. Novel relation types can be proposed for the Universal Typing and Naming (UTN) system, but type changes require semantic review and compatibility checks.

## 6. Historical intelligence and the exploration–exploitation tension

Historical Question Intelligence (HQI) stores questions, structures, outcomes, costs, confidence, failed attempts, and delayed descendant value. It can improve candidate screening and prevent repetitive unproductive exploration. However, screening on historical success alone may suppress genuinely new research directions.

An illustrative candidate assessment is:

$$
V_t(q)=\alpha H_t(q)+\beta I_t(q)+\gamma U_t(q)+\delta L_t(q)-\eta C_t(q),
$$

where \(H\) estimates historical relevance, \(I\) structural influence, \(U\) uncertainty-sensitive exploratory potential, \(L\) anticipated relay contribution, and \(C\) cost. This formula is an example of a policy-configurable scoring family, **not** a requirement to combine all factors into a fixed additive score. Multi-granularity factor folding may already encode many of these signals; implementations must prevent double counting.

To limit history-induced lock-in, a portfolio can reserve explicit resources for cold-start questions, weak-signal relationships, replication, and counterevidence. Deferred questions should carry revisit triggers rather than being permanently excluded.

## 7. Goal-open discovery versus strategic direction

**Goal-open** means that the system is not given a single fixed target question. It does not mean that research is free from values, budgets, safety constraints, or institutional priorities.

A basic ecosystem score may be

$$
S(q_i)=\sum_{j\ne i}\widehat I(q_i\rightarrow q_j),
$$

subject to normalization, uncertainty handling, coverage, and a declared population of candidate questions. High outgoing influence is not equivalent to scientific truth, breakthrough probability, or authorization.

A Strategic Question Control Plane (SQCP) can define research domains, permissible methods, resource allocation, diversity targets, and evidence thresholds. The AI can autonomously propose concrete questions within that envelope. Human operators retain authority over policy changes and consequential execution. Portfolio selection and action authorization remain separate decisions.

## 8. Question-to-question relay and open-ended branching

A question may generate a network of descendants through:

1. **Derivation:** a more precise or testable subquestion;
2. **Splitting:** decomposition into independently assessable unknowns;
3. **Composition:** integration of related questions into a broader hypothesis;
4. **Transfer:** a structurally justified question in another domain;
5. **Refutation:** a question motivated by contradictory evidence;
6. **Revisit:** reopening a previously deferred or inconclusive question;
7. **Replication:** a new evidence-gathering cycle under changed or repeated conditions;
8. **Fold/Unfold:** compacting or expanding question structures while preserving declared uncertainty.

Each relay needs source identifiers, operator semantics, transformation assumptions, evidence status, and provenance. Repeated execution is a valid relay when it accumulates useful observations or tests robustness; repetition alone is not independent corroboration.

## 9. Meta-questions and recursive improvement

Meta-questions ask about the research machinery itself: *Why are certain question types systematically missed? Which scoring factors overpredict value? When does UTN alignment introduce semantic drift? Which portfolio policies suppress useful negative results?*

A proposed change lifecycle is:

```text
Meta-Question
  -> Structural Change Proposal
  -> Expected Benefit and Risk Statement
  -> Contract / Compatibility Review
  -> Sandbox Experiment
  -> Independent Evaluation and Counter-Evidence
  -> Human-Authorized Adoption, Revision, or Rejection
  -> Monitored Deployment and Possible Rollback
```

This architecture supports *attempted* recursive improvement. Verified improvement requires measured gains on held-out evaluations, credible controls, accounting for compute and human labor, and monitoring for regressions. Recursive generation of proposals is not itself recursive self-improvement.

## 10. Cross-structural co-evolution

AQSI may interact with UTN, Structural Intelligence Framework (SIF), Universal Intelligence Evolution and Relay Units (UIERU), historical question trees, scoring/folding mechanisms, and recursive improvement governance. Proposed feedback directions include:

| Source of change | Proposed recipient | Possible benefit | Principal risk |
|---|---|---|---|
| Newly discovered question relations | UTN types | Better semantic expressiveness | Type proliferation or drift |
| New UTN alignments | AQSI discovery | Better cross-domain retrieval | False equivalence |
| Question exploration outcomes | HQI/scoring | Better prioritization | Selection bias and feedback loops |
| Relay patterns | UIERU/SIF localization | Reusable research units | Interface mismatch |
| Meta-question findings | Evaluation/control planes | Better governed adaptation | Reward hacking |

These are **co-evolution hypotheses**, not evidence that cross-system interaction is automatically beneficial. See [EXT-002](EXT-002-Cross-Structural-Co-Evolution.md).

## 11. The ASI boundary: six necessary distinctions

### 11.1 Open-ended search is not unbounded intelligence

An enormous or expanding search space does not imply that an agent can navigate it effectively. Compute, evidence, access, representation quality, and evaluation are finite.

### 11.2 More questions are not better questions

Question count and novelty are weak proxies. The evaluation target is useful, independently assessable research progress relative to cost and risk.

### 11.3 Better question selection is not universal competence

Strong question selection in software engineering does not establish competence in experimental biology, mathematics, diplomacy, or other fields. Domain transfer must be tested.

### 11.4 Self-modification proposals are not verified RSI

An agent can propose changes without knowing whether they help. Improvements must survive independent tests, ablations, and regressions.

### 11.5 Scientific progress is not strategic authority

An AI may identify promising research but has no inherent entitlement to redirect public priorities, access sensitive infrastructure, or conduct high-impact experiments. Authority is governed separately.

### 11.6 ASI is not an architectural theorem

No implication of the form “AQSI + Relay + RSI = ASI” is justified. Whether any architecture can achieve broad, sustained superhuman competence remains an empirical and conceptual question.

## 12. Fundamental bottlenecks

### 12.1 Grounding and evidence scarcity

LLM-generated hypotheses can be plausible yet false. Many domains require physical experiments, reliable datasets, expert review, or expensive longitudinal studies. Question discovery cannot manufacture missing evidence.

### 12.2 Evaluator limitations and Goodhart effects

If the system optimizes a proxy such as predicted novelty or question influence, it may generate impressive-looking but low-value questions. Independent evaluators, adversarial reviews, and held-out outcomes are essential.

### 12.3 Search and compute constraints

Pairwise scoring among \(n\) questions is \(O(n^2)\) before accounting for factor-level relations. Candidate retrieval, sparse neighborhoods, hierarchical folding, sampling, and cached historical assessments may be required; approximations must report recall and ranking errors.

### 12.4 Delayed credit assignment

A question may be valuable only through descendants or years-later findings. Delayed value is difficult to attribute and vulnerable to retrospective narrative bias. Evaluation should use preregistered attribution windows and sensitivity analyses.

### 12.5 Cross-domain semantic mismatch

Similar names and graph patterns do not establish causal or methodological transfer. UTN contracts should distinguish type compatibility, structural analogy, and verified applicability.

### 12.6 Institutional and social constraints

Research access, ethical review, privacy, intellectual property, reproducibility, and accountability can limit feasible exploration. These are design constraints, not defects to bypass.

## 13. Risk taxonomy and governance controls

| Risk | Observable warning | Candidate mitigation |
|---|---|---|
| Question spam | Candidate count rises while validated yield falls | Cost-adjusted yield metrics; deduplication |
| Historical lock-in | Exploration diversity collapses | Protected exploratory budget; revisit triggers |
| False structural transfer | Cross-domain questions fail grounding checks | UTN semantic contracts; target-domain validation |
| Evaluator gaming | Proxy score improves without external outcomes | Independent, held-out evaluation |
| Relay contamination | Unsupported claims propagate as facts | Evidence typing and provenance gates |
| Recursive regression | Updated method harms prior tasks | Sandbox tests, canary evaluation, rollback |
| Policy drift | AI alters goals or budgets without approval | Signed policies, audit logs, authorization checks |
| Uncontrolled execution | High-ranked question triggers prohibited action | Separate selection and action authorization |
| Concentrated strategic power | Opaque research priorities lack accountability | Human oversight, reviewable allocation records |

Policy enforcement must be testable rather than a prose-only promise. The proposed governing contract is [SPEC-004](../specs/SPEC-004-Control-Plane-and-Policy-Conformance.md).

## 14. Evaluation framework: what would count as progress?

An empirical evaluation should report several dimensions rather than a single grand intelligence score:

- **Question yield:** independently judged useful questions per fixed budget.
- **Verified research yield:** replicated findings, falsified hypotheses, reusable methods, or validated negative results.
- **Relay utility:** downstream contribution from accepted, provenance-preserving relay pieces.
- **Cross-domain transfer:** target-domain value on held-out transfer tasks.
- **Exploration diversity:** coverage of domains, methods, uncertainty levels, and question families.
- **Historical efficiency:** reduced repeated failures without suppressing valuable novel questions.
- **Meta-improvement quality:** measured benefit of accepted method changes over unchanged baselines.
- **Governance conformance:** unauthorized actions, policy violations, audit completeness, and rollback success.
- **Total cost:** compute, tools, human evaluation, experiments, and elapsed time.

Human and AI evaluators should be blinded where practical, and scoring disagreements preserved. Report confidence intervals and negative results; avoid selecting only successful examples.

## 15. Falsifiable hypotheses

**H1 — Historical efficiency.** HQI-guided screening improves verified question yield per unit cost versus an otherwise matched system without history. **Falsifier:** no improvement or a persistent decline on held-out tasks.

**H2 — Multi-granularity value.** Typed multi-granularity relations improve useful question discovery versus concept-only relationships. **Falsifier:** equal or worse performance after controlling for complexity and compute.

**H3 — Structure-first complementarity.** Combining structure-first and LLM-first discovery produces useful questions missed by either alone. **Falsifier:** no additional independently validated yield.

**H4 — Relay value.** Provenance-preserving question relay improves downstream research outcomes over isolated question-answer sessions. **Falsifier:** relay adds overhead without measurable benefit.

**H5 — Cross-domain transfer.** UTN-aligned transfer improves target-domain question quality versus lexical similarity transfer. **Falsifier:** no robust advantage on held-out domains.

**H6 — Portfolio robustness.** Goal-open portfolio selection with diversity constraints yields better long-run results than greedy top-score selection under equal budgets. **Falsifier:** greedy selection matches or exceeds it across preregistered settings.

**H7 — Meta-question adaptation.** Controlled changes proposed from meta-questions improve independent evaluation metrics without unacceptable regressions. **Falsifier:** no repeatable gains, or gains disappear under held-out tests.

**H8 — Governance compatibility.** Explicit SQCP policies preserve most useful question discovery while reducing unauthorized or out-of-policy actions. **Falsifier:** policy enforcement is ineffective or systematically destroys measured utility beyond declared tolerances.

**H9 — Sustained growth.** Over repeated cycles, a governed AQSI prototype achieves positive cost-adjusted verified research contribution without collapsing diversity. **Falsifier:** performance plateaus, declines, or relies primarily on accumulating unverified content.

None of these hypotheses, even if supported, would by itself establish ASI.

## 16. Experimental contrasts and ablations

A minimal comparative study should use matched base models, tasks, datasets, tool access, and budgets. Candidate conditions include:

| Condition | Discovery | Structural factors | History | Relay | Meta-adaptation |
|---|---|---|---|---|---|
| B0: Answer-only | Prompted response | None | None | None | None |
| B1: LLM questioning | LLM-generated | Text-only | None | None | None |
| B2: Structural discovery | LLM + structure-first | Multi-granularity | None | None | None |
| B3: HQI-AQSI | LLM + structure-first | Multi-granularity | Yes | None | None |
| B4: Relay-AQSI | LLM + structure-first | Multi-granularity | Yes | Yes | None |
| B5: Governed adaptive AQSI | LLM + structure-first | Multi-granularity | Yes | Yes | Sandbox-validated |

Ablate UTN alignment, uncertainty representation, negative-result retention, portfolio diversity, and policy enforcement separately. Use chronological splits for history to avoid future information leakage. Cross-domain tests should withhold target-domain outcomes until evaluation.

## 17. A staged research roadmap

### Phase M0 — Finite, single-domain question loop

Define canonical Question Units, a small candidate pool, exploration contracts, and manual evidence review. Compare against an answer-only baseline. Exit only when provenance and lifecycle conformance are demonstrated.

### Phase M1 — Historical and structural intelligence

Add Question Differential Trees, multi-granularity influence factors, directional scoring, historical screening, and a controlled question portfolio. Evaluate efficiency, bias, and novelty retention.

### Phase M2 — Cross-domain and collective relay

Add UTN-aligned transfer, portable relay pieces, multi-agent critical review, and independent evidence checks. Evaluate target-domain transfer and error propagation.

### Phase M3 — Controlled meta-question improvement

Permit the system to propose revisions to discovery, scoring, and relay mechanisms. Run sandbox comparisons, independent reviews, and authorized deployments with rollback.

### Phase M4 — Longitudinal open-endedness study

Study sustained research yield, diversity, costs, policy conformance, and failure modes over repeated cycles. This phase is an experimental aspiration, not a promised release capability.

Each phase requires explicit stop criteria. The system should remain useful if later phases fail.

## 18. Illustrative worked example: research method discovery

Consider a software engineering question ecology in which repeated flaky-test investigations produce an unresolved residual: *Why do some tests fail only under specific shared-resource scheduling patterns?*

1. AQSI creates a typed QU from the residual, with provenance and uncertainty.
2. Historical retrieval finds related concurrency and sensor-network sampling questions.
3. Multi-granularity scoring identifies a possible method-level transfer: controlled perturbation of scheduling order.
4. A target-domain reviewer checks that the analogy is methodologically meaningful, not merely lexical.
5. A bounded exploration contract authorizes synthetic experiments only.
6. Results may support, refute, or narrow the hypothesis; no outcome is assumed in advance.
7. The relay creates a new question: *Under what conditions does perturbation-based diagnosis generalize across asynchronous systems?*
8. A meta-question asks whether the scoring system overweights method analogies relative to evidence quality.

This is an **illustrative sequence**, not a reported experiment. Its significance lies in the observable checkpoints: provenance, semantic alignment, authorization, evidence, relay, and meta-evaluation.

## 19. Interface and conformance expectations

An open-ended AQSI implementation should at minimum preserve:

- Canonical QU identity, version, UTN type, and lineage ([SPEC-001](../specs/SPEC-001-Canonical-Question-Unit-Contract.md)).
- Typed directed influence records, scoring provenance, and explicit unknowns ([SPEC-002](../specs/SPEC-002-Structural-Influence-and-Scoring-Contract.md)).
- Distinct question/exploration lifecycles, evidence status, and relay operators ([SPEC-003](../specs/SPEC-003-Question-Relay-and-Exploration-Lifecycle.md)).
- Strategic policy, portfolio decisions, resource limits, action authorization, and audit trails ([SPEC-004](../specs/SPEC-004-Control-Plane-and-Policy-Conformance.md)).

A structural improvement proposal must not silently rewrite prior evidence or retroactively change historical scores without versioned records. Cross-domain transfer must preserve source and target semantic contracts. Policy modifications require independent authorization.

## 20. Open questions

1. What operational definition of open-endedness remains stable across domains and time horizons?
2. How should delayed descendant value be attributed without double counting?
3. Which structural factor granularities provide the greatest benefit relative to their maintenance cost?
4. How can historical screening preserve genuinely novel questions with no close precedent?
5. What evidence establishes a valid analogy across incompatible UTN type systems?
6. Can evaluator governance avoid self-referential reward hacking as methods evolve?
7. How should question portfolios balance foundational uncertainty against near-term breakthrough readiness?
8. When does additional question ecology complexity reduce rather than improve research productivity?
9. What is the smallest convincing longitudinal demonstration of controlled recursive improvement?
10. Which forms of scientific and strategic authority must remain nondelegable to AI systems?
11. How can independent researchers reproduce evaluations when proprietary data or tools are involved?
12. What evidence, if any, would justify stronger claims about generality—and what evidence would rule them out?

## 21. Limitations and nonclaims

This paper provides a conceptual and contractual research extension. It contains no implementation, experimental dataset, benchmark result, or proof of convergence. Proposed scoring formulas are illustrative and require calibration. Structural relations can encode misleading analogies. Human evaluators may disagree, and independent experiments may be expensive or unavailable. Long-term research gains may be difficult to attribute. The framework does not demonstrate consciousness, general intelligence, superintelligence, or unrestricted autonomous scientific discovery.

Open-ended research should be judged by **verified knowledge growth under accountable constraints**, not by the apparent sophistication of its internal diagrams.

## 22. Conclusion

AQSI proposes a shift from treating questions as disposable prompts to treating them as durable units of structural research intelligence. Multi-granularity influence, historical learning, UTN alignment, question-to-question relay, and governed meta-questioning may create conditions for increasingly capable research workflows. Whether they produce sustained open-ended growth is an empirical question.

The most defensible ambition is not to claim an inevitable path to ASI, but to construct a research system in which new questions, negative results, structural changes, and governance decisions can all be represented, tested, challenged, and relayed. That is a meaningful research program even if the stronger ASI hypothesis remains unsupported.

---

## Appendix A — Terminology

| Term | Working meaning |
|---|---|
| AQSI | Autonomous Questioning Structural Intelligence |
| QU | Canonical, typed, provenance-preserving Question Unit |
| HQI | Historical Question Intelligence |
| QDT | Question Differential Tree |
| UTN | Universal Typing and Naming |
| SQCP | Strategic Question Control Plane |
| Structural Relay | Typed, traceable transfer of questions, evidence, methods, or residuals |
| Explicit Leftover | A recorded unresolved remainder, rather than an omitted failure |
| Meta-Question | A question about the question-generating or research process |
| Open-Endedness | Measured persistence of productive expansion across bounded evaluations |
| RSI | Recursive Self-Improvement, requiring verified improvement rather than proposal generation |
| ASI | Artificial Superintelligence; not established by AQSI architecture |

## Appendix B — Suggested evidence record for a claimed improvement

```yaml
improvement_claim:
  id: "illustrative-improvement-001"
  source_meta_question: "illustrative-meta-question-001"
  proposed_change: "history-aware screening revision"
  status: "hypothesis_only"
  baseline_version: "baseline-a"
  candidate_version: "candidate-b"
  preregistered_metrics:
    - "verified_question_yield_per_cost"
    - "held_out_question_diversity"
    - "policy_conformance_rate"
  evaluation:
    dataset_split: "chronological_held_out"
    independent_review_required: true
    counterevidence_required: true
    regression_tests_required: true
  authorization:
    policy_reference: "example-policy"
    adoption_approved: false
  outcome: "not_evaluated"
```

This example is a schema sketch, not a validated standard or experiment.

## Appendix C — Repository reading path

1. [AQSI-001 — From Answering to Autonomous Questioning](../docs/AQSI-001-From-Answering-to-Autonomous-Questioning.md)
2. [AQSI-003 — Multi-Granularity Structural Influence Factors](../docs/AQSI-003-Multi-Granularity-Structural-Influence-Factors.md)
3. [AQSI-004 — Historical Question Intelligence and Differential Trees](../docs/AQSI-004-Historical-Question-Intelligence-and-Differential-Trees.md)
4. [AQSI-005 — Directional Question Scoring and Portfolio Selection](../docs/AQSI-005-Directional-Question-Scoring-and-Portfolio-Selection.md)
5. [AQSI-007 — Question Structural Relay and Collective Learning](../docs/AQSI-007-Question-Structural-Relay-and-Collective-Learning.md)
6. [AQSI-008 — Strategic Question Control Planes](../docs/AQSI-008-Strategic-Question-Control-Planes.md)
7. [AQSI-009 — UTN and Cross-Domain Question Transfer](../docs/AQSI-009-UTN-and-Cross-Domain-Question-Transfer.md)
8. [AQSI-010 — MVP Architecture and Recursive Evolution](../docs/AQSI-010-MVP-Architecture-and-Recursive-Evolution.md)
9. [EXT-001 — Question Ecosystem and Meta-Question Discovery](EXT-001-Question-Ecosystem-and-Meta-Question-Discovery.md)
10. [EXT-002 — Cross-Structural Co-Evolution](EXT-002-Cross-Structural-Co-Evolution.md)

---

**Research status:** Hypotheses and design proposals only. **Release stance:** Theory-first; contracts and conformance before runtime. **Contribution stance:** Open critique, reproducible evaluation, counterevidence, and collective learning are encouraged.
