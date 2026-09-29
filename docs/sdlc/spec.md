# Specification: Global Card Perks

> **Status:** Draft, reconstructed from the original repository. Not implemented.
> **Upstream:** [intent.md](intent.md) · **Downstream:** [plan.md](plan.md)
> **Source of truth:** [`docs/original/README.original.md`](../original/README.original.md)

This spec describes *what* the system must do, not *how*. Each requirement carries an origin tag:

- **[README]**: stated directly in the original README (confirmed intent).
- **[Derived]**: follows logically from a README statement (inferred).
- **[Proposed]**: a new suggestion to make the spec workable. It was not part of the original project and must be confirmed before implementation.

## 1. Summary

Global Card Perks is an open-source platform that gathers credit card benefit data from many issuers into one dashboard. A cardholder registers their cards and sees every associated perk, reward, discount and promotion, kept up to date by pluggable data connectors.

## 2. Scope

### In scope

- Registering the cards a user holds. **[README]**
- Aggregating benefits from global networks and from local banks and neobanks. **[README]**
- Showing those benefits in a web dashboard. **[README]**
- A connector model that lets contributors add new data sources. **[README]**

### Out of scope

- Payments, transactions or money movement. **[Derived]**, see [intent §6](intent.md#6-non-goals)
- Card applications, approval or recommendation engines. **[Derived]**

## 3. Domain glossary

| Term | Meaning | Origin |
| --- | --- | --- |
| **Issuer** | A network or institution whose cards carry benefits (for example American Express, Visa, Mastercard, local banks, neobanks). | [README] |
| **Card product** | A specific card offering from an issuer (for example a particular rewards card). The unit that benefits attach to. | [Derived] |
| **Benefit** | A perk, reward, discount or promotion linked to a card product. | [README] |
| **Connector** | A plug-in module that pulls benefit data from one source and turns it into the platform's format. | [README] |
| **Registered card** | A user's statement that they hold a given card product. | [README] / [Derived] |

## 4. Functional requirements

| ID | Requirement | Origin |
| --- | --- | --- |
| FR-1 | A user can register the credit cards they hold. | [README] |
| FR-2 | After registering, the user immediately sees every benefit associated with their registered cards. | [README] "instantly view all associated perks" |
| FR-3 | Benefits are shown in one unified dashboard, grouped so users can explore them. | [README] |
| FR-4 | The system aggregates benefits from major networks and from local banks and neobanks. | [README] |
| FR-5 | The system updates benefit information from its sources in near real time. | [README] (see Q1) |
| FR-6 | Data sources are added as independent, plug-and-play connectors. | [README] |
| FR-7 | Support can be extended to new regions and institutions without changing the core system. | [README] |
| FR-8 | Each benefit shows its source and the time it was last updated. | [Proposed]: supports the "outdated information" problem |
| FR-9 | A user can remove a registered card. | [Proposed] |

### Acceptance criteria (examples)

- **FR-1 / FR-2:** Given a user with no cards, when they register card product *X*, then the dashboard lists every active benefit known for *X* without a manual refresh.
- **FR-6:** Given a new connector that follows the connector contract, when it is added, then its benefits appear in the dashboard and no core module changes.
- **FR-8** *(proposed)*: Every benefit shown has a non-empty source reference and a last-updated timestamp.

## 5. Non-functional requirements

| ID | Requirement | Origin |
| --- | --- | --- |
| NFR-1 | **Freshness:** benefit data is refreshed in real time or near real time. The exact target is still to be decided. | [README] (see Q1) |
| NFR-2 | **Extensibility:** the connector interface is stable and documented so external contributors can build against it. | [README] "modular architecture" |
| NFR-3 | **Scalability:** adding issuers, benefits or regions doesn't require redesign. | [README] "scalable and flexible" |
| NFR-4 | **Usability:** the dashboard is usable by non-technical cardholders. | [README] "user-friendly", "intuitive" |
| NFR-5 | **Global readiness:** the data model allows multiple regions, currencies and languages. | [Derived] from "worldwide" |
| NFR-6 | **Data minimization:** card registration identifies the *card product* only. Full card numbers, CVV or other payment credentials are never collected. | [Proposed]: see Q3 |
| NFR-7 | **Openness:** the source code is distributed under Apache License 2.0. | [README] / LICENSE |

## 6. Conceptual data model

**[Derived]** from the README. This is a conceptual model, not a schema.

```text
Issuer 1───* CardProduct 1───* Benefit
                  ▲
                  │ *
User 1───* RegisteredCard

Connector *───1 Issuer        (a connector provides benefits for one or more card products of an issuer)
```

## 7. External interfaces

| Interface | Description | Status |
| --- | --- | --- |
| Web dashboard | User-facing interface for registering cards and exploring benefits. | [README] |
| Connector contract | The interface each data connector implements (for example: list card products, fetch benefits, report last-updated time). | [README] concept, [Proposed] shape |
| Issuer data sources | Issuer APIs or other sources behind the connectors. | Unknown (see Q2) |

## 8. Open questions

These questions must be answered before implementation. The original repository doesn't answer them.

| ID | Question | Why it matters |
| --- | --- | --- |
| Q1 | "Real-time" (intro) or "near real-time" (features)? What refresh interval is acceptable? | Drives the connector scheduling and caching design. |
| Q2 | How is benefit data obtained: official issuer APIs, partner feeds, public web pages, manual curation? Is each method allowed by the source's terms? | Legal viability and connector design. |
| Q3 | What exactly does "register a credit card" mean? Picking a card product from a catalog, or linking a real account? | Security and compliance scope (for example, PCI DSS applies if card numbers are handled). |
| Q4 | Do users need accounts and authentication, or can the dashboard work anonymously or locally? | Identity, privacy and persistence requirements. |
| Q5 | Which issuers and regions come first? | Sets the scope of the first release. |
| Q6 | Who maintains data quality when sources conflict or go stale? | Trust in the displayed information. |
| Q7 | Which technology stack? The only hint is the Python `.gitignore` template. | Feeds [plan.md](plan.md). |

## 9. Traceability

| Intent | Requirements |
| --- | --- |
| Centralization | FR-1, FR-2, FR-3 |
| Freshness | FR-5, FR-8, NFR-1 |
| Modularity | FR-6, NFR-2 |
| Global reach | FR-4, FR-7, NFR-5 |
| Open collaboration | NFR-2, NFR-7 |
| Scalability | FR-7, NFR-3 |
