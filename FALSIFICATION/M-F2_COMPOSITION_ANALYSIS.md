# AetherMemory — M-F2 Composition Analysis

**Failure condition under test:** M-F2 — Non-decomposition
**Status:** Partial execution (Policy and Audit contributions are conditional)
**Version:** 1.0.0
**Date:** 2026-11-19
**Author:** Samir Baladi
**ORCID:** [0009-0003-8903-0029](https://orcid.org/0009-0003-8903-0029)
**License:** CC-BY-4.0
**Position in the Aether family:** Twelfth project (candidate)
**Decision:** (E) Undetermined (interim)

---

## 0. Status of this analysis

This document **executes** part of M-F2: the composition argument described
in `FALSIFICATION/FALSIFICATION_PLAN.md` (Section 3.2).

It is **partial**, for the same reason M-F1 is partial: AetherPolicy and
AetherAudit are paused at Phase 4. Their contribution to the composition
cannot be fixed. The analysis therefore builds the composition in **two
stages**:

1. **Stage A — Git + Mesh.** This is the foundational composition. It is
   assessed fully, because both dimensions are foundational.
2. **Stage B — Git + Mesh + Policy + Audit.** This is the full composition.
   It is assessed **conditionally**, under the most favourable reading of
   Policy and Audit for the reduction. If the remainder survives even under
   the most favourable reading, M-F2 is not falsified by Policy or Audit.

The analysis does **not** decide M-F2. It records what survives the
composition and under what conditions.

---

## 1. What M-F2 requires

M-F2 is falsified if the composition of Git + Mesh + Policy + Audit covers
S1–S7 with **no remainder** — that is, if every stage is provided by the
composition.

A remainder is any stage, or any part of a stage, that the composition does
not provide. A single remainder is sufficient to keep M-F2 open (not
falsified).

This is the falsification-first direction: the condition is tested by looking
for a remainder, not by asserting one.

---

## 2. Carrying forward M-F1

The M-F1 analysis (`M-F1_COVERAGE_ANALYSIS.md`) established:

| Stage | Git | Mesh | Policy | Audit |
|:-:|:-:|:-:|:-:|:-:|
| S1 Acquisition | ✘ | ✘ | ? | ? |
| S2 Qualification | ✘ | ~ | ? | ? |
| S3 Consolidation | ~ | ~ | ? | ? |
| S4 Persistence | ✔ | ✔ | ? | ? |
| S5 Retrieval | ~ | ✘ | ? | ? |
| S6 Revision | ~ | ~ | ? | ? |
| S7 Expiration | ✘ | ✘ | ? | ? |

**S4 is covered.** M-F2 does not need to address S4: if the composition covers
it, AetherMemory adds nothing there. The remainder, if any, is in S1, S2, S3,
S5, S6, S7.

---

## 3. Stage A — Composition of Git + Mesh

This is the composition of the two foundational dimensions alone.

### 3.1 What Stage A covers

**S4 (Persistence).** Covered. Git stores, Mesh replicates. No remainder.

**S3 (Consolidation), partial.** Git can merge branches; Mesh converges
replicas. The composition resolves **mechanical** conflicts (same bytes,
different versions) but not **semantic** conflicts (two contradictory claims
about the world). The remainder is the semantic resolution.

**S5 (Retrieval), partial.** Git can fetch a version; Mesh distributes. The
composition retrieves by **identifier**, not by **context and authority**. The
remainder is scope-bounded retrieval.

**S6 (Revision), partial.** Git tracks byte revisions; Mesh propagates them.
The composition records that a unit changed, not that it was **superseded**.
The remainder is revision semantics.

### 3.2 What Stage A does not cover

**S1 (Acquisition).** Neither Git nor Mesh decides what enters the memory.
The composition has no acquisition stage. **Full remainder.**

**S2 (Qualification).** Neither Git nor Mesh assesses source trust. The
composition has no qualification stage. **Full remainder.**

**S7 (Expiration & Forgetting).** Neither Git nor Mesh distinguishes deletion
from forgetting. The composition deletes bytes; it does not invalidate
knowledge. **Full remainder.**

### 3.3 Stage A summary

The composition of Git + Mesh leaves:

- **Three full remainders:** S1, S2, S7.
- **Three partial remainders:** S3 (semantic resolution), S5 (scope-bounded
  retrieval), S6 (revision semantics).

**Stage A does not cover the lifecycle.** M-F2 is not falsified by Stage A.

---

## 4. Stage B — Adding Policy and Audit

Policy and Audit are the two candidates that might cover the remainders. They
are paused at Phase 4. To assess the composition without resolving them, the
analysis adopts the **most favourable reading** for the reduction: it assumes
that Policy and Audit cover **as much as they plausibly could**.

If a remainder survives even under this assumption, M-F2 is not falsified by
Policy or Audit.

### 4.1 Most favourable reading of AetherPolicy

The most favourable reading is that AetherPolicy provides:

- **Lifecycle rules** — retention periods, expiration conditions, deletion
  triggers. This could cover **S7 (Expiration)** as a rule.
- **Authorization rules** — who may retrieve what. This could cover part of
  **S5 (Retrieval)**.
- **Revision rules** — when a unit must be updated. This could cover part of
  **S6 (Revision)**.

Even under this reading, AetherPolicy provides **rules**, not **enforcement**
or **state**. A policy says "expire after 30 days"; it does not say which unit
is expiring now, nor does it preserve the unit's provenance after expiration.
The remainder is the **lifecycle state**, not the **lifecycle rule**.

### 4.2 Most favourable reading of AetherAudit

The most favourable reading is that AetherAudit provides:

- **Provenance records** — source and derivation chain of every unit. This
  could cover **S2 (Qualification)** as a record, and part of **M4**.
- **Lifecycle history** — when a unit was acquired, revised, or retired. This
  could cover part of **S1 (Acquisition)** and **S6 (Revision)**.

Even under this reading, AetherAudit provides **records**, not **validity**.
An audit record says "this unit came from source X at time T"; it does not say
"this unit is valid now". The remainder is **temporal validity**, not
**provenance**.

### 4.3 Stage B summary

Under the most favourable reading of Policy and Audit:

| Stage | Covered by composition? | Remainder |
|:-:|:-:|---|
| S1 Acquisition | Partial (Audit records the entry) | The **decision** to admit a unit — who admits, under what criteria. |
| S2 Qualification | Partial (Audit records the source) | The **assessment** of trust — is this source valid *now*? |
| S3 Consolidation | Partial (Git merges bytes) | **Semantic** resolution of conflicting claims. |
| S4 Persistence | Full | None. |
| S5 Retrieval | Partial (Policy authorizes) | **Scope-bounded retrieval at use time** — is this unit in scope for *this* requester *now*? |
| S6 Revision | Partial (Audit records, Policy rules) | **Marking a unit as superseded** — the state, not the history. |
| S7 Expiration | Partial (Policy rules) | **Forgetting with provenance preserved** — the state, not the rule. |

**A remainder survives at every stage except S4.** The remainder is not a
single missing stage; it is the **state** of each stage as distinct from its
**rule** (Policy) and its **record** (Audit).

---

## 5. The nature of the remainder

The composition analysis shows that the remainder is **not** a missing
function. It is a missing **layer**:

| Provided by composition | Remainder |
|---|---|
| Rule (Policy) | State (which unit, now) |
| Record (Audit) | Validity (is this unit valid now) |
| Bytes (Git) | Semantic coherence (do these claims agree) |
| Replicas (Mesh) | Convergence of validity (not just of data) |

The remainder is the **state of knowledge at a moment**, as distinct from the
**rules** that govern it, the **records** that describe it, and the **bytes**
that store it.

This is exactly the distinction the paper draws in Section 1.2:

> "Memory is not (only) storage... Memory is not (only) consistency...
> Memory is not (only) policy."

The composition analysis **gives this distinction a concrete form**: the
remainder is the state layer that Git, Mesh, Policy, and Audit each presuppose
but none provides.

---

## 6. Preliminary M-F2 status

| Question | Answer |
|---|---|
| Does Git + Mesh cover S1–S7? | **No.** Three full remainders (S1, S2, S7). |
| Does Git + Mesh + Policy + Audit cover S1–S7 under the most favourable reading? | **No.** A remainder survives at six of seven stages (all but S4). |
| Is M-F2 **falsified**? | **No.** A remainder survives even under the most favourable reading. |
| Is M-F2 **accepted**? | **No.** The remainder is characterized, but its **architectural status** is not settled. It may still be a feature of Policy, Audit, or a composition effect. |
| **Current M-F2 status** | **Partial — remainder characterized; architectural status open.** |

M-F2 is **not falsified** and **not accepted**. It remains **untested in full**.

---

## 7. What this analysis does establish

1. **A remainder survives the composition**, even under the most favourable
   reading of Policy and Audit.
2. **The remainder is the state layer** — the state of knowledge at a moment,
   distinct from the rules (Policy), records (Audit), bytes (Git), and
   replicas (Mesh).
3. **The remainder is concentrated in S1, S2, S7** (full) and S3, S5, S6
   (partial), with S4 fully covered.
4. **The reduction to Policy and Audit is a reduction to rule and record, not
   to state.** The state layer is not provided by either.

---

## 8. What this analysis does not establish

- It does not show that AetherMemory is independent. The remainder is
  characterized, but it may still be a feature of an existing dimension.
- It does not show that the state layer requires a **separate architectural
  dimension**. It may be a **property** of the composition, not a dimension.
- It does not resolve the structural dependency on Policy and Audit (T3).
  The analysis adopted the most favourable reading; the actual reading may be
  less favourable.
- It does not substitute for the independent review (Phase 2).

---

## 9. Consequences for the decision

M-F2 was described in `M-F1_COVERAGE_ANALYSIS.md` (Section 8) as **the
decisive condition**. This analysis does not decide it, but it narrows what a
decision would require.

To decide M-F2, one of the following is needed:

1. **An argument that the state layer is a feature of Policy, Audit, or the
   composition** — which would falsify M-F2.
2. **An argument that the state layer requires a separate dimension** — which
   would support M-F2.
3. **A demonstration that the state layer is vacuous** — that is, that
   "validity now" is fully determined by the rules and records. This is the
   strongest form of the reduction and is not addressed here.

The third is the most serious. If "validity now" is fully determined by
Policy (rules) and Audit (records), then the state layer is not a remainder
but a **derived quantity**. The analysis does not settle this. It is carried
into Phase 2 as the central question for the independent reviewer.

---

## 10. Next step

Phase 2 — Hypothesis Review. The independent reviewer is asked to assess
whether the state layer is a genuine remainder or a derived quantity. This is
the decisive question for the Phase 4 decision.

Until then, M-F2 remains **partial — remainder characterized; architectural
status open**, and the overall decision remains **(E) Undetermined
(interim)**.

---

**AetherMemory v1.0.0 — M-F2 Composition Analysis**
© 2026 Samir Baladi — Ronin Institute / Rite of Renaissance
DOI: [10.6084/m9.figshare.35069155](https://doi.org/10.6084/m9.figshare.35069155)

*Partial execution. M-F2 not falsified, not accepted. The remainder is the
state layer; its architectural status is the Phase 2 question.*
