# AetherMemory — M-F3 Decentralization Analysis

**Failure condition under test:** M-F3 — Decentralizability
**Status:** Partial execution (Mesh assessment full; Policy/Audit conditional)
**Version:** 1.0.0
**Date:** 2026-11-19
**Author:** Samir Baladi
**ORCID:** [0009-0003-8903-0029](https://orcid.org/0009-0003-8903-0029)
**License:** CC-BY-4.0
**Position in the Aether family:** Twelfth project (candidate)
**Decision:** (E) Undetermined (interim)

---

## 0. Status of this analysis

This document **executes** part of M-F3: the decentralization argument
described in `FALSIFICATION/FALSIFICATION_PLAN.md` (Section 3.3).

It is **partial**, for the same reason M-F1 and M-F2 are partial:
AetherPolicy and AetherAudit are paused at Phase 4. Their contribution to
decentralization cannot be fixed. The analysis therefore assesses the five
responsibilities (M1–M5) against **AetherMesh** (foundational, fully
assessable), and records the Policy and Audit contributions conditionally.

The analysis does **not** decide M-F3. It records which responsibilities
require a central authority, which do not, and which are open.

---

## 1. What M-F3 requires

M-F3 is falsified if **at least one** of M1–M5 **requires** a central
authority — for example:

- a global clock (a single source of "now");
- a single index (a single directory of all knowledge units);
- a central arbiter of validity (a single authority that decides what is
  valid);
- a central arbiter of scope (a single authority that decides who may
  retrieve what).

If no responsibility requires a central authority, M-F3 is not falsified.
This is the falsification-first direction: the condition is tested by looking
for a required central authority, not by asserting decentralization.

---

## 2. The five responsibilities (restated)

| ID | Responsibility | Statement (hypothesis) |
|:-:|---|---|
| **M1** | Memory Lifecycle Integrity | Preserving the integrity of knowledge from acquisition to expiration. |
| **M2** | Scope-Bounded Retrieval | Ensuring knowledge is only retrieved within its authorized scope. |
| **M3** | Temporal Validity | Ensuring knowledge is only used while it is valid. |
| **M4** | Provenance Tracking | Preserving the source and derivation chain of every knowledge unit. |
| **M5** | Forgetting Semantics | Distinguishing deletion (data removed) from forgetting (knowledge invalidated). |

---

## 3. What AetherMesh provides

AetherMesh is the foundational decentralization dimension. It provides:

- **Replication** — every node holds a replica of the state.
- **Convergence** — replicas converge to the same state (CRDTs, consensus,
  or gossip, depending on the AetherMesh design).
- **No central authority** — there is no single node that all others depend
  on.

What AetherMesh does **not** provide:

- **Semantic coherence** — convergence of data is not coherence of claims
  (Section 1.2 of the paper).
- **Validity** — Mesh converges on the state, not on whether the state is
  valid.
- **Scope** — Mesh distributes; it does not decide who may read what.

The distinction is the same one M-F2 established: Mesh provides the **data
layer**, not the **state layer**.

---

## 4. Responsibility-by-responsibility analysis

For each responsibility, the analysis asks: does it require a central
authority, given what AetherMesh provides?

### 4.1 M1 — Memory Lifecycle Integrity

**Question.** Does preserving lifecycle integrity require a central
authority?

**Analysis.** Lifecycle integrity is the state of a knowledge unit across
S1–S7. AetherMesh distributes the unit; it does not track the unit's state
across stages. To preserve integrity, each node must know the unit's current
stage. This can be done **locally**, with the stage recorded as metadata
alongside the unit and replicated by Mesh.

There is **no** stage that requires a global view. Acquisition is local (each
node admits units). Qualification is local (each node assesses trust).
Consolidation may require agreement, but Mesh provides convergence.
Persistence is local (each node stores). Retrieval is local (each node
answers). Revision is local (each node records the revision). Expiration is
local (each node expires the unit).

**Verdict.** No central authority required. M1 is **decentralizable** under
AetherMesh.

**Caveat.** The caveat is **consistency**: if two nodes disagree on the
stage of a unit, Mesh converges, but the convergence may not preserve
semantic integrity. This is a coherence question, not a centralization
question. It is carried into M-F2's state-layer discussion.

### 4.2 M2 — Scope-Bounded Retrieval

**Question.** Does enforcing scope require a central authority?

**Analysis.** Scope is the set of parties authorized to retrieve a unit.
The authorization may be expressed as a **capability** (a token held by the
requester) or as a **policy** (a rule evaluated by each node). In either
case, the node answering the retrieval can enforce scope **locally**, without
a central authority, if the authorization is part of the unit's metadata or
the requester's credentials.

There is **no** requirement for a central authority if:

- the authorization is a capability (verifiable locally, cryptographically);
- the authorization is a policy (evaluable locally against the requester's
  identity).

**Verdict.** No central authority required. M2 is **decentralizable**.

**Caveat.** This depends on AetherGovern (threat T5) and AetherIdentity
(candidate). If authorization is issued by a central authority, M2 is not
decentralizable. The analysis assumes the authorization is local. This
assumption is a **reservation** on M-F3, not a demonstration.

### 4.3 M3 — Temporal Validity

**Question.** Does enforcing temporal validity require a central authority?

**Analysis.** Temporal validity is the property that a unit is valid **now**.
"Now" is the difficulty: if each node has its own clock, the nodes may
disagree on whether a unit is valid.

There are two cases:

- **If validity is relative to a local clock** — each node decides whether
  the unit is valid at its own time. No central authority required. But
  nodes may disagree.
- **If validity is relative to a global clock** — a single source of "now"
  is required. This is a **central authority**.

**Verdict.** M3 **may require** a central clock if validity is defined
globally. This is the **strongest candidate for a central authority** among
the five responsibilities.

**Caveat.** The clock can be decentralized (logical clocks, vector clocks,
or a distributed timestamp such as a hash chain). Whether a decentralized
clock is sufficient is an **open question**. If it is, M3 is decentralizable.
If not, M3 requires a central authority and **M-F3 is falsified**.

This is a **genuine open question**, not a rhetorical one.

### 4.4 M4 — Provenance Tracking

**Question.** Does preserving provenance require a central authority?

**Analysis.** Provenance is the chain of sources and derivations for a unit.
The chain can be recorded as a **hash-linked list** alongside the unit, and
replicated by Mesh. Any node can verify the chain locally.

There is **no** requirement for a central authority: the chain is
self-verifying (each link is a hash of the previous). This is the same
mechanism AetherGit uses for version history.

**Verdict.** No central authority required. M4 is **decentralizable**.

**Caveat.** The chain depends on AetherAudit for the **recording** of the
source. If Audit requires a central recorder, M4 inherits that dependency.
The analysis assumes Audit can be decentralized (each node records its own
provenance and replicates). This is a **reservation**.

### 4.5 M5 — Forgetting Semantics

**Question.** Does distinguishing deletion from forgetting require a central
authority?

**Analysis.** Deletion is the removal of data; forgetting is the
invalidation of knowledge. Invalidation can be recorded as a **tombstone**
(a marker that the unit is no longer valid, while its provenance is
preserved) and replicated by Mesh. Each node can honor the tombstone locally.

There is **no** requirement for a central authority if the tombstone is part
of the unit's metadata.

**Verdict.** No central authority required. M5 is **decentralizable**.

**Caveat.** If forgetting requires **global consistency** (every node must
forget at the same moment), a central clock is required. This is the same
caveat as M3. The analysis assumes forgetting is eventual, not simultaneous.
This is a **reservation**.

---

## 5. Summary

| Responsibility | Central authority required? | Verdict |
|:-:|:-:|---|
| **M1** Lifecycle Integrity | No | Decentralizable |
| **M2** Scope-Bounded Retrieval | No (if authorization is local) | Decentralizable, with reservation |
| **M3** Temporal Validity | **May require a global clock** | **Open** |
| **M4** Provenance Tracking | No (self-verifying chain) | Decentralizable |
| **M5** Forgetting Semantics | No (if eventual, not simultaneous) | Decentralizable, with reservation |

**One responsibility (M3) is open.** The other four are decentralizable, with
reservations on M2, M4, and M5.

---

## 6. Preliminary M-F3 status

| Question | Answer |
|---|---|
| Does any responsibility **demonstrably** require a central authority? | **No.** None has been shown to require one. |
| Does any responsibility **plausibly** require a central authority? | **Yes — M3 (temporal validity).** The global-clock question is genuine. |
| Is M-F3 **falsified**? | **No.** No responsibility has been shown to require a central authority. |
| Is M-F3 **accepted**? | **No.** M3 is open, and three reservations (M2, M4, M5) are unresolved. |
| **Current M-F3 status** | **Partial — M3 open; three reservations.** |

M-F3 is **not falsified** and **not accepted**. It remains **untested in
full**.

---

## 7. What this analysis does establish

1. **Four of five responsibilities are decentralizable** without a central
   authority, under stated assumptions.
2. **M3 (temporal validity) is the open case.** If a decentralized clock is
   insufficient, M3 requires a central authority and M-F3 is falsified.
3. **The three reservations** (M2, M4, M5) are **conditional on Policy,
   Audit, and Govern** — the same structural dependency (T3) that affects
   M-F1 and M-F2.
4. **The decentralized clock question** is the **decisive question** for
   M-F3. It is carried into Phase 2.

---

## 8. What this analysis does not establish

- It does not show that AetherMemory is decentralized. It shows that four
  responsibilities **can** be decentralized, under assumptions.
- It does not resolve the clock question. The question is genuine and is
  carried forward.
- It does not resolve the reservations on M2, M4, M5.
- It does not resolve the structural dependency (T3).
- It does not substitute for the independent review (Phase 2).

---

## 9. The decisive question

M-F3 is decided by one question:

> **Can temporal validity (M3) be enforced with a decentralized clock, or
> does it require a global clock?**

- **If a decentralized clock is sufficient** (logical clocks, vector clocks,
  or distributed timestamps), M3 is decentralizable and M-F3 is **not
  falsified**.
- **If a decentralized clock is insufficient**, M3 requires a central
  authority and M-F3 is **falsified**.

This is not a rhetorical question. The answer depends on:

- the granularity of "now" required (milliseconds, seconds, hours);
- the tolerance for disagreement between nodes;
- the cost of a distributed timestamp.

None of these is settled here. The question is carried into Phase 2.

---

## 10. Consequences for the decision

M-F3 adds a **fourth decisive question** to the Phase 2 review (alongside the
three from M-F1, M-F2, and the structural dependency T3):

1. M-F1: Is the lifecycle covered by Git + Mesh? (partially answered: no)
2. M-F2: Is the remainder real or a composition effect? (partially
   answered: remainder is the state layer)
3. M-F3: Does temporal validity require a global clock? (**open**)
4. T3: Do Policy and Audit resolve the open cells? (**open**)

The Phase 4 decision requires all four to be addressed.

---

## 11. Next step

Phase 2 — Hypothesis Review. The independent reviewer is asked to assess the
four decisive questions. Until then, M-F3 remains **partial — M3 open; three
reservations**, and the overall decision remains **(E) Undetermined
(interim)**.

---

**AetherMemory v1.0.0 — M-F3 Decentralization Analysis**
© 2026 Samir Baladi — Ronin Institute / Rite of Renaissance
DOI: [10.6084/m9.figshare.35069155](https://doi.org/10.6084/m9.figshare.35069155)

*Partial execution. M-F3 not falsified, not accepted. M3 (temporal validity)
is the decisive open question.*
