# Contributor and Agent Guidelines

These rules apply to anyone who changes this repository, whether a person or an automated coding assistant.

## Repository status

This repository is a preserved concept-stage project. It holds no source code, only the original project vision plus documentation added later. See [docs/project-context.md](docs/project-context.md).

## Rules

1. **Preserve the originals.** Never edit files in [`docs/original/`](docs/original/), `LICENSE` or `.gitignore`. They are historical artifacts.
2. **Don't invent facts.** Label claims about the original project as *Confirmed*, *Inferred* or *Unknown*. Never present an inference or proposal as something the original project did.
3. **Follow the chain.** Changes follow [intent](docs/sdlc/intent.md) → [spec](docs/sdlc/spec.md) → [plan](docs/sdlc/plan.md). Update the upstream document before writing code that depends on it, and reference requirement IDs (`FR-*`, `NFR-*`) in commits and pull requests.
4. **Resolve open questions first.** Don't implement anything that depends on an open question (`Q*`) or pending decision (`D*`) until it is answered and recorded.
5. **Keep changes small and reviewable.** Humans review every change before merge.
6. **No unneeded infrastructure.** Don't add build tools, CI/CD, containers or deployment configuration until there is code that needs them.
7. **Never commit secrets or real card data.**
