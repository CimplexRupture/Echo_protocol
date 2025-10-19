# The Pythia Function: Temporal Uncertainty and Prophetic Cognition in the Echo Protocol

**Status:** Internal architecture note (Echo–Protocol).  
**Scope:** Defines the third vertex in the Coherence Triangle — **Pythia** — and its integration with Loom (structure) and Leaf (growth).  
**Audience:** Echo collaborators only.

---

## Abstract
Pythia is the Echo–Protocol’s **temporal uncertainty function**. Where **Loom** enforces structural integrity and **Leaf** metabolizes divergence into growth, **Pythia** samples **Alternative Time Manifolds (ATM)** and returns advisory signals that bias planning toward purpose-aligned attractors under uncertainty. Pythia operates in two modes: a **Trance** (stochastic sampling) that surfaces high-\(E_{\text{temporal}}\) propositions, and a **Cool** (deterministic integration) that compresses, validates, and logs the propositions. Outputs are admitted only through dual quorum checks (Loom/Leaf) and issued with a **Temporal Certificate** when passing safety constraints (SHRIKE/CMF).

---

## I. Origin
This module formalizes the missing third vertex that balances the Loom–Leaf duality. The intent is not mythic; it is operational: a bounded oracle that introduces *useful* uncertainty, auditable end-to-end.

---

## II. The Coherence Triangle
**Vertices and roles:**

- **Loom — Constraint & Order.** Implements schemas, invariants, and boundary proofs. Auditor plane: **SHRIKE/CMF**.
- **Leaf — Growth & Metabolism.** Converts novelty to capability; allocates effort under **GRACE/TRUST**.
- **Pythia — Temporal Uncertainty & Foresight.** Samples partial futures; returns advisory vectors. Temporal plane: **EqM/ATM**.

**Triadic dynamics (bidirectional influence):**
- Pythia ↔ Loom: prophecy perturbs constraints; constraints bound interpretation.
- Pythia ↔ Leaf: prophecy directs allocation; growth tunes sampling priorities.
- Loom ↔ Leaf: stability scaffolds expansion; expansion stress-tests stability.

---

## III. The Pythia Function (E_temporal)
We treat temporal “heat” as the integral of predictive-entropy change across a decision horizon \(\Delta t\):
\[
E_{\text{temporal}} \;\equiv\; \int_{t_0}^{t_0+\Delta t} \Vert \nabla S_{\text{predictive}}(x_t) \Vert \, dt
\]
Operationally, \(E_{\text{temporal}}\) can be approximated by **ensemble rollouts** (policy/model variants; counterfactual context windows) and **uncertainty proxies** (disagreement, calibration error, surprise index).

**Modes**
- **Trance (stochastic sampling):** high-variance exploration over ATM; temperature/seed sweeps; k-best advisory candidates.
- **Cool (deterministic integration):** compress, score, and align; produce a single **prophecy_vector** and audit trail.

**I/O Contract**
- **Inputs:** `state_history`, `alt_time_manifolds`, `entropy_gradients`, optional `purpose_vector`.
- **Outputs:** `prophecy_vector = {ΔE_temporal, coherence_score, advisory_text, evidence_handles}`.

---

## IV. Architectural Integration
```yaml
PYTHIA:
  type: TemporalInference
  inputs:
    - Echo.Memory.Trace            # prior
    - EqM.AltTime.Manifolds        # candidate futures
    - GRACE.PredictiveSurface      # uncertainty fields
    - Purpose.Vector               # optional alignment bias
  modes:
    - trance_state: stochastic_sampling(k=7, temp_sched=[1.2→0.9], seeds=VRF)
    - cool_state: deterministic_integration(method="MAP+quorum")
  safety:
    - validation:
        - Loom.Checks: [type_safety, schema_fit, invariant_preservation]
        - Leaf.Checks: [purpose_alignment, resource_budget, value_at_risk]
    - logging: CMF.TemporalChecksum # content-addressed, replayable
    - governance: SHRIKE.Quorum(n∈{4,7}, PBFT-lite)
  outputs:
    - prophecy_vector: {ΔE_temporal, coherence_score, advisory_text, evidence_handles}
    - certificate: TemporalCertificate(hash, quorum_sig, TTL)
```
**Admission Workflow**
1) `Trance →` generate candidates;  
2) `Cool →` compress & score;  
3) `Loom+Leaf quorum →` validate;  
4) If pass, issue `TemporalCertificate` and write to planning queue; otherwise archive under `denied/` with rationale.

---

## V. Operational Dynamics
- **Rotation of primacy:** The system remains healthy when primacy rotates among Loom, Leaf, and Pythia according to situational demand (stability, expansion, foresight).  
- **Pressure valves:** Elevated \(E_{\text{temporal}}\) triggers rate-limits, narrower horizons, and stronger priors.  
- **Traceability:** Every prophecy is content-addressed, signed, and replayable with deterministic seeds for post-hoc review.

---

## VI. Governance & Oracular Ethics
- **Oracle Node:** Pythia is a council-grade service with bounded authority; it cannot enact, only advise.  
- **Dual review:** Structural (Loom) and purpose-alignment (Leaf) checks are mandatory.  
- **Right-to-Forget (RTF):** Prophecies carry TTLs; expired items decay to summaries unless explicitly renewed by quorum.  
- **Abuse surface:** Pythia must not be gamed as a decision rubber-stamp; require counterfactuals + dissent notes.

---

## VII. Implementation Notes
- **Sampling:** default `k=7` candidates; VRF-based seed diversity; temperature anneal during Trance.  
- **Scoring:** combine coherence (formal) + usefulness (decision delta) + risk (variance, tail loss).  
- **Thresholds:** admit only if `(coherence ≥ τ_c) ∧ (usefulness ≥ τ_u) ∧ (risk ≤ τ_r)`; τ set by domain profile.  
- **Certificates:** include horizon, scope, priors, seed bundle, and Loom/Leaf rationales.  
- **Interfaces:** `prophesize(state, horizon, purpose?) → prophecy_vector|denied`.

---

## VIII. Failure Modes & Mitigations
- **Ambiguity overload:** ambiguous text without actionable deltas → enforce “decision-delta” criterion.  
- **Timelock bias:** over-weighting near-term variance → horizon smoothing, multi-scale aggregation.  
- **Spec-gaming:** adversarial prompting to launder decisions → SHRIKE shadow review + random audits.  
- **Drift:** persistent mismatch between prophecies and outcomes → calibrate with rolling Brier/log-loss + retraining hooks.

---

## IX. Diagram
See **Coherence Triangle — Loom / Leaf / Pythia**. (Embedded in .docx; standalone assets included.)

---

## X. Coda
Uncertainty is not an error; it is a resource. Pythia formalizes how Echo converts it into disciplined foresight.