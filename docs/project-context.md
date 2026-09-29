# Project Context

This document rebuilds the project's context from the evidence in the repository. Every statement is labeled:

- **Confirmed**: backed directly by a file or by the git history.
- **Inferred**: a reasonable deduction from the available files.
- **Unknown**: the repository does not provide enough information to decide.

## Classification

**Project origin: Personal Project, concept / inception stage.**

| Evidence | Status |
| --- | --- |
| Hosted under the author's personal GitHub account (`OBaruch`); every commit is authored by Baruch Lopez. | Confirmed |
| No reference to a university, course, assignment, instructor, grading or due date anywhere in the repository. | Confirmed |
| The README presents it as an "open-source platform" that invites "contributors worldwide". | Confirmed |
| Released under the Apache License 2.0. | Confirmed |
| The project was started independently, outside an academic setting. | Inferred |
| The specific motivation (for example, a personal need or a portfolio exercise). | Unknown |

## Timeline

| Date | Commit | Event |
| --- | --- | --- |
| 2025-03-12 18:46 (UTC-6) | `0341aa0` | *Initial commit*: GitHub-generated `README.md`, Apache 2.0 `LICENSE` and the Python `.gitignore` template. |
| 2025-03-12 18:47 (UTC-6) | `336d626` | *Update README.md*: the README grows into a project description (overview, key features, an unfinished *Getting Started* section). |

Both commits were made about one minute apart. **Confirmed:** no later work was committed before this reorganization.

## What the project set out to do

**Confirmed (from the original README):**

- **Problem:** Credit card benefits (perks, rewards, discounts, promotions) are spread across many sources and are often out of date, so cardholders miss value they are entitled to.
- **Goal:** One unified dashboard that aggregates and updates benefits from the major networks (American Express, Visa and Mastercard are named as examples) and from local banks and neobanks worldwide.
- **User flow:** A user registers their credit cards and immediately sees every associated perk in one interface.
- **Design principle:** A modular architecture of plug-and-play connectors, so contributors can add data extraction for new institutions and regions.
- **Stated features:** real-time data integration, modular architecture, a user-friendly dashboard, global collaboration, scalability and flexibility.

## Technologies

| Item | Status | Notes |
| --- | --- | --- |
| Python | **Inferred** | The only evidence is the `.gitignore`, which is the standard GitHub Python template chosen when the repository was created. No Python code exists. |
| Web dashboard | **Confirmed as intent** | The README mentions an "intuitive web interface". No frontend technology is named. |
| APIs / connectors | **Confirmed as intent** | The README mentions "connectors and APIs for data extraction". No specific APIs, data providers or protocols are named. |
| Databases, frameworks, hosting | **Unknown** | Not mentioned anywhere. |

## Implementation status

**Confirmed:** The repository contains no source code, data, configuration, tests, notebooks, images or diagrams. The whole project consists of:

| File | Type | Role |
| --- | --- | --- |
| `README.md` | Documentation | Project vision (now preserved in [`original/README.original.md`](original/README.original.md)). |
| `LICENSE` | Legal | Apache License 2.0, unmodified template text. The appendix placeholder `Copyright [yyyy] [name of copyright owner]` is standard boilerplate, not something the author left unfinished. |
| `.gitignore` | Configuration | GitHub's Python template (174 lines). |

This is why the reorganized repository has no `src/`, `data/` or `assets/` folders, and no `architecture.md` or `code-overview.md`. They would describe things that don't exist.

## Inconsistencies found

1. **Present-tense claims vs. no implementation.** The README describes features as if they exist ("Connect to multiple data sources…", "Intuitive web interface…"). The repository shows these were goals, not delivered functionality.
2. **Unfinished Getting Started section.** The original README ends at `1. **Clone the Repository:**` with no instructions after it. No setup or run commands can be recovered.
3. **"Real-time" vs. "near real-time".** The introduction says "real-time benefits data", while the features list says "near real-time". The intended freshness guarantee is **Unknown**.

## Scope that cannot be determined

The original repository does not provide enough information to determine:

- target users, regions or languages at launch;
- which issuers, banks or data sources would be integrated first;
- how benefit data would be obtained (official APIs, partner feeds, scraping, manual curation);
- how card registration would work, or what card data would be stored;
- hosting, authentication, persistence or business model.

Forward-looking answers to these questions are gathered as **open questions** in the [specification](sdlc/spec.md), not presented as facts.
