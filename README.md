# Global Card Perks

> **Status: concept stage.** This repository records the vision for an open-source platform. No implementation was built.

## Project Overview

Global Card Perks was planned as an open-source platform that gathers credit card benefits (perks, rewards, discounts and promotions) from issuers worldwide into one dashboard. Examples of issuers are networks like American Express, Visa and Mastercard, plus local banks and neobanks. A cardholder would register their cards once and see every associated benefit in one place.

## Project Context

**Personal Project, concept / inception stage** (started March 12, 2025).

- **Confirmed:** Created under the author's personal GitHub account, released under the Apache License 2.0, and described as an open-source project open to contributors worldwide. Nothing ties it to a course or institution.
- **Confirmed:** The repository has a project description, a license and a `.gitignore`. It has **no source code**, and the original *Getting Started* section was never finished.
- **Unknown:** The personal motivation behind the project, and why development didn't go further.

Full evidence and timeline: [docs/project-context.md](docs/project-context.md).

## Problem Statement

Card benefits are scattered across many sources and are often out of date, so cardholders miss value they are entitled to. *(Original README.)*

## Objective

Give users one interface where they register their cards and instantly see all associated benefits. The data would come from a modular set of connectors that contributors can extend to new institutions and regions. *(Original README.)*

## Planned Features

From the original README. **None of these were implemented.**

- **Real-time data integration:** connect to multiple data sources and update benefits in near real time.
- **Modular architecture:** plug-and-play connectors for different issuers and banks.
- **User-friendly dashboard:** a web interface to register cards and explore benefits.
- **Global collaboration:** extendable to new regions and institutions.
- **Scalable and flexible:** grows as new benefits or data sources appear.

## Repository Structure

```text
.
├── README.md                  # This file (rewritten during reorganization)
├── AGENTS.md                  # Rules for contributors and coding assistants
├── LICENSE                    # Apache License 2.0 (original)
├── .gitignore                 # Python template (original)
└── docs/
    ├── README.md              # Documentation index
    ├── project-context.md     # Origin, evidence, status (Confirmed / Inferred / Unknown)
    ├── sdlc/
    │   ├── intent.md          # Why: problem, outcome, principles
    │   ├── spec.md            # What: requirements, domain model, open questions
    │   └── plan.md            # How: proposed decisions, architecture, phases
    └── original/
        ├── README.md          # About the original materials
        └── README.original.md # Original README, unmodified
```

There are no `src/`, `data/` or `assets/` folders because the original repository contained no code, data or images.

## Original Implementation

This repository preserves the original state of the project. No source code was ever written, so none exists to preserve. The original files (`LICENSE`, `.gitignore` and the original README, now in [`docs/original/README.original.md`](docs/original/README.original.md)) are kept unmodified. Everything else was added later to explain the project.

## Technologies

| Technology | Status |
| --- | --- |
| Python | **Inferred** only from the `.gitignore` template chosen at creation. No Python code exists. |
| Web dashboard, APIs / connectors | **Planned** in the README. No frameworks or providers were named. |
| Databases, hosting, other tooling | **Unknown** |

## How It Works

Only the intended design is known (from the original README):

1. A user registers the credit cards they hold.
2. Connectors, one per issuer or data source, gather benefit data and keep it current.
3. The dashboard shows every benefit for the user's registered cards in one view.

A conceptual architecture and proposed delivery phases are in [docs/sdlc/plan.md](docs/sdlc/plan.md). They are proposals, not a description of existing software.

## Running the Project

There is nothing to run. The original README began a *Getting Started* section (`1. Clone the Repository:`) but it contains no further instructions, and the repository has no executable code.

## Documentation

- [Documentation index](docs/README.md)
- [Project context](docs/project-context.md)
- [Intent](docs/sdlc/intent.md) → [Specification](docs/sdlc/spec.md) → [Plan](docs/sdlc/plan.md)
- [Original materials](docs/original/)
- [Contributor and agent guidelines](AGENTS.md)

## License

Apache License 2.0. See [LICENSE](LICENSE).

## Historical Note

This repository was later reorganized and documented to make it easier to read and to keep the historical context of the original project. The original files remain unchanged. The intent, specification and plan documents were reconstructed from the original project description, and they clearly separate what the original stated from what was inferred or proposed afterwards.
