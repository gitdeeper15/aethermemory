# AetherMemory — Falsification Plan

**Status:** Phase 3 — Falsification Design (Initial Draft)
**Version:** 1.0.0
**Date:** 2026-11-19
**Author:** Samir Baladi
**ORCID:** [0009-0003-8903-0029](https://orcid.org/0009-0003-8903-0029)
**License:** CC-BY-4.0
**Position in the Aether family:** Twelfth project (candidate)
**Decision:** (E) Undetermined (interim)

---

## 0. Status of this document

This document specifies **how** the four failure conditions (M-F1 to M-F4)
would be tested. It is a **Phase 3 deliverable**.

It does **not**:

- run any test;
- report any result;
- claim that any condition has been examined;
- authorize implementation or experimentation.

**All four failure conditions remain untested.** This document only describes
the procedure by which they could be tested, and the decision rule that would
apply once they are.

---

## 1. Principles

The plan follows the falsification-first methodology stated in the paper
(Section 6). Four principles govern it.

### 1.1 State failure before success

Each condition is stated as a **failure condition**: a result that would
count against AetherMemory. The investigation does not look for confirmation;
it looks for the conditions under which the candidate fails.

### 1.2 One condition, one question

Each failure condition answers exactly one clause of the central question
(Section 4 of the paper). A condition that answers more than one clause is
poorly stated and is revised.

### 1.3 No condition is tested by argument alone

A failure condition is **tested** only when there is a procedure, a result,
and a record. Reading the literature is not a test. A test requires an
artifact (an analysis, a construction, a measurement) that another party
could reproduce.

### 1.4 A negative result is a result

If any failure condition is falsified — that is, if the candidate fails it —
the candidate is rejected as a separate dimension, and the content may survive
as a feature of another dimension. This is a legitimate outcome, not a failure
of the investigation.

---

## 2. The four failure conditions

The four conditions are restated from the paper (Section 6.3) and the README.

| ID | Clause of the central question | Condition under test | Current status |
|:-:|---|---|:-:|
| **M-F1** | (i) Non-redundancy | The lifecycle is not already covered by AetherGit, AetherMesh, AetherPolicy, or AetherAudit. | 🟡 **Partially executed** (Git + Mesh); Policy/Audit open. See `M-F1_COVERAGE_ANALYSIS.md`. |
| **M-F2** | (ii) Non-decomposition | The lifecycle does not decompose into a composition of Git, Mesh, Policy, and Audit; a remainder survives the composition. | 🟡 **Partially executed**; remainder characterized as the state layer. See `M-F2_COMPOSITION_ANALYSIS.md`. |
| **M-F3** | (iii) Decentralizability | No central memory authority is required. | 🟡 **Partially executed**; M3 (temporal validity) open. See `M-F3_DECENTRALIZATION_ANALYSIS.md`. |
| **M-F4** | (iv) Observable benefit | A benefit can be observed under a defined evaluation. | ⚫ **Not executable at Phase 0** (requires Phase 5 and 6). See `M-F4_STATUS.md`. |

The **decision rule** (Section 6.4 of the paper): a positive answer requires
all four to be tested with none falsified, with M-F4 supported by measured
results. A negative answer on any one is sufficient to reject the candidate as
a separate dimension.

---

## 3. How each condition would be examined

For each condition, the plan states (a) the artifact that would count as a
test, (b) the result that would falsify the condition, and (c) what remains
open after the test.

### 3.1 M-F1 — Non-redundancy

**Question.** Is the lifecycle (S1–S7) already covered by AetherGit,
AetherMesh, AetherPolicy, or AetherAudit?

**Artifact.** A stage-by-stage coverage analysis: for each of S1–S7, a record
of which existing dimension (if any) provides the stage, with a citation to
the relevant Aether paper.

**Falsification.** M-F1 is falsified if, for every stage S1–S7, an existing
dimension is shown to provide the stage **without an additional layer**.

**What remains open.** Even if M-F1 holds (no single dimension covers every
stage), the lifecycle may still decompose — which is M-F2.

**Dependency.** This analysis depends on the resolution of AetherPolicy and
AetherAudit (T3). If either is folded into another dimension, the coverage
changes.

### 3.1.1 Partial execution record

M-F1 has been **partially executed** in `FALSIFICATION/M-F1_COVERAGE_ANALYSIS.md`.
The analysis assesses S1–S7 against AetherGit and AetherMesh only, because
AetherPolicy and AetherAudit are paused at Phase 4.

Summary of findings:

- **S4 (Persistence)** is fully covered by Git + Mesh.
- **S1 (Acquisition), S2 (Qualification), S7 (Expiration & Forgetting)**
  are not covered by Git or Mesh.
- **S3 (Consolidation), S5 (Retrieval), S6 (Revision)** are partially
  covered (mechanical, not semantic).
- **AetherPolicy and AetherAudit** could cover S1, S2, S5, and S7; their
  status is Open.

M-F1 is therefore **not falsified and not accepted**. It remains open on
Policy and Audit. The analysis does not decide M-F1; it narrows M-F2
(Section 8 of the analysis).

### 3.2 M-F2 — Non-decomposition

**Question.** Does the lifecycle decompose into Git + Mesh + Policy + Audit?

**Artifact.** A composition argument: a construction that combines the four
dimensions and shows whether a remainder survives.

**Falsification.** M-F2 is falsified if the composition covers S1–S7 with
**no remainder** — that is, if every stage is provided by the composition.

**What remains open.** If a remainder survives, it must be characterized:
is it a new responsibility (M1–M5), or is it an interaction effect that
belongs to the composition?

**Dependency.** This is the most fragile condition (threat T3). The
composition contains AetherPolicy and AetherAudit, both paused at Phase 4.

### 3.2.1 Partial execution record

M-F2 has been **partially executed** in
`FALSIFICATION/M-F2_COMPOSITION_ANALYSIS.md`. The analysis builds the
composition in two stages:

- **Stage A (Git + Mesh):** three full remainders (S1, S2, S7) and three
  partial remainders (S3, S5, S6).
- **Stage B (Git + Mesh + Policy + Audit, most favourable reading):** a
  remainder survives at six of seven stages (all but S4).

Summary of findings:

- **The remainder is the state layer** — the state of knowledge at a moment,
  distinct from rules (Policy), records (Audit), bytes (Git), and replicas
  (Mesh).
- The remainder is **not a missing function**; it is a missing **layer**.
- Whether the state layer is an **independent dimension**, a **feature of the
  composition**, or a **derived quantity** is left to Phase 2.

M-F2 is therefore **not falsified and not accepted**. The decisive question
for Phase 2 is whether "validity now" is fully determined by Policy (rules)
and Audit (records). If it is, the state layer is derived and M-F2 is
falsified.

### 3.3 M-F3 — Decentralizability

**Question.** Does lifecycle integrity require a central memory authority?

**Artifact.** A design argument or a construction showing whether the
responsibilities M1–M5 can be discharged without a central authority, relying
on AetherMesh for distribution.

**Falsification.** M-F3 is falsified if at least one of M1–M5 **requires** a
central authority (for example, a global clock, a single index, or a central
arbiter of validity).

**What remains open.** If M-F3 holds, the result does not show that
decentralization is efficient — only that no central authority is required.

### 3.3.1 Partial execution record

M-F3 has been **partially executed** in
`FALSIFICATION/M-F3_DECENTRALIZATION_ANALYSIS.md`. The analysis assesses the
five responsibilities (M1–M5) against AetherMesh.

Summary of findings:

- **M1, M2, M4, M5** are decentralizable without a central authority, under
  stated assumptions.
- **M3 (temporal validity)** is **open**: if a decentralized clock is
  insufficient, M3 requires a global clock and M-F3 is falsified.
- Three reservations remain: M2 (local authorization), M4 (decentralized
  audit recorder), M5 (eventual forgetting).

M-F3 is therefore **not falsified and not accepted**. The decisive question
is whether temporal validity can be enforced with a decentralized clock.

### 3.4 M-F4 — Observable benefit

**Question.** Can a benefit be observed under a defined evaluation?

**Artifact.** A defined evaluation (Section 9 of the paper) with scenarios
ES1–ES7, metrics EM1 and onward, and a mapping to the failure conditions.
The evaluation is **proposed, not executed**.

**Falsification.** M-F4 is falsified if, under the defined evaluation, no
measurable benefit is observed over the existing dimensions.

**What remains open.** M-F4 is the only condition that requires measurement.
Without an experiment, M-F4 cannot be tested. Phase 5 and Phase 6 are not
permitted until Phase 4 is positive.

---

### 3.4.1 Status record

M-F4 is **not executable at Phase 0**. It requires measurement, and
measurement requires Phase 5 (specification) and Phase 6 (implementation),
which are not permitted. See `FALSIFICATION/M-F4_STATUS.md`.

The evaluation design (paper, Section 9) is **proposed, not executed**. It
defines scenarios ES1–ES7, metrics EM1 and onward, and baselines B1–B3, but
none has been run.

M-F4 is therefore **not tested, not falsified, and not accepted**. It remains
the last condition to be settled, after Phase 4 is positive.

## 4. Decision rule and outcomes

The decision rule is stated in the paper (Section 6.4) and is restated here
for completeness.

| Outcome | Condition | Consequence |
|:-:|---|---|
| **(A) Accepted** | All four tested, none falsified, M-F4 supported by measured results. | AetherMemory proceeds to Phase 5 (specification). |
| **(R) Rejected** | At least one condition falsified. | The candidate is rejected as a separate dimension; the content may survive as a feature of another dimension. |
| **(F) Folded** | The remainder is shown to belong to another dimension. | The candidate is folded; no separate dimension. |
| **(D) Deferred** | A condition cannot be tested because a dependency is unresolved. | The candidate remains at Phase 4 (interim). |
| **(E) Undetermined** | Evidence is insufficient to accept and insufficient to reject. | **Current state.** Phase 0. |

The current classification is **(E) Undetermined (interim)**. No condition has
been tested.

---

## 5. What would change the classification

To move from (E) to (A), (R), (F), or (D), one of the following is needed:

1. **M-F1 analysis** — a stage-by-stage coverage analysis against the four
   dimensions.
2. **M-F2 analysis** — a composition argument.
3. **M-F3 analysis** — a decentralization argument.
4. **M-F4 measurement** — requires Phase 5 and Phase 6, which are not
   permitted.
5. **Resolution of AetherPolicy or AetherAudit** — the structural dependency
   (T3) must be resolved before M-F2 can be settled.

Without one of these, the project remains at Phase 4 (interim), classified
(E) Undetermined.

---

## 6. What this plan does not do

- It does not test any condition.
- It does not report any result.
- It does not claim that any condition is likely to hold or fail.
- It does not authorize implementation, experimentation, or measurement.
- It does not resolve the structural dependency on AetherPolicy and
  AetherAudit.

---

## 7. Relation to the evaluation design

The evaluation design (Section 9 of the paper, proposed not executed) is the
only path to M-F4. The scenarios ES1–ES7 and metrics EM1 and onward are
described there and are **not** repeated here. This plan only states that
M-F4 requires the evaluation to be executed, and that execution requires
Phase 5 and Phase 6.

---

## 8. Next step

Phase 4 — Independence Decision. The decision record
(`DECISIONS/INDEPENDENCE_DECISION.md`) restates the current classification
(E) Undetermined (interim), names the evidence that is missing, and states
that no condition has been tested.

---

**AetherMemory v1.0.0 — Falsification Plan**
© 2026 Samir Baladi — Ronin Institute / Rite of Renaissance
DOI: [10.6084/m9.figshare.35069155](https://doi.org/10.6084/m9.figshare.35069155)

*Phase 3 deliverable. The plan describes how to test; it does not test.*
