# Red Hat documentation style — condensed reference

Use this file when **drafting** or **self-reviewing** documentation with the **docs-writer** skill. It does not replace the full guides.

## Canonical sources (read the real guide for edge cases)

| Guide | URL | Use for |
|-------|-----|---------|
| Red Hat Technical Writing Style Guide | [stylepedia.net/style/](https://stylepedia.net/style/) | Training, certification, most technical docs **except** as noted below |
| Supplementary Style Guide (product docs) | [redhat-documentation.github.io/supplementary-style-guide/](https://redhat-documentation.github.io/supplementary-style-guide/) | Red Hat **product** documentation |
| Modular Documentation Reference | [redhat-documentation.github.io/modular-docs/](https://redhat-documentation.github.io/modular-docs/) | Concept / procedure / reference modules |
| AsciiDoc markup conventions | [redhat-documentation.github.io/asciidoc-markup-conventions/](https://redhat-documentation.github.io/asciidoc-markup-conventions/) | AsciiDoc specifics |
| Accessibility for writers | [redhat-documentation.github.io/accessibility-guide/](https://redhat-documentation.github.io/accessibility-guide/) | Accessible headings, links, alt text |

**Note:** Product documentation follows **Supplementary Style Guide** and **IBM Style** (IBM Style is primary for product docs; SSG overrides/supplements). Other Red Hat technical docs follow **Stylepedia** (Technical Writing Style Guide).

---

## Self-review checklist

Copy and tick when reviewing a draft:

- [ ] **Audience** clear (internal vs customer; skill level assumed)
- [ ] **Active voice** where it reads naturally; passive only when justified
- [ ] **No contractions**
- [ ] **No unexplained acronyms** on first use (spell out + abbreviation in parentheses if needed)
- [ ] **Sentences** short; no cramming; fix run-ons and comma splices
- [ ] **that** included in clauses where it helps (*Ensure that …*, *Verify that …*)
- [ ] **this/that/these/those** + noun
- [ ] **allow** only for permission; otherwise rephrase
- [ ] **may/should** replaced with unambiguous wording (*can*, *might*, *must*, *we recommend*)
- [ ] **No anthropomorphism** (*the service returns an error*, not *the service refuses*)
- [ ] **Inclusive language** (no *whitelist/blacklist*; no *sanity check*; no *master/slave* where avoidable)
- [ ] **No slang/jargon** from the avoid list (or justified for a technical term)
- [ ] **Product names** not possessive; **abbreviations** not possessive
- [ ] **Numbers** per rules (0–9 spelled out in prose; 10+ numerals; consistency in a paragraph)
- [ ] **Dates/times** unambiguous (month name in prose)
- [ ] **Lists**: lead-in is a complete sentence; items parallel; punctuation matches sentence vs fragment rules
- [ ] **Procedures**: imperative steps; one action per step where possible
- [ ] **Code/examples**: synthetic data only; no real secrets
- [ ] **Links**: meaningful link text; avoid URL shorteners (product-doc guidance)

---

## Grammar and construction (high impact)

- **Countable nouns**: *fewer* / *number* for countable; *less* / *amount* for uncountable.
- **If … then**: Often clearer with *then* after *if* when both clauses are independent.
- **Following**: Use with a noun (*the following interfaces:*).
- **Either … or**: Only for two choices; for three or more use *such as* or restructure.
- **There is / there are**: Rewrite with a clear subject (*Ansible supports …* not *There are multiple formats …*).
- **Using** at sentence end: Often ambiguous; prefer *by using* or *that uses*.
- **Dangling modifiers**: Opening participial phrase must modify the subject (*After you configure …*, not *Having configured …, the product is ready*).
- **Redundant words**: Omit *actually*, *really*, *simply*, *very*, *revert back*, *located on* → *on*.

---

## Word and phrase usage (sample)

Prefer the first column; verify product-specific glossary if your team maintains one.

| Avoid / deprecated | Prefer |
|--------------------|--------|
| codebase | code base |
| navigate to | go to |
| log out from | log out of |
| click on | click |
| fill in/out (form) | complete (form) |
| print out | print |
| leverage | use, take advantage of |
| utilize | use |
| perform the installation of | install |
| is designed to | state what it does (*X works with …*) |
| if you want / if you wish | To \<action\>, … |
| best-of-breed, synergy, paradigm, upskill | Plain, specific wording |
| happy path | primary path, default flow, success path (be explicit) |
| sanity check | confidence check, basic verification, validation check |
| whitelist / blacklist | allowlist / blocklist or denylist |
| master (paired with slave) | primary/replica, main/subordinate, or product-specific terms |

For AI/ML terms (*inference*, *fine-tuning*, *LLM*, etc.), use Stylepedia dictionary entries.

---

## Lists (Red Hat Technical Writing Style Guide)

- **Bulleted**: Order not important; usually **three or more** items (exceptions exist per publication).
- **Ordered**: Sequence matters, or you refer to items by number from elsewhere.
- **Variable / definition lists**: Terms + definitions; often better than wide tables for translation.
- **Procedures**: Numbered steps with a **title**; steps achieve one task.
- **Nesting**: Prefer at most **two** levels.
- **Lead-in**: **Complete sentence** ending with a colon.
- **Do not** break a sentence with a list in the middle and continue after it—restructure.
- **Parallelism**: All items same grammatical pattern (e.g. all imperatives for steps).
- **Punctuation**:
  - All items **complete sentences** → end each with a period.
  - All items **fragments** (no subject+verb as a standalone sentence) → **no** end punctuation on items.
  - Mixed fragment + following sentence in an item → end each item with a period.

---

## Code blocks and commands

- Put **explanations outside** the code block.
- For product docs, **separate** command input and example output into **separate** blocks when both are shown.
- Use **synthetic** hostnames, IPs, and user names.
- Introduce blocks with a complete lead-in (see Style Guide: introducing lists, code, procedures).

---

## Modular documentation (product / AsciiDoc)

Align with the [Modular Documentation Reference Guide](https://redhat-documentation.github.io/modular-docs/):

| Module type | Purpose |
|-------------|---------|
| **Concept** | Explain *what* and *why*; background; no numbered steps |
| **Procedure** | *How* to accomplish a task; numbered steps |
| **Reference** | *What* (APIs, options, tables, quick facts) |

Practices:

- One primary user task or concept per assembly; reuse modules rather than copy-paste.
- **Short descriptions** / abstracts: avoid starting with admonitions (product guidance).
- Follow assembly and module naming conventions your doc repo uses.

---

## AsciiDoc conventions (basics)

- Use semantic markup (headings, lists, admonitions) per [AsciiDoc Mark-up Quick Reference](https://redhat-documentation.github.io/asciidoc-markup-conventions/).
- Mark **non-translatable** strings (paths, commands, UI labels) consistently so localization can skip them.
- Prefer stable anchors and cross-references that survive modular reuse.

---

## Release notes (product documentation)

Follow **Supplementary Style Guide** release-note guidance (tense, headings, approved section names, Jira references). In general:

- Be **factual** and **specific**; avoid marketing fluff.
- Use **headings** per team template.
- Clarify **technology preview** or support implications when your team requires it.

---

## Cross-references and links

- Do not send readers on a link hunt—each topic should stand alone enough for the task.
- Use descriptive link text (*see the installation guide*), not *click here*.
- Avoid URL shorteners in customer-facing docs.

---

## When unsure

1. Check **Supplementary Style Guide** (product) or **Stylepedia** (general).
2. Prefer **plain, literal** wording over metaphor or idiom.
3. State in the doc or handoff: **TBD**, **verify with SME**, or **needs editorial pass**.
