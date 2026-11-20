# AetherMemory — Roadmap

**Version:** 1.0.0
**Status:** Phase 0 (Architectural Hypothesis) — in progress.
**Decision:** (E) Undetermined (interim).
**No implementation.**
**Structural dependency:** AetherPolicy (Phase 4 paused), AetherAudit (Phase 4 paused).

---

## Phase Status

| Phase | Description | Status |
|:-:|---|---|
| 0 | Architectural Hypothesis | ✅ Complete (`ARCHITECTURAL_HYPOTHESIS.md`) |
| 1 | Responsibility Mapping | ✅ Complete (`research/RESPONSIBILITY_BOUNDARIES.md`) |
| 2 | Hypothesis Review (Independent) | ✅ Complete (Jonathan Rabe, 2026-11-19) |
| 3 | Falsification Design | ✅ Complete (`FALSIFICATION/FALSIFICATION_PLAN.md`) |
| 4 | Independence Decision | ⚠️ Interim: (E) Undetermined (`DECISIONS/INDEPENDENCE_DECISION.md`) |
| 5 | Architectural Specification | ❌ Not permitted |
| 6 | Reference Implementation | ❌ Not permitted |
| 7 | Evaluation | ❌ Not permitted |

**The investigation has not passed Phase 4.** The Phase 4 decision is interim and cannot be final until Phase 2 (independent review) is completed.

---

## Phase 0 — Architectural Hypothesis ✅ Complete

**Output:** `ARCHITECTURAL_HYPOTHESIS.md`.

The hypothesis is stated. It is falsifiable. It is not a result.

- Central question with four clauses (i–iv).
- Seven lifecycle stages (S1–S7).
- Five candidate responsibilities (M1–M5).
- Boundaries with the eleven other Aether projects.
- Structural dependency on AetherPolicy and AetherAudit declared explicitly.

---

## Phase 1 — Responsibility Mapping ✅ Complete

**Output:** `research/RESPONSIBILITY_BOUNDARIES.md`.

The boundary map records, for each of M1–M5 against each of the eleven other projects, one of four relations: Consumes, Overlaps (suspected), Distinct (hypothesis), or Open.

Four high-risk overlaps are identified:

- M2 vs AetherGovern (T5).
- M3 vs AetherPolicy.
- M4 vs AetherAudit (T3).
- M5 vs the deletion/forgetting distinction (T4).

Two relations are **Open** because of the structural dependency on AetherPolicy and AetherAudit.

---

## Phase 2 — Hypothesis Review ✅ Complete

**Output:** `REVIEW/INDEPENDENT_REVIEW.md`.

**Status:** Completed by Jonathan Rabe (2026-11-19). The reviewer confirmed the (E) Undetermined (interim) classification and recommended keeping it interim until M-F1–M-F4 are resolved.

The Phase 4 decision remains interim as per the reviewer's recommendation, because the underlying failure conditions are still untested.

---

## Phase 3 — Falsification Design ✅ Complete

**Outputs:**
- `FALSIFICATION/FALSIFICATION_PLAN.md` — the design.
- `FALSIFICATION/M-F1_COVERAGE_ANALYSIS.md` — **partial execution of M-F1**.
- `FALSIFICATION/M-F2_COMPOSITION_ANALYSIS.md` — **partial execution of M-F2**.
- `FALSIFICATION/M-F3_DECENTRALIZATION_ANALYSIS.md` — **partial execution of M-F3**.
- `FALSIFICATION/M-F4_STATUS.md` — **status declaration for M-F4**.

The plan specifies how M-F1 to M-F4 would be tested. M-F1, M-F2, and M-F3
have been partially executed. M-F4 is declared not executable at Phase 0.

- **M-F1:** partially executed. S1, S2, S7 uncovered by Git + Mesh; S3, S5,
  S6 partial; S4 covered. Policy/Audit open. Not falsified, not accepted.
- **M-F2:** partially executed. Stage A (Git + Mesh) leaves 3 full and 3
  partial remainders. Stage B (adding Policy and Audit, most favourable
  reading) leaves a remainder at 6 of 7 stages. The remainder is the **state
  layer**. Not falsified, not accepted.
- **M-F3:** partially executed. M1, M2, M4, M5 decentralizable; M3 (temporal
  validity) open on the global-clock question. Not falsified, not accepted.
- **M-F4:** not executable at Phase 0. Requires measurement, which requires
  Phase 5 and Phase 6. Not tested, not falsified, not accepted.

---

## Phase 4 — Independence Decision ⚠️ Interim (E) Undetermined

**Output:** `DECISIONS/INDEPENDENCE_DECISION.md`.

**Status:** Interim. The decision is (E) Undetermined. It is not final, because Phase 2 (Independent Review) has not been completed.

**Companion report:** `REPORTS/architectural_investigation/investigation_report.md`.

---

## Phase 5 — Architectural Specification ❌ Not permitted

**Output:** `SPECIFICATION.md`.

**Status:** Not permitted. Requires a positive Phase 4 decision.

---

## Phase 6 — Reference Implementation ❌ Not permitted

**Output:** `src/aethermemory/`, `tests/`, `experiments/`.

**Status:** Not permitted. Requires Phase 5.

---

## Phase 7 — Evaluation ❌ Not permitted

**Output:** `REPORTS/evaluation/`.

**Status:** Not permitted. Requires Phase 6.

---

## What would change the status

To move from Phase 4 (interim) to Phase 4 (final), one of the following is needed:

1. **Phase 2 completion** — an independent review of the hypothesis, the boundary map, and the falsification plan.
2. **Execution of M-F1, M-F2, M-F3** — analyses that can be carried out at Phase 3.
3. **A stronger argument** addressing M-F2 (the most fragile condition).
4. **An experiment** for M-F4 (requires Phase 5 and Phase 6, which are not permitted).
5. **Resolution of AetherPolicy or AetherAudit** — the structural dependency (T3) must be resolved for M-F2 to be settled.

Without one of these, the project remains at Phase 4 (interim), classified (E) Undetermined.

---

## What is not on this roadmap

- Any implementation before Phase 4 is positive.
- Any claim that AetherMemory is an independent dimension.
- Any renumbering of AetherGit, AetherMesh, AetherGovern, AetherPolicy, or AetherAudit.
- Any specification or protocol before Phase 5.

---

## Phase 4 outcomes

| Outcome | Meaning | Consequence |
|:-:|---|---|
| **(A) Accepted** | All four tested, none falsified, M-F4 measured. | Proceed to Phase 5. |
| **(R) Rejected** | At least one condition falsified. | Candidate rejected as a separate dimension. |
| **(F) Folded** | Remainder belongs to another dimension. | No separate dimension. |
| **(D) Deferred** | A condition cannot be tested (dependency unresolved). | Remains at Phase 4 (interim). |
| **(E) Undetermined** | Evidence insufficient to accept or reject. | **Current state.** |

---

**AetherMemory v1.0.0 — Roadmap**
© 2026 Samir Baladi — Ronin Institute / Rite of Renaissance
DOI: [10.6084/m9.figshare.35069155](https://doi.org/10.6084/m9.figshare.35069155)

*Phase 0 in progress. No implementation.*
