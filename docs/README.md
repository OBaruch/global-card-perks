# Documentation

| Document | Purpose |
| --- | --- |
| [project-context.md](project-context.md) | Project origin, timeline, evidence and implementation status, labeled Confirmed / Inferred / Unknown. |
| [sdlc/intent.md](sdlc/intent.md) | **Why:** the problem, desired outcome, users and guiding principles. |
| [sdlc/spec.md](sdlc/spec.md) | **What:** functional and non-functional requirements, domain model and open questions. |
| [sdlc/plan.md](sdlc/plan.md) | **How (proposed):** decisions to make, conceptual architecture and delivery phases. |
| [original/](original/) | Original, unmodified project materials. |

## How the SDLC documents relate

```text
intent.md  ──►  spec.md  ──►  plan.md  ──►  (tasks / code, not started)
   why            what           how
```

Each document links to the one above it, and requirement IDs (`FR-*`, `NFR-*`), questions (`Q*`) and decisions (`D*`) let every later change be traced back to the original intent.

All three documents are **reconstructed** from the original README. They separate what the original project stated from what was inferred or proposed during the reorganization.
