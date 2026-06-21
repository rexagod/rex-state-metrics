# Claude Code — project context

This repository uses **AGENTS.md** as the canonical description of architecture, conventions, and pitfalls.

## Before making changes

1. Read `AGENTS.md` and skim `docs/agentic-sdlc.md`.
2. Follow `REDHAT.md` for Red Hat AI policy (attribution, sensitive data, upstream).
3. Prefer small, reviewable steps; ask for constraints (API stability, dependencies, target Go version).

## Working agreements

- Propose a short plan for non-trivial work; then implement.
- After edits, run `make verify` (lint + test + generated-code check) or suggest the relevant subset.
- For commits: use conventional commit format (enforced by pre-commit hook) and add `Assisted-by:` or `Generated-by:` when appropriate.

## Team customs

- `make setup` — install all development tools and pre-commit hooks.
- `make lint` / `make lint_fix` — run all linters (Go, YAML, Markdown, Jsonnet, Makefile).
- `make test` — run unit and e2e tests.
- `make verify` — full verification (lint + test + generated-code check).
- `make generate` — regenerate manifests, codegen, and jsonnet.
- `make build` — build the binary.
- `make image` — build the container image.
