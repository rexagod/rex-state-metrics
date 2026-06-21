# Guiding principles and tenets — agentic SDLC

**Audience**: Teams adopting an agentic-first SDLC.  
**Relationship**: This doc is the **organizational** “why” and operating model. For day-to-day workflow (context, review, testing), see [agentic-sdlc.md](agentic-sdlc.md).

## Core ideas

These ideas underpin the principles below:

- **Built-in, not bolted on** — Requirements, checks, and outputs are encoded in the workflow (not only reviewed after the fact).
- **API contract between agents** — Every team encodes what they require, what they check, and what they produce—as `AGENTS.md` files, skills, or rules—creating a contract other agents can rely on.
- **Guardrails compose hierarchically** — Org → product → team → repo. Every agent inherits the full chain. By design, guardrails are **non-bypassable** where policy requires it.
- **Humans define the problem; agents execute within guardrails** — Taste and judgment live at intent and design; implementation and validation scale through agents.
- **Role evolution, not replacement** — The goal is output and leverage per person; roles shift toward architecture, encoding expertise, and judgment—not wholesale substitution.

## Principles

Strategic direction aligned with engineering leadership and architectural guardrails. Goals should survive vendor and model changes.

1. **Outcomes, not tools** — Optimize for durable goals (quality, velocity, risk reduction), not a specific IDE, model, or vendor. Tooling changes; outcomes stay.

2. **Rethink workflows through agents** — Redesign how work flows (concurrent validation, encoded checks, atomic change units), not only speed up the old serial gates.

3. **Guardrails are inherited, not inspected** — Expectations live in rules, skills, and repo context so they apply consistently; “catch it in review only” is insufficient for scale.

4. **Measure at the workflow level** — Prefer cycle time, throughput, defect rate, and leading quality indicators over raw “% AI-generated” or line counts.

5. **All-in product scope** — Treat the whole product surface (security, docs, UX consistency, performance, support signals) as part of delivery scope, not optional add-ons after code merges.

6. **Upstream commitment** — Respect upstream and open-source policy: verify contribution rules, attribution, and license implications before shipping agent-assisted changes upstream (see [REDHAT.md](../REDHAT.md)).

## Tenets

How we apply the framework without prescribing a single toolchain:

1. **Non-prescriptive framework** — Teams choose assistants, CI, and practices; the model is defined by outcomes and encoded guardrails, not one stack.

2. **Success through outcomes (efficiency or productivity)** — Success is either the same work with fewer bottlenecks, or more value with the same team—pick the lens that matches the charter.

3. **Quality and leading indicators** — Define quality explicitly (tests, security bars, docs, UX, performance) and track signals that predict defects and rework—not vanity metrics.

4. **Upstream always** — Upstream policy and community norms are part of the definition of done for contributions that leave the org’s boundary.

## Operating-model maxims

Rules for changing how we work **inside** the agentic model. Add to this list as the org learns.

- **Agents first for process change** — To change process, deliverables, or quality bars, **change agents** (context, skills, rules, automation) so behavior matches intent **before** relying on tribal reminders or manual gates alone.

## Related docs

- [agentic-sdlc.md](agentic-sdlc.md) — Playbook: context, development loop, persona lifecycle, review, testing, metrics  
- [../skills/](../skills/) — Tool-agnostic persona skills (QE, PM, engineer, security, docs, and so on)  
- [../AGENTS.md](../AGENTS.md) — Repo-level context for assistants  
- [../REDHAT.md](../REDHAT.md) — Red Hat AI policy and attribution  
