# AetherMemory — Independent Review Protocol

**Status:** Phase 2 — Protocol (Complete)
**Version:** 1.0.0
**Date:** 2026-11-19
**Author:** Samir Baladi
**License:** CC-BY-4.0

---

## 0. Purpose

This protocol states how an independent review of AetherMemory should be
conducted. It is written **before** the review, so that the review cannot be
shaped after the fact by its outcome.

The protocol does **not** presuppose the outcome. A review that concludes
"the current classification (E) is correct" and a review that concludes "the
classification should change" are both valid outcomes.

---

## 1. Independence requirement

The reviewer must be independent of the author. Independence means:

- the reviewer is not the author;
- the reviewer has not contributed to the hypothesis, the boundary map, or
  the falsification plan;
- the reviewer has no stake in the outcome of the decision.

The reviewer declares independence in `INDEPENDENT_REVIEW.md` (Section 2.1).

---

## 2. Artifacts to be reviewed

The reviewer reads, in order:

1. `README.md` — project overview and status.
2. `ARCHITECTURAL_HYPOTHESIS.md` — the hypothesis and its four clauses.
3. `research/RESPONSIBILITY_BOUNDARIES.md` — the boundary map.
4. `FALSIFICATION/FALSIFICATION_PLAN.md` — the four failure conditions.
5. `DECISIONS/INDEPENDENCE_DECISION.md` — the current classification.

The reviewer may read any other artifact in the repository. The five above
are the minimum.

---

## 3. Questions the review must answer

The reviewer answers the following questions. Each answer is supported by a
reference to the artifact and, where possible, to a specific section.

### 3.1 On the hypothesis

- **H1.** Is the central question stated without circularity?
- **H2.** Do the four clauses (i–iv) map cleanly to the four failure
  conditions (M-F1–M-F4)?
- **H3.** Is any claim in the hypothesis stated more strongly than the
  evidence supports?

### 3.2 On the boundary map

- **B1.** Is the map fair to the existing dimensions? In particular, is
  AetherGit, AetherMesh, AetherPolicy, or AetherAudit treated too lightly?
- **B2.** Are the four high-risk overlaps (Section 6 of the boundary
  document) correctly identified?
- **B3.** Are the two **Open** relations (M1 vs Policy, M1 vs Audit) honestly
  open, or do they conceal a reduction?

### 3.3 On the falsification plan

- **F1.** Is each failure condition stated so that it can fail?
- **F2.** Is the decision rule (all four tested, none falsified, M-F4
  measured) adequate?
- **F3.** Is the plan free of a path by which the candidate cannot fail?

### 3.4 On the decision

- **D1.** Is (E) Undetermined (interim) the correct classification given the
  evidence?
- **D2.** Is the decision final or interim, and is that distinction stated
  correctly?
- **D3.** Does the decision record overstate or understate the evidence?

---

## 4. Format of the review

The reviewer completes `INDEPENDENT_REVIEW.md` with:

1. **Reviewer identity and independence declaration.**
2. **Artifacts reviewed** (checklist).
3. **Answers to H1–H3, B1–B3, F1–F3, D1–D3.**
4. **A recommendation**, one of:
   - (a) accept the current classification (E);
   - (b) recommend a change of classification, with reasons;
   - (c) recommend revision of an artifact before a final decision.
5. **A statement of what the reviewer did not review.**

---

## 5. What the review is not

- It is not a peer review for publication.
- It is not an implementation review.
- It is not a decision; it informs the Phase 4 decision.
- It is not binding on the author, but a final Phase 4 decision that departs
  from the review's recommendation must record why.

---

## 6. Conflict of interest

A reviewer with a conflict of interest (for example, a stake in AetherPolicy
or AetherAudit) must declare it. A declared conflict does not automatically
disqualify the reviewer, but it is recorded in `INDEPENDENT_REVIEW.md`.

---

**AetherMemory v1.0.0 — Independent Review Protocol**
© 2026 Samir Baladi — Ronin Institute / Rite of Renaissance
DOI: [10.6084/m9.figshare.35069155](https://doi.org/10.6084/m9.figshare.35069155)
