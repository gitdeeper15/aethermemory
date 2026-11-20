# AetherMemory — Complete Inventory

**Version:** 1.0.0 (Architectural Investigation · Phase 0)
**Release Date:** 2026-11-19
**Author:** Samir Baladi
**Email:** gitdeeper@gmail.com
**ORCID:** [0009-0003-8903-0029](https://orcid.org/0009-0003-8903-0029)
**License:** CC-BY-4.0 (docs, manuscript, figures) · MIT (code, future — none in this release)
**Status:** Architectural Investigation · Candidate (Phase 0: in progress)
**Record ID:** AETHERMEMORY-01
**DOI (Zenodo):** 10.6084/m9.figshare.35069155
**Website:** [aethermemory.netlify.app](https://aethermemory.netlify.app)

---

## Research Status

| Item | Status |
|---|---|
| Document type | Research article (architectural hypothesis, Phase 0) |
| Paper (v1.0.0) | ✅ Published (Zenodo) |
| Implementation | ❌ Not built (not permitted at Phase 0) |
| Tests | ❌ None |
| Experiments | ❌ None executed (Section 9 of the paper is a proposal) |
| PyPI package | ❌ Not published |
| Real-world deployment | None; no deployed system has been benchmarked |
| Propositions P1–P2 | Stated with proof sketches; not machine-checked |
| Failure conditions | M-F1, M-F2, M-F3, M-F4 — **all untested** |
| Internal review | ✅ Complete |
| Independent review | ✅ Complete (Jonathan Rabe, 2026-11-19) |
| Review status | Not peer reviewed |
| Decision | **(E) Undetermined (interim)** |
| Structural dependency | AetherPolicy (Phase 4 paused), AetherAudit (Phase 4 paused) |

---

## Repository Links

| Platform | URL | Role | Status |
|----------|-----|------|--------|
| GitHub | https://github.com/gitdeeper15/aethermemory | Primary | ✅ Active |
| GitLab | https://gitlab.com/gitdeeper15/aethermemory | Mirror | ✅ Active |
| Codeberg | https://codeberg.org/gitdeeper15/aethermemory | Mirror | ✅ Active |
| Bitbucket | https://bitbucket.org/gitdeeper15/aethermemory | Mirror | ✅ Active |
| Website | https://aethermemory.netlify.app | Live documentation | ✅ Active |
| Zenodo | https://doi.org/10.6084/m9.figshare.35069155 | Citable DOI | ✅ Published |
| ORCID | https://orcid.org/0009-0003-8903-0029 | Identity | ✅ Active |

---

## Root Files

| File | Purpose | Status |
|------|---------|:-:|
| `.gitignore` | Git ignore rules | ✅ |
| `AUTHORS.md` | Contributors | ✅ |
| `CHANGELOG.md` | Version history | ✅ |
| `CITATION.cff` | Citation metadata | ✅ |
| `CONTRIBUTING.md` | Contribution guidelines | ✅ |
| `INVENTORY.md` | This file | ✅ |
| `LICENSE` | CC-BY-4.0 (docs) + MIT (code, future) | ✅ |
| `PROJECT_SUMMARY.txt` | One-page summary | ✅ |
| `README.md` | Main documentation | ✅ |
| `ARCHITECTURAL_HYPOTHESIS.md` | The hypothesis under investigation | ✅ |
| `ROADMAP.md` | Phase status (0 → 6) | ✅ |
| `VERSION` | `1.0.0` | ✅ |
| `manifest.json` | Project manifest | ✅ |
| `scientific_state.json` | Scientific state record | ✅ |
| `netlify.toml` | Netlify configuration | ✅ |

---

## Directories

| Directory | Contents | Status |
|-----------|----------|:-:|
| `docs/figures/` | 9 figures (Fig1–Fig9) | ✅ Complete |
| `research/` | `RESPONSIBILITY_BOUNDARIES.md` | ✅ Placeholder (Phase 1 not started) |
| `FALSIFICATION/` | `FALSIFICATION_PLAN.md`, `M-F1_COVERAGE_ANALYSIS.md`, `M-F2_COMPOSITION_ANALYSIS.md`, `M-F3_DECENTRALIZATION_ANALYSIS.md`, `M-F4_STATUS.md` | ✅ Plan complete; M-F1, M-F2, M-F3 partially executed; M-F4 declared not executable |
| `DECISIONS/` | `INDEPENDENCE_DECISION.md` | ✅ Placeholder (Phase 4 not started) |
| `REVIEW/` | `INTERNAL_REVIEW.md`, `INDEPENDENT_REVIEW.md`, `INDEPENDENT_REVIEW_PROTOCOL.md`, `README.md` | ✅ Placeholder (Phase 2 not started) |
| `REFERENCES/` | 30 references from the paper | ⏳ To be populated |
| `REPORTS/architectural_investigation/` | `investigation_report.md` | ✅ Placeholder (Phase 0 in progress) |
| `paper/` | `AetherMemory_Research_Paper_v0.1.0.pdf` | ✅ Published |
| `PUBLICATION/Netlify/public/` | Website (HTML pages) | ⏳ Pending |

No `src/`, no `tests/`, no `experiments/` — and none is planned unless Phase 4 becomes positive.

---

## PUBLICATION/

| File | Purpose | Status |
|------|---------|:-:|
| `PUBLICATION/Netlify/public/index.html` | Website landing page | ✅ |
| `PUBLICATION/Netlify/public/dashboard.html` | Project dashboard | ✅ |
| `PUBLICATION/Netlify/public/documentation.html` | Documentation page | ✅ |
| `PUBLICATION/Netlify/public/reports.html` | Reports page | ✅ |
| `PUBLICATION/Netlify/public/project.json` | Machine-readable project metadata | ✅ |
| `PUBLICATION/Netlify/public/robots.txt` | Search engine directives | ✅ |
| `PUBLICATION/Netlify/public/sitemap.xml` | Sitemap | ✅ |
| `PUBLICATION/Netlify/public/_headers` | HTTP headers config | ✅ |

---

## REFERENCES/

| File | Purpose | Status |
|------|---------|:-:|
| `REFERENCES/README.md` | Reference list placeholder (30 refs in paper) | ⏳ To be populated |

---

## Formal Artifacts

| Category | Count |
|---|---|
| Lifecycle stages (S1–S7) | 7 |
| Failure conditions (M-F1 to M-F4) | 4 |
| Propositions (P1–P2, proof sketches) | 2 |
| Candidate responsibilities (M1–M5) | 5 |
| Boundaries (Git, Mesh, Policy, Audit, Govern, Proof, Runtime, Orchestrate, Identity, Human) | 10 |
| Open questions (Q1–Q10) | 10 |
| Figures | 9 |
| References | 30 (in the paper) |
| Related Aether projects | 12 (including AetherMemory) |
| Phases | 7 (0–6) |
| Tests run | 0 |
| Experiments executed | 0 |

---

## Failure Conditions (M-F1 to M-F4)

| ID | Claim under test | Status |
|:-:|---|:-:|
| M-F1 | Non-redundancy | 🟡 **Partial** (Git + Mesh); Policy/Audit open |
| M-F2 | Distinction from Git + Mesh + Policy + Audit | 🟡 **Partial**; remainder = state layer |
| M-F3 | Decentralizability | 🟡 **Partial**; M3 (temporal validity) open |
| M-F4 | Observable benefit | ⚫ **Not executable at Phase 0** |

> "Untested" is the default state at Phase 0. The decision rule requires **all four** to be tested with none falsified, with M-F4 supported by measured results.

---

## Phase Status

| Phase | Description | Status |
|---|---|---|
| 0 | Architectural Hypothesis | 🟡 In progress |
| 1 | Responsibility Mapping | ⏳ Not started |
| 2 | Hypothesis Review (Independent) | ⏳ Not started |
| 3 | Falsification Design | ⏳ Not started |
| 4 | Independence Decision | ⏳ Not started |
| 5 | Architectural Specification | ❌ Not permitted |
| 6 | Reference Implementation | ❌ Not permitted |

---

## Companion Works

AetherMemory is the **twelfth project (candidate)** of the Aether family. It does **not** replace AetherGit, AetherMesh, AetherPolicy, or AetherAudit.

| # | System | Dimension | Status | DOI |
|:-:|---|---|---|---|
| 1 | AetherGit | Storage / Foundation | Foundational | [10.5281/zenodo.23976986](https://doi.org/10.5281/zenodo.23976986) |
| 2 | AetherFlow | Integration | Foundational | [10.5281/zenodo.23979129](https://doi.org/10.5281/zenodo.23979129) |
| 3 | AetherProof | Verification | Foundational | [10.5281/zenodo.24013124](https://doi.org/10.5281/zenodo.24013124) |
| 4 | AetherMesh | Decentralization | Foundational | [10.5281/zenodo.24038038](https://doi.org/10.5281/zenodo.24038038) |
| 5 | AetherGovern | Governance | Foundational | [10.5281/zenodo.24054524](https://doi.org/10.5281/zenodo.24054524) |
| 6 | AetherRuntime | Runtime Assurance | Foundational | [10.5281/zenodo.24078477](https://doi.org/10.5281/zenodo.24078477) |
| 7 | AetherOrchestrate | Orchestration | Foundational | [10.5281/zenodo.24095399](https://doi.org/10.5281/zenodo.24095399) |
| 8 | AetherIdentity | Identity | Candidate | [10.5281/zenodo.24102739](https://doi.org/10.5281/zenodo.24102739) |
| 9 | AetherPolicy | Policy Lifecycle | Candidate (Phase 4: paused) | [10.5281/zenodo.24160047](https://doi.org/10.5281/zenodo.24160047) |
| 10 | AetherAudit | Audit / Evidence | Candidate (Phase 4: paused) | [10.5281/zenodo.24274628](https://doi.org/10.5281/zenodo.24274628) |
| 11 | AetherHuman | Human Participation | Candidate (Phase 4: paused) | [10.5281/zenodo.24315874](https://doi.org/10.5281/zenodo.24315874) |
| 12 | **AetherMemory** | **Memory Lifecycle** | **Candidate (this repository; Phase 0)** | **[10.6084/m9.figshare.35069155](https://doi.org/10.6084/m9.figshare.35069155)** |

---

## What This Repository Does Not Claim

- That AetherMemory is an independent architectural dimension.
- That the seven lifecycle stages are complete, independent, or necessary.
- That the boundaries with AetherGit, AetherMesh, AetherGovern, AetherPolicy, AetherAudit, and the other dimensions are sufficient.
- That the gap is genuine.
- That implementation should begin.
- Any observed benefit (M-F4 is untested).
- Any causal effect.

---

## Citation

### Paper (v1.0.0)

```bibtex
@misc{baladi2026aethermemory,
  author    = {Baladi, Samir},
  title     = {AetherMemory: Memory Lifecycle Integrity in Autonomous Multi-Agent Systems},
  year      = {2026},
  version   = {1.0.0},
  publisher = {Zenodo},
  doi       = {10.6084/m9.figshare.35069155},
  url       = {https://doi.org/10.6084/m9.figshare.35069155},
  note      = {Architectural investigation; Phase 0: (E) Undetermined (interim)}
}
```

---

Contact

· Email: gitdeeper@gmail.com
· ORCID: 0009-0003-8903-0029
· Website: aethermemory.netlify.app
· GitHub: gitdeeper15/aethermemory

---

Last Updated: 2026-11-19
Current Version: 1.0.0
Decision: (E) Undetermined (interim)
