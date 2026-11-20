# AetherMemory — M-F1 Coverage Analysis

**Failure condition under test:** M-F1 — Non-redundancy
**Status:** Partial execution (Git and Mesh only; Policy and Audit open)
**Version:** 1.0.0
**Date:** 2026-11-19
**Author:** Samir Baladi
**ORCID:** [0009-0003-8903-0029](https://orcid.org/0009-0003-8903-0029)
**License:** CC-BY-4.0
**Position in the Aether family:** Twelfth project (candidate)
**Decision:** (E) Undetermined (interim)

---

## 0. Status of this analysis

This document **executes** part of M-F1: the stage-by-stage coverage analysis
described in `FALSIFICATION/FALSIFICATION_PLAN.md` (Section 3.1).

It is **partial**. Two of the four reference dimensions — AetherPolicy and
AetherAudit — are paused at Phase 4. Their coverage cannot be assessed without
resolving their own status. The analysis therefore assesses S1–S7 against
**AetherGit** and **AetherMesh** only, and records the Policy/Audit cells as
**Open**.

The analysis does **not** decide M-F1. It records what is covered, what is
partially covered, and what is not covered, so that the eventual M-F1 decision
has a basis.

---

## 1. What M-F1 requires

M-F1 is falsified if, **for every stage S1–S7**, an existing dimension
provides the stage **without an additional layer**.

A single uncovered or partially-covered stage is sufficient to keep M-F1 open
(not falsified). This is the falsification-first direction: the condition is
tested by looking for a stage the existing dimensions do not cover.

---

## 2. Reference dimensions

| Dimension | Status | Included in this analysis |
|---|---|:-:|
| AetherGit | Foundational | ✅ Yes |
| AetherMesh | Foundational | ✅ Yes |
| AetherPolicy | Candidate, Phase 4 paused | ⏳ Open |
| AetherAudit | Candidate, Phase 4 paused | ⏳ Open |

The reference set is the one stated in the paper (Section 4.3). Its narrowness
is carried into threat T3 and is not resolved here.

---

## 3. Stage-by-stage analysis

For each stage, the table records whether AetherGit and AetherMesh cover it,
partially cover it, or do not cover it. The Policy and Audit columns are left
open.

Legend: **✔** = covered · **~** = partial · **✘** = not covered · **?** = open

| Stage | Guiding question | AetherGit | AetherMesh | AetherPolicy | AetherAudit |
|:-:|---|:-:|:-:|:-:|:-:|
| **S1** Acquisition | How is knowledge acquired? | ✘ | ✘ | ? | ? |
| **S2** Qualification | Is the source valid and trustworthy? | ✘ | ~ | ? | ? |
| **S3** Consolidation | How is duplicate or conflicting knowledge resolved? | ~ | ~ | ? | ? |
| **S4** Persistence | How is knowledge preserved across sessions? | ✔ | ✔ | ? | ? |
| **S5** Retrieval | How is knowledge retrieved by context and authority? | ~ | ✘ | ? | ? |
| **S6** Revision | How is knowledge updated or superseded? | ~ | ~ | ? | ? |
| **S7** Expiration & Forgetting | How does knowledge expire or get forgotten? | ✘ | ✘ | ? | ? |

### 3.1 Justification of each cell

**S1 — Acquisition.**
AetherGit records bytes; it does not decide what enters the memory. AetherMesh
replicates; it does not acquire. Neither dimension provides acquisition.
→ ✘ / ✘

**S2 — Qualification.**
AetherGit has no notion of source trust. AetherMesh may propagate trust
metadata but does not assess it. Neither provides qualification.
→ ✘ / ~

**S3 — Consolidation.**
AetherGit can merge branches but does not resolve **semantic** conflicts
between knowledge units. AetherMesh converges replicas but does not resolve
conflicting claims (Section 1.2 of the paper). Both are partial.
→ ~ / ~

**S4 — Persistence.**
AetherGit persists bytes across sessions (commits, tags). AetherMesh persists
replicas. Both cover persistence.
→ ✔ / ✔

**S5 — Retrieval.**
AetherGit can retrieve a specific version but not by context or authority.
AetherMesh has no retrieval model. Neither covers retrieval by scope.
→ ~ / ✘

**S6 — Revision.**
AetherGit tracks revisions of bytes; it does not mark a knowledge unit as
superseded. AetherMesh propagates revisions but does not define revision
semantics. Both are partial.
→ ~ / ~

**S7 — Expiration & Forgetting.**
AetherGit can delete files; it does not distinguish deletion from forgetting.
AetherMesh does not forget. Neither covers S7 in the sense of M5.
→ ✘ / ✘

---

## 4. What the analysis shows

### 4.1 Covered stages

Only **S4 (Persistence)** is fully covered by Git + Mesh. This is the stage
where storage and replication are strongest, and where AetherMemory is least
likely to add anything.

### 4.2 Partially covered stages

**S3 (Consolidation)**, **S5 (Retrieval)**, and **S6 (Revision)** are
partially covered. In each case, Git or Mesh provides a **mechanical** version
of the stage (merge, fetch, version) but not the **semantic** version the
lifecycle hypothesis requires (resolve conflicting claims, retrieve by scope,
mark a unit as superseded).

Whether this gap is architectural or semantic is exactly what M-F2 must
decide. M-F1 cannot settle it.

### 4.3 Uncovered stages

**S1 (Acquisition)**, **S2 (Qualification)**, and **S7 (Expiration &
Forgetting)** are **not covered** by Git or Mesh.

These three stages are the strongest candidates for the remainder that M-F2
tests.

### 4.4 The Policy and Audit columns

The two dimensions that could cover S2 (Qualification), S5 (Retrieval by
authority), and S7 (Expiration) are **AetherPolicy** and **AetherAudit** — both
paused at Phase 4.

- AetherPolicy may cover **S7** (expiration rules) and part of **S5**
  (authorization).
- AetherAudit may cover **S2** (source trust as an audit record) and part of
  **S6** (revision history).

**This is the structural dependency (T3) made concrete.** M-F1 cannot be
decided until Policy and Audit are resolved.

---

## 5. Preliminary M-F1 status

| Question | Answer |
|---|---|
| Is every stage S1–S7 covered by Git + Mesh? | **No.** S1, S2, S7 are uncovered; S3, S5, S6 are partial. |
| Is M-F1 **falsified** by Git + Mesh alone? | **No.** The condition requires *all* reference dimensions; Git + Mesh do not cover all stages. |
| Can M-F1 be **accepted**? | **No.** Policy and Audit are open. S2, S5, S7 might be covered by them. |
| **Current M-F1 status** | **Partial — open on Policy and Audit.** |

M-F1 is **not falsified** and **not accepted**. It remains **untested in full**.

---

## 6. What this analysis does establish

1. **Git + Mesh do not cover the lifecycle.** Three stages are uncovered
   (S1, S2, S7) and three are partial (S3, S5, S6).
2. **The remainder is concentrated in three stages** — acquisition,
   qualification, and expiration/forgetting — and in the semantic aspect of
   three others.
3. **The structural dependency on Policy and Audit is decisive.** The three
   uncovered stages are exactly the ones Policy and Audit might cover.
4. **M-F1 cannot be decided at Phase 0.** It requires either (a) resolving
   Policy and Audit, or (b) a stronger argument that they cannot cover these
   stages.

---

## 7. What this analysis does not establish

- It does not show that AetherMemory is independent.
- It does not show that the gap is genuine.
- It does not falsify M-F1.
- It does not accept M-F1.
- It does not resolve the structural dependency.
- It does not substitute for the independent review (Phase 2).

---

## 8. Consequences for M-F2

The M-F1 analysis narrows M-F2. The composition argument no longer needs to
address all seven stages uniformly. It must address:

- **S1, S2, S7** — the three uncovered stages, against Policy and Audit.
- **S3, S5, S6** — the three partial stages, against the semantic extension
  of Git and Mesh.
- **S4** — the one covered stage. If S4 is fully covered, AetherMemory adds
  nothing there.

M-F2 is therefore **the decisive condition**. It is the one that determines
whether the remainder is real or is a composition effect.

---

## 9. Next step

The M-F1 analysis is now partially executed. To complete it:

1. Resolve AetherPolicy (Phase 4, paused).
2. Resolve AetherAudit (Phase 4, paused).
3. Re-run this analysis with all four dimensions.

Until then, M-F1 remains **partial — open on Policy and Audit**, and the
overall decision remains **(E) Undetermined (interim)**.

---

**AetherMemory v1.0.0 — M-F1 Coverage Analysis**
© 2026 Samir Baladi — Ronin Institute / Rite of Renaissance
DOI: [10.6084/m9.figshare.35069155](https://doi.org/10.6084/m9.figshare.35069155)

*Partial execution. M-F1 not falsified, not accepted.*
