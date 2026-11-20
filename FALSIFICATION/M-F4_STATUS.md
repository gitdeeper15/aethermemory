# AetherMemory — M-F4 Status Declaration

**Failure condition under test:** M-F4 — Observable benefit
**Status:** Not executable at Phase 0 (requires Phase 5 and 6)
**Version:** 1.0.0
**Date:** 2026-11-19
**Author:** Samir Baladi
**ORCID:** [0009-0003-8903-0029](https://orcid.org/0009-0003-8903-0029)
**License:** CC-BY-4.0
**Position in the Aether family:** Twelfth project (candidate)
**Decision:** (E) Undetermined (interim)

---

## 0. Status of this document

This document is **not** an execution of M-F4. M-F4 cannot be executed at
Phase 0, because it requires measurement, and measurement requires Phase 5
(specification) and Phase 6 (implementation), which are not permitted.

This document is a **status declaration**. It records:

1. why M-F4 is not executable now;
2. what M-F4 would require;
3. what would be measured;
4. what a positive and a negative result would mean;
5. how M-F4 relates to M-F1, M-F2, and M-F3.

It does **not** test M-F4, does **not** report any result, and does **not**
authorize implementation or measurement.

---

## 1. Why M-F4 is not executable at Phase 0

M-F4 is the only failure condition that requires **measurement**. The other
three (M-F1, M-F2, M-F3) are **analytical** — they can be executed, in part,
by argument (as `M-F1_COVERAGE_ANALYSIS.md`,
`M-F2_COMPOSITION_ANALYSIS.md`, and `M-F3_DECENTRALIZATION_ANALYSIS.md` do).

M-F4 asks whether a **benefit can be observed** under a defined evaluation.
Observation requires:

- a **system** that exhibits the behavior (Phase 6);
- a **specification** of what the system should do (Phase 5);
- an **evaluation design** that compares the system to a baseline;
- **measurement** of the scenarios and metrics.

None of these exists at Phase 0. The evaluation design is **proposed, not
executed** (paper, Section 9). The system does not exist. The measurement
does not exist.

M-F4 is therefore **not testable** at Phase 0. This is not a weakness of the
investigation; it is a consequence of the phase order. The investigation
does not permit implementation before Phase 4 is positive, and M-F4 cannot
be tested before implementation.

---

## 2. What M-F4 would require

To test M-F4, all of the following would be required.

### 2.1 A specification (Phase 5)

The specification would define what AetherMemory does — the responsibilities
M1–M5, the lifecycle stages S1–S7, and the interfaces with the existing
dimensions. It would be the basis for the implementation.

**Status:** Not permitted. Requires a positive Phase 4 decision.

### 2.2 A reference implementation (Phase 6)

The implementation would realize the specification. It would be the system
whose behavior is measured.

**Status:** Not permitted. Requires Phase 5.

### 2.3 An evaluation design (proposed)

The evaluation design is described in the paper (Section 9) and is
**proposed, not executed**. It defines:

- **Scenarios ES1–ES7** — the situations in which the system is tested.
- **Metrics EM1 and onward** — the quantities that are measured.
- **Baselines** — the systems against which AetherMemory is compared.
- **A mapping to the failure conditions** — which metric tests which
  condition.

The design is a **proposal**. It has not been executed.

### 2.4 A baseline

The baseline is the composition of existing dimensions — Git + Mesh + Policy
+ Audit — without AetherMemory. M-F4 tests whether AetherMemory provides a
**benefit over the baseline**.

The baseline is the same composition that M-F2 analyzed. M-F2 established
that a remainder survives the composition; M-F4 would test whether closing
that remainder (with AetherMemory) yields a measurable benefit.

---

## 3. What would be measured

The evaluation design (paper, Section 9) proposes scenarios and metrics. The
following is a summary of what M-F4 would measure. It is **not** the full
design; it is a record of what the design would test.

### 3.1 Scenarios (ES1–ES7, proposed)

| # | Scenario | What it tests |
|:-:|---|---|
| **ES1** | Stale knowledge retrieval | Whether a stale fact is retrieved when it should not be. |
| **ES2** | Conflicting claims | Whether two contradictory claims are consolidated or both retained. |
| **ES3** | Scope violation | Whether a unit is retrieved by a party outside its authorized scope. |
| **ES4** | Provenance loss | Whether the source of a unit is lost across sessions. |
| **ES5** | Deletion vs forgetting | Whether deletion and forgetting are distinguished. |
| **ES6** | Decentralized convergence | Whether nodes converge on the same validity state. |
| **ES7** | Cross-session persistence | Whether knowledge persists correctly across sessions. |

The scenarios are **proposed**. They are not executed.

### 3.2 Metrics (EM1 and onward, proposed)

| # | Metric | What it measures |
|:-:|---|---|
| **EM1** | Stale retrieval rate | Fraction of retrievals that return a stale unit. |
| **EM2** | Conflict resolution accuracy | Fraction of conflicts resolved correctly. |
| **EM3** | Scope violation rate | Fraction of retrievals outside authorized scope. |
| **EM4** | Provenance completeness | Fraction of units with a complete derivation chain. |
| **EM5** | Deletion/forgetting distinction | Whether the two are distinguished in practice. |
| **EM6** | Convergence time | Time for nodes to converge on a validity state. |
| **EM7** | Persistence accuracy | Fraction of units correctly persisted across sessions. |

The metrics are **proposed**. They are not measured.

### 3.3 Baselines (proposed)

| # | Baseline | Description |
|:-:|---|---|
| **B1** | Git + Mesh only | The foundational composition, without Policy, Audit, or AetherMemory. |
| **B2** | Git + Mesh + Policy + Audit | The full composition, without AetherMemory. |
| **B3** | AetherMemory + composition | The candidate, on top of the composition. |

M-F4 would compare **B3** to **B2**. The comparison is what would show a
benefit, if any.

---

## 4. What a positive and a negative result would mean

### 4.1 A positive result

A positive result — a measurable benefit of B3 over B2 — would **support**
M-F4. It would not by itself accept AetherMemory as an independent dimension;
it would be one of four conditions (M-F1 to M-F4) that must hold.

Even a positive M-F4 would require M-F1, M-F2, and M-F3 to be settled. M-F4
is **necessary, not sufficient**.

### 4.2 A negative result

A negative result — no measurable benefit of B3 over B2 — would **falsify**
M-F4. A falsified M-F4 is sufficient to reject AetherMemory as a separate
dimension, per the decision rule (paper, Section 6.4).

A negative M-F4 would not necessarily mean the investigation was wasted: it
would show that the remainder identified by M-F2 is a **derived quantity**,
not an architectural layer. That is a result in itself.

---

## 5. Relation to M-F1, M-F2, and M-F3

The four failure conditions are not independent of one another. M-F4 is the
**last** condition, and it depends on the others.

| Condition | Status | Relation to M-F4 |
|:-:|---|---|
| **M-F1** | Partial (Git + Mesh do not cover S1, S2, S7) | M-F4 would test whether covering these stages yields a benefit. |
| **M-F2** | Partial (remainder = state layer) | M-F4 would test whether the state layer, if provided, yields a benefit. |
| **M-F3** | Partial (M3 open) | M-F4 would test whether a decentralized M3 yields a benefit over a centralized one (or over none). |
| **M-F4** | Not executable | — |

M-F4 is the **empirical test** of what M-F1, M-F2, and M-F3 establish
**analytically**. The analytical results do not substitute for the empirical
test; the empirical test does not substitute for the analytical results.

---

## 6. Why this is not a failure

M-F4 being not executable at Phase 0 is **not a failure** of the
investigation. It is a consequence of the phase order:

- The investigation does not permit implementation before Phase 4 is
  positive.
- M-F4 cannot be tested before implementation.
- Therefore M-F4 cannot be tested before Phase 4 is positive.

This is a **deliberate design choice** of the falsification-first
methodology: the investigation does not claim a benefit before it has a
system to measure. The alternative — claiming a benefit on the basis of an
argument — would violate the methodology.

---

## 7. What would change the status

To make M-F4 executable, all of the following would be required, in order:

1. **Phase 4 is positive** — AetherMemory is accepted as an independent
   dimension.
2. **Phase 5 — Specification** — the specification is written.
3. **Phase 6 — Reference Implementation** — the implementation is built.
4. **Evaluation** — the evaluation design (Section 9 of the paper) is
   executed.

Without all four, M-F4 remains **not executable**.

---

## 8. Summary

| Question | Answer |
|---|---|
| Is M-F4 executable at Phase 0? | **No.** It requires Phase 5 and Phase 6. |
| Has M-F4 been tested? | **No.** No measurement exists. |
| Is M-F4 falsified? | **No.** It has not been tested. |
| Is M-F4 accepted? | **No.** It has not been tested. |
| **Current M-F4 status** | **Not executable at Phase 0.** |

M-F4 remains **untested**. The overall decision remains **(E) Undetermined
(interim)**.

---

## 9. Next step

Phase 2 — Hypothesis Review. The independent reviewer is asked to assess
whether M-F4 is correctly declared **not executable** at Phase 0, and whether
the evaluation design (paper, Section 9) is adequate to test it once Phase 5
and Phase 6 are permitted.

Until then, M-F4 remains **not executable**, and the overall decision remains
**(E) Undetermined (interim)**.

---

**AetherMemory v1.0.0 — M-F4 Status Declaration**
© 2026 Samir Baladi — Ronin Institute / Rite of Renaissance
DOI: [10.6084/m9.figshare.35069155](https://doi.org/10.6084/m9.figshare.35069155)

*M-F4 is not executable at Phase 0. No measurement exists. Not tested, not
falsified, not accepted.*
