# AetherMemory — Responsibility Boundaries

**Status:** Phase 1 — Responsibility Mapping (Initial Draft)
**Version:** 1.0.0
**Date:** 2026-11-19
**Author:** Samir Baladi
**ORCID:** [0009-0003-8903-0029](https://orcid.org/0009-0003-8903-0029)
**License:** CC-BY-4.0
**Position in the Aether family:** Twelfth project (candidate)
**Decision:** (E) Undetermined (interim)

---

## 0. Status of this document

This document maps the **initial boundaries** between the five candidate
responsibilities of AetherMemory (M1–M5) and the eleven other projects of the
Aether family. It is a **Phase 1 deliverable**.

It does **not**:

- claim that the boundaries are sufficient;
- claim that any responsibility is independent;
- claim that the mapping is complete;
- claim that AetherMemory is a confirmed dimension;
- authorize specification or implementation.

The mapping is stated so that it can be reviewed (Phase 2), falsified (Phase 3),
and decided upon (Phase 4). Every boundary below is a **hypothesis**, not a
result.

---

## 1. Purpose and method

### 1.1 Purpose

The central question of AetherMemory (Section 2) presupposes that five
responsibilities (M1–M5) exist and that they are not fully carried by the
existing dimensions. Phase 1 does not test that presupposition. It only
records, dimension by dimension, **where the contact surfaces are** and **what
kind of overlap is suspected**.

The output is a boundary map, not a decision.

### 1.2 Method

For each of the five responsibilities (M1–M5) and for each of the eleven other
projects, the map records one of four relations:

| Relation | Meaning |
|:-:|---|
| **Consumes** | AetherMemory depends on this dimension but does not provide it. |
| **Overlaps (suspected)** | The dimension may already provide part or all of the responsibility; the overlap is a reduction risk. |
| **Distinct (hypothesis)** | The responsibility is not carried by the dimension, as far as the author's present reading goes. |
| **Open** | The relation cannot be classified without resolving a structural dependency. |

Every relation marked **Overlaps (suspected)** or **Open** is a candidate
reduction. These are carried into the falsification conditions (Section 6 of
the paper, M-F1 to M-F4) and into threat T3 (structural dependency).

### 1.3 What is not done here

- No test is run.
- No experiment is designed (that is Phase 3).
- No independence decision is made (that is Phase 4).
- No interface, schema, or protocol is proposed.

---

## 2. The five responsibilities (restated)

The five responsibilities are restated here for reference. Their definitions
are the working definitions of the paper (Section 5.2, Table 3).

| ID | Responsibility | Statement (hypothesis) | Principal reduction risk |
|:-:|---|---|---|
| **M1** | Memory Lifecycle Integrity | Preserving the integrity of knowledge from acquisition to expiration. | May be a property of M2–M5 taken together; composition of Policy and Audit (T3). |
| **M2** | Scope-Bounded Retrieval | Ensuring knowledge is only retrieved within its authorized scope. | May reduce to AetherGovern (T5). |
| **M3** | Temporal Validity | Ensuring knowledge is only used while it is valid. | Expiration rules may belong to AetherPolicy. |
| **M4** | Provenance Tracking | Preserving the source and derivation chain of every knowledge unit. | May reduce to AetherAudit. |
| **M5** | Forgetting Semantics | Distinguishing deletion (data removed) from forgetting (knowledge invalidated). | May be semantic: deletion plus audit plus retention rule (T4). |

---

## 3. Boundary map: M1–M5 against the seven foundational dimensions

### 3.1 AetherGit (Storage)

| Responsibility | Relation | Note |
|:-:|:-:|---|
| **M1** | Open | AetherGit stores bytes and versions. Whether versioned storage already preserves lifecycle integrity is the M-F1 question and is not resolved. |
| **M2** | Consumes | Scope-bounded retrieval may be enforced against stored data; storage does not define scope. |
| **M3** | Consumes | Temporal validity may be encoded as metadata in stored units; storage does not enforce it. |
| **M4** | Overlaps (suspected) | Git history is a derivation chain. Whether it is a *provenance* chain in the sense of M4 is open. |
| **M5** | Distinct (hypothesis) | Storage deletes data. It does not distinguish deletion from forgetting. |

### 3.2 AetherFlow (Integration)

| Responsibility | Relation | Note |
|:-:|:-:|---|
| **M1** | Distinct (hypothesis) | Integration is transport, not lifecycle. |
| **M2** | Consumes | Knowledge enters through Flow; scope is not defined by Flow. |
| **M3** | Distinct (hypothesis) | Flow does not evaluate validity. |
| **M4** | Consumes | Flow events may carry provenance metadata; Flow does not preserve it as a chain. |
| **M5** | Distinct (hypothesis) | Flow does not forget. |

### 3.3 AetherProof (Verification)

| Responsibility | Relation | Note |
|:-:|:-:|---|
| **M1** | Consumes | Qualification (S2) may consume verification primitives. |
| **M2** | Distinct (hypothesis) | Proof is about claims, not about scope of retrieval. |
| **M3** | Overlaps (suspected) | A proof may attest validity at a time; whether that is temporal validity is open. |
| **M4** | Overlaps (suspected) | A proof is part of a derivation chain; whether it *is* M4 is open. |
| **M5** | Distinct (hypothesis) | Proof does not forget. |

### 3.4 AetherMesh (Decentralization)

| Responsibility | Relation | Note |
|:-:|:-:|---|
| **M1** | Open | M-F3 (decentralizability) asks whether lifecycle integrity survives distribution. Not resolved. |
| **M2** | Distinct (hypothesis) | Mesh converges replicas; it does not define authorized scope. |
| **M3** | Overlaps (suspected) | Convergence of data is not coherence of validity (Section 1.2 of the paper). |
| **M4** | Overlaps (suspected) | Replication history is not provenance; the distinction is open. |
| **M5** | Distinct (hypothesis) | Mesh does not distinguish deletion from forgetting. |

### 3.5 AetherGovern (Governance)

| Responsibility | Relation | Note |
|:-:|:-:|---|
| **M1** | Distinct (hypothesis) | Governance issues authority; it does not preserve lifecycle integrity. |
| **M2** | **Overlaps (suspected)** | This is threat **T5**. If "authorized scope" is an authorization decision, M2 may reduce to AetherGovern. |
| **M3** | Consumes | Validity rules may be issued by Governance; enforcement is M3. |
| **M4** | Distinct (hypothesis) | Governance does not record provenance. |
| **M5** | Open | Forgetting may be expressible as a governance policy; open question Q2. |

### 3.6 AetherRuntime (Runtime Assurance)

| Responsibility | Relation | Note |
|:-:|:-:|---|
| **M1** | Distinct (hypothesis) | Runtime assurance is about execution, not persistent knowledge. |
| **M2** | Consumes | Runtime may enforce retrieval scope at execution time; it does not define it. |
| **M3** | Consumes | Runtime may check validity at use time; the validity record is M3. |
| **M4** | Distinct (hypothesis) | Runtime does not preserve provenance chains. |
| **M5** | Distinct (hypothesis) | Runtime does not forget. |

### 3.7 AetherOrchestrate (Orchestration)

| Responsibility | Relation | Note |
|:-:|:-:|---|
| **M1** | Distinct (hypothesis) | Orchestration coordinates operations; it does not preserve lifecycle integrity. |
| **M2** | Consumes | Orchestration may sequence retrieval calls; it does not define scope. |
| **M3** | Consumes | Orchestration may schedule revision; it does not define validity. |
| **M4** | Distinct (hypothesis) | Orchestration does not preserve provenance. |
| **M5** | Distinct (hypothesis) | Orchestration does not forget. |

---

## 4. Boundary map: M1–M5 against the four candidates

### 4.1 AetherIdentity (Identity — independence unresolved)

| Responsibility | Relation | Note |
|:-:|:-:|---|
| **M1** | Distinct (hypothesis) | Identity does not preserve lifecycle integrity. |
| **M2** | Consumes | Scope may be expressed in terms of identity; identity does not define scope. |
| **M3** | Distinct (hypothesis) | Identity does not evaluate validity. |
| **M4** | Consumes | Provenance attributes to an identity; identity does not preserve the chain. |
| **M5** | Distinct (hypothesis) | Identity does not forget. |

### 4.2 AetherPolicy (Policy Lifecycle — Phase 4 paused)

| Responsibility | Relation | Note |
|:-:|:-:|---|
| **M1** | **Open** | **Structural dependency.** If lifecycle rules belong to Policy, M1 may reduce. Boundary depends on AetherPolicy's resolution. |
| **M2** | Open | Scope rules may be policy; enforcement may be M2. |
| **M3** | **Overlaps (suspected)** | Expiration rules may belong to AetherPolicy (Table 3). |
| **M4** | Consumes | Retention/provenance policies may be issued by Policy; the chain is M4. |
| **M5** | **Open** | Forgetting may be expressible as a policy. Open question Q2. |

### 4.3 AetherAudit (Audit and Evidence — Phase 4 paused)

| Responsibility | Relation | Note |
|:-:|:-:|---|
| **M1** | **Open** | **Structural dependency.** Audit records may already cover lifecycle history. |
| **M2** | Consumes | Audit may record who retrieved what; it does not define scope. |
| **M3** | Consumes | Audit may record validity checks; it does not define validity. |
| **M4** | **Overlaps (suspected)** | Provenance may reduce to Audit. This is threat **T3**. |
| **M5** | **Open** | Forgetting with provenance preserved may be an audit record. Open question Q3. |

### 4.4 AetherHuman (Human Participation — Phase 4 paused)

| Responsibility | Relation | Note |
|:-:|:-:|---|
| **M1** | Distinct (hypothesis) | Human participation is not lifecycle integrity. |
| **M2** | Consumes | Humans may be subjects of scope; they do not define it. |
| **M3** | Distinct (hypothesis) | Human participation does not evaluate validity. |
| **M4** | Consumes | Humans may be sources in a provenance chain; the chain is M4. |
| **M5** | Distinct (hypothesis) | Human participation does not forget. |

---

## 5. Summary matrix

Legend: **C** = Consumes · **O** = Overlaps (suspected) · **D** = Distinct
(hypothesis) · **?** = Open

| Dimension | M1 | M2 | M3 | M4 | M5 |
|:-:|:-:|:-:|:-:|:-:|:-:|
| AetherGit | ? | C | C | O | D |
| AetherFlow | D | C | D | C | D |
| AetherProof | C | D | O | O | D |
| AetherMesh | ? | D | O | O | D |
| AetherGovern | D | **O** | C | D | ? |
| AetherRuntime | D | C | C | D | D |
| AetherOrchestrate | D | C | C | D | D |
| AetherIdentity | D | C | D | C | D |
| **AetherPolicy** | **?** | ? | **O** | C | **?** |
| **AetherAudit** | **?** | C | C | **O** | **?** |
| AetherHuman | D | C | D | C | D |

The matrix is the author's reading. It is not a verified assessment. It is the
basis of Figure 8 (preliminary coverage matrix) and of the reservations on
M-F1 and M-F2.

---

## 6. The four high-risk overlaps

Four overlaps are singled out because they are the most likely reductions.

### 6.1 M2 vs AetherGovern (T5)

M2 is stated in terms of "authorized scope". If authorization is issued by
AetherGovern, then M2 may be a consumer of AetherGovern rather than an
independent responsibility. **This is threat T5 and a reservation on M-F1.**

### 6.2 M3 vs AetherPolicy

Expiration rules may belong to AetherPolicy. If so, M3 is a consumer of
AetherPolicy. **This is the most direct consequence of the structural
dependency on AetherPolicy (T3).**

### 6.3 M4 vs AetherAudit

Provenance may reduce to Audit. If Audit already records the derivation chain
of every unit, M4 is a consumer of Audit. **This is threat T3 and a
reservation on M-F2.**

### 6.4 M5 vs the deletion/forgetting distinction (T4)

The distinction between deletion and forgetting may be **semantic**, not
architectural. If so, M5 is not a responsibility but a convention. **This is
threat T4 and a reservation on P2.**

---

## 7. Open questions carried forward

The following open questions (from Appendix B of the hypothesis) bear directly
on the boundary map and are carried into Phase 2:

- **Q2.** Can "forgetting" be expressed as a policy in AetherGovern, or does
  it require a new primitive?
- **Q3.** Can "provenance" be expressed as an audit record in AetherAudit, or
  does it require a new primitive?
- **Q4.** Can "scope-bounded retrieval" be expressed as an authorization
  decision in AetherGovern?
- **Q5.** Does the structural dependency on AetherPolicy and AetherAudit
  undermine the independence of AetherMemory?
- **Q7–Q10.** Minimal interfaces with Git, Mesh, Policy, Audit (not defined
  here; out of scope for Phase 1).

---

## 8. What this document establishes

It establishes only that:

1. A boundary map can be drawn for M1–M5 against the eleven projects.
2. Four overlaps are the most likely reductions (Section 6).
3. Two relations are **Open** because of the structural dependency on
   AetherPolicy and AetherAudit (Section 4.2, 4.3).
4. The mapping is sufficient to **design** falsification conditions (Phase 3),
   not to **decide** independence (Phase 4).

It does not establish that the boundaries are sufficient, that any
responsibility is independent, or that the gap is genuine.

---

## 9. Next step

Phase 2 — Hypothesis Review. An independent reviewer is asked to assess
whether the boundary map is (a) complete enough to review, (b) fair to the
existing dimensions, and (c) honest about the open relations.

---

**AetherMemory v1.0.0 — Responsibility Boundaries**
© 2026 Samir Baladi — Ronin Institute / Rite of Renaissance
DOI: [10.6084/m9.figshare.35069155](https://doi.org/10.6084/m9.figshare.35069155)

*Phase 1 deliverable. Boundaries are hypotheses, not results.*
