# Contributing — Agentic First

This project uses an **agentic-first** workflow: AI coding agents are the primary authors of implementation, while humans set intent, review, and own outcomes. For the principles behind this approach, see [docs/principles.md](docs/principles.md).

Contributions are welcome—whether you are writing code by hand, directing an agent, or improving the scaffolding itself.

## Before you start

1. **Read [AGENTS.md](AGENTS.md)** — project context, architecture, conventions, and common pitfalls. This is the single most important file for agent (and human) quality.
2. **Skim [docs/agentic-sdlc.md](docs/agentic-sdlc.md)** — the team playbook: development loop, skills lifecycle, review, testing, and metrics.
3. **Review [REDHAT.md](REDHAT.md)** — Red Hat AI code assistant policy: attribution, sensitive data, upstream rules.

If you use **Cursor**, the rules in `.cursor/rules/` apply automatically. For **Claude Code**, `CLAUDE.md` points at `AGENTS.md`.

## Upstream Kubernetes community

This project is a [Kubernetes SIGs](https://github.com/kubernetes-sigs) project. The Kubernetes community abides by the CNCF [code of conduct](code-of-conduct.md).

- [Contributor License Agreement](https://git.k8s.io/community/CLA.md) — required before we can accept your pull requests.
- [Kubernetes Contributor Guide](https://k8s.dev/guide) — main contributor documentation.
- [Contributor Cheat Sheet](https://k8s.dev/cheatsheet) — common resources for existing developers.
- [Slack channel](https://kubernetes.slack.com/messages/sig-instrumentation)
- [Mailing List](https://groups.google.com/a/kubernetes.io/g/sig-instrumentation)

## Ticket-first workflow

**If it is not in Jira (or your team's tracker), it does not exist** for trackable engineering work.

- Create or reference a ticket **before** starting implementation—features, bugs, spikes, tech debt, meaningful refactors.
- Write tickets for agents: **Goal**, **Acceptance criteria** (testable), **Files/modules**, **Constraints**, **Links** to prior art.
- Commits and PRs carry the ticket key (e.g. `MON-123` in the subject or PR description).
- Discovered work becomes new tickets—do not silently expand a change set off-ticket.

See [docs/agentic-sdlc.md](docs/agentic-sdlc.md) and [skills/product-engineering.md](skills/product-engineering.md) for full discipline.

## Making changes (the agentic loop)

```
Specify intent → Agent proposes changes → Human reviews → Refine or accept → Repeat
```

- **One coherent goal per session.** State scope, point to files, list non-negotiables (no API break, no new deps, etc.).
- **Use skills.** The `skills/` directory defines tool-agnostic personas across the lifecycle—product manager, engineer, QE, security, UX, docs, performance, and more. Reference the relevant skill in your prompt to activate its guardrails.
- **Agents are strong at**: boilerplate, refactors, tests, docs, localized bug fixes with reproducers.
- **Humans should lead**: novel architecture, security-sensitive paths, performance-critical design, ambiguous product trade-offs.
- If the session drifts, **reset** with a fresh summary or new session.

## Attribution

All AI-assisted contributions require a commit trailer per [REDHAT.md](REDHAT.md):

```text
Assisted-by: <name of code assistant>
Generated-by: <name of code assistant>
```

| Situation | Trailer |
|-----------|---------|
| You directed the work and edited meaningfully | `Assisted-by` |
| Large generated chunk, minimal human edit | `Generated-by` |
| Unsure | `Assisted-by` |

Prefer `Assisted-by:` or `Generated-by:` over `Co-Authored-By:` for AI tools — `Co-Authored-By:` may have CLA and contributor-stats implications in some projects.

## Code review expectations

Agent-produced code goes through the same review as hand-written code. Reviewers should focus on:

- **Semantic correctness** and edge cases
- **Hallucinated APIs**, wrong flags, or imaginary config
- **Over-engineering** and missing error handling
- **Consistency** with existing patterns in the codebase

Agent-assisted review (summarizing diffs, spotting inconsistencies) **supplements** but never replaces human review. For adversarial review of high-risk changes, see [skills/adversarial-qe.md](skills/adversarial-qe.md).

### Persona review comments

When a persona skill performs a review, it posts a **comment** to the Jira issue or PR/MR under review. These comments are always AI-assisted and human-directed; they include a standard header identifying the persona, the AI tool and model used, and the human who directed the review. See [docs/agentic-sdlc.md](docs/agentic-sdlc.md) for the format and posting rules.

## Testing

- Use agents to **write** tests, then **critically review** them: check for behavior vs. implementation coupling, edge-case coverage, and maintainability.
- **Test-first pattern** is encouraged: agree on cases, write failing tests, implement, review.
- Map tests back to acceptance criteria from the ticket. See [skills/test-writing-qe.md](skills/test-writing-qe.md).
- Prefer golden test files under `tests/golden/` for resolver output verification.

Run `make test` (unit + e2e) and `make lint` before submitting a PR. Use `make verify` for the full gate.

## CI / compliance

- Agent-produced code uses the **same CI, scans, and gates** as hand-written code. No bypass.
- No secrets in commits—use env vars and a gitignored `.env` with synthetic values in docs.
- Attribution trailers are expected on every AI-assisted commit.
- All source files must include Apache 2.0 license headers (enforced by `make lint`).

## Upstream contributions

Before contributing agent-assisted changes to the **upstream** kubernetes-sigs/resource-state-metrics project:

1. **Check that project's AI policy**—the Kubernetes community may have specific rules on AI-assisted contributions.
2. Follow attribution and license requirements from [REDHAT.md](REDHAT.md).

## Updating scaffolding

Context is infrastructure. Stale context is debt.

- **`AGENTS.md`** — Update when architecture, conventions, or pitfalls change.
- **`skills/`** — Keep personas in sync with team conventions; add new skills as roles emerge.
- **`.cursor/rules/`** — Maintain Cursor-specific rules if your team uses Cursor.
- **`REDHAT.md`** — Keep aligned with the canonical Red Hat AI policy wiki; if this file conflicts, the wiki wins.

## Quick reference

| Resource | Purpose |
|----------|---------|
| [AGENTS.md](AGENTS.md) | Project context for any assistant |
| [REDHAT.md](REDHAT.md) | AI policy, attribution, upstream rules |
| [docs/agentic-sdlc.md](docs/agentic-sdlc.md) | Workflow playbook |
| [docs/principles.md](docs/principles.md) | Organizational principles and tenets |
| [skills/](skills/) | Tool-agnostic lifecycle personas |
