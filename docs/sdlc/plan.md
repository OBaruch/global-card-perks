# Plan: Global Card Perks

> **Status:** Proposed. Nothing in this plan has been implemented.
> **Upstream:** [intent.md](intent.md) → [spec.md](spec.md)

This plan describes *how* the [spec](spec.md) could be delivered. The original repository contains no implementation and no technical decisions beyond a Python `.gitignore` template. Every technical choice below is therefore a **proposal** to be confirmed. None of it records what was built.

## 1. Current state (baseline)

| Area | State | Evidence |
| --- | --- | --- |
| Product vision | Defined | [original README](../original/README.original.md) |
| Requirements | Reconstructed as a draft | [spec.md](spec.md) |
| Source code | None | Repository contents at commit `336d626` |
| Stack | Undecided. Python hinted at. | `.gitignore` (GitHub Python template) |
| License | Apache 2.0 | `LICENSE` |
| Documentation | Reorganized; this plan | `docs/` |

## 2. Guiding approach

Work moves through gated steps in which each artifact has to be approved before the next one is written:

1. **Intent** is agreed ([intent.md](intent.md)).
2. **Spec** open questions Q1–Q7 are resolved and the spec moves from *Draft* to *Approved*.
3. **Plan** decisions (§3) are recorded as short decision records in `docs/decisions/`, a folder to create when the first decision is made.
4. **Tasks** are cut from the phases below as small, independently reviewable changes. Each one references the requirement IDs it satisfies (for example `FR-6`).
5. **Verification:** every change is reviewed by a human before merge, whoever or whatever wrote it. Acceptance criteria in the spec are the definition of done.

## 3. Decisions to make

| ID | Decision | Options (not exhaustive) | Blocks | Linked question |
| --- | --- | --- | --- | --- |
| D1 | Backend language and framework | Python (hinted at by `.gitignore`), other | Phase 1 | Q7 |
| D2 | How benefit data is acquired | Official APIs, partner feeds, curated datasets, public pages (subject to terms) | Phase 2 | Q2 |
| D3 | Card registration model | Catalog selection of card products (no card numbers), or account linking | Phase 1 | Q3 |
| D4 | User identity | Anonymous or local, or authenticated accounts | Phase 3 | Q4 |
| D5 | Refresh strategy | Scheduled polling, event/webhook-driven, hybrid | Phase 2 | Q1 |
| D6 | Initial issuer and region coverage | To be chosen | Phase 2 | Q5 |

## 4. Proposed architecture (conceptual)

Derived from the README's "modular architecture" and "plug-and-play connectors". Component boundaries are proposals.

```text
            ┌──────────────────────────┐
            │      Web dashboard       │  FR-1, FR-2, FR-3
            └────────────┬─────────────┘
                         │
            ┌────────────▼─────────────┐
            │        Core service      │  catalog, registered cards, benefit queries
            └────────────┬─────────────┘
                         │ normalized benefits
            ┌────────────▼─────────────┐
            │     Connector registry    │  FR-6, FR-7, NFR-2
            └──┬──────────┬──────────┬─┘
               │          │          │
          Connector A  Connector B  Connector N   (one per issuer or source)
```

Key contract (proposed, NFR-2): each connector declares the issuer it covers, lists card products, returns benefits in a common schema, and reports a last-updated timestamp (FR-8).

## 5. Phases

| Phase | Goal | Main outputs | Requirements |
| --- | --- | --- | --- |
| **0. Foundations** | Resolve open questions and record decisions D1–D6. | Approved spec, decision records, first README *Getting Started* that works | — |
| **1. Domain and catalog** | Model issuers, card products and benefits; let users select cards (no payment data). | Data model, card catalog, registration flow | FR-1, FR-9, NFR-5, NFR-6 |
| **2. Connector framework** | Define the connector contract and ship a first reference connector. | Connector interface and docs, one or two connectors, refresh job | FR-4, FR-5, FR-6, FR-8, NFR-1, NFR-2 |
| **3. Dashboard** | Show a user's benefits in one view. | Web dashboard | FR-2, FR-3, NFR-4 |
| **4. Community extension** | Make it easy for outside contributors to add connectors and regions. | Contributor guide, connector template | FR-7, NFR-3, NFR-7 |

## 6. Risks

| Risk | Impact | Mitigation (proposed) |
| --- | --- | --- |
| Issuers offer no public benefit data | Core value can't be delivered | Settle D2 first; start with sources whose terms allow reuse |
| Handling card numbers brings compliance scope | Security and legal burden | Catalog-based registration only (NFR-6) |
| Stale or incorrect benefits | Loss of user trust (the original problem) | Source and timestamp on every benefit (FR-8); staleness alerts |
| Connectors break when sources change | Data gaps | Per-connector health checks; isolate failures |

## 7. Out of this plan

The plan adds no infrastructure (containers, CI/CD, cloud deployment) until the decisions above are made and code exists to need it.
