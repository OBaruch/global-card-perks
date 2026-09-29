# Intent: Global Card Perks

> **Status:** Reconstructed from the original repository (commit `336d626`, 2025-03-12).
> **Implementation status:** Not started. The repository has no source code.
> **Source of truth:** [`docs/original/README.original.md`](../original/README.original.md)

This document records *why* the project exists and *what outcome* it aims for, independent of any implementation. It is the top of the chain **intent → [spec](spec.md) → [plan](plan.md)**. Anything downstream should trace back to a statement here.

## 1. Problem

> "Many users miss out on valuable card benefits because the information is scattered across different sources and often outdated."
> (original README)

Cardholders hold cards from different networks (American Express, Visa, Mastercard) and from different local banks and neobanks. Each publishes its perks, rewards, discounts and promotions in its own place, format and update cycle. Cardholders can't easily answer:

- *Which benefits do my cards give me right now?*
- *Is what I read still valid?*

## 2. Desired outcome

A cardholder registers the cards they own **once** and sees **all current benefits** for those cards in **one place**, kept up to date automatically.

## 3. Target users

| User | Need | Status |
| --- | --- | --- |
| Cardholder | See every benefit of their own cards in one place. | Confirmed (README) |
| Contributor / developer | Add connectors for new issuers, banks or regions. | Confirmed (README) |
| Issuers, banks, merchants as users | Not mentioned. | Unknown / out of scope |

## 4. Guiding principles

These principles come from the original README and constrain every later decision:

1. **Centralization:** one unified view, not one app per issuer.
2. **Freshness:** benefits are updated in real time or near real time (see open question Q1 in the spec).
3. **Modularity:** data sources plug in as independent connectors.
4. **Global reach:** support for any network, bank or region, not one country.
5. **Open collaboration:** open source (Apache 2.0), extended by contributors worldwide.
6. **Scalability:** new benefits and data sources can be added without redesign.

## 5. Success signals

The original repository defines no metrics. These signals are **inferred** from the stated goal and are meant to be confirmed or replaced:

- A user can see the benefits of every card they registered without visiting any issuer site.
- Displayed benefits match the issuers' published terms, with a visible "last updated" timestamp.
- A contributor can add a new data source by writing one connector, without changing the core.

## 6. Non-goals

The README doesn't name any. These are **inferred** from what the README leaves out, and noted so scope doesn't creep silently:

- Making payments, moving money or acting as a card issuer.
- Card applications, credit scoring or card recommendation.
- Replacing the issuers' official terms. The platform points to them; it isn't the legal source.

## 7. Constraints and risks known at intent level

| Topic | Note | Status |
| --- | --- | --- |
| License | Apache License 2.0. | Confirmed |
| Card data sensitivity | "Registering credit cards" involves financial data. How much card data is needed is not defined. | Unknown: see spec Q3 |
| Data access | How benefit data is legally and technically obtained is not defined. | Unknown: see spec Q2 |

## 8. Traceability

| Intent element | Where it goes next |
| --- | --- |
| Problem and outcome | [spec.md §2 Scope](spec.md#2-scope) |
| Principles 1–6 | [spec.md §4 Functional requirements](spec.md#4-functional-requirements) and [§5 Non-functional requirements](spec.md#5-non-functional-requirements) |
| Unknowns | [spec.md §8 Open questions](spec.md#8-open-questions) |
