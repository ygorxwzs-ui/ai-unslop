<div align="center">

# AI-Unslop

### Less AI noise. More actual product.

An Agent Skill for clearer interfaces, intentional hierarchy, and useful feedback.<br>
Keep the brand. Fix the noise. Ship the smallest meaningful change.

[![GitHub stars](https://img.shields.io/github/stars/ygorxwzs-ui/ai-unslop?style=flat&color=f59e0b)](https://github.com/ygorxwzs-ui/ai-unslop/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/ygorxwzs-ui/ai-unslop?style=flat&color=6366f1)](https://github.com/ygorxwzs-ui/ai-unslop/forks)
[![Last commit](https://img.shields.io/github/last-commit/ygorxwzs-ui/ai-unslop?style=flat&color=10b981)](https://github.com/ygorxwzs-ui/ai-unslop/commits/main/)
[![Open issues](https://img.shields.io/github/issues/ygorxwzs-ui/ai-unslop?style=flat&color=0ea5e9)](https://github.com/ygorxwzs-ui/ai-unslop/issues)

[Quick start](#quick-start) &nbsp; / &nbsp; [Principles](#the-principles) &nbsp; / &nbsp; [Documentation](#documentation) &nbsp; / &nbsp; [Roadmap](#roadmap)

</div>

---

## What it does

AI-Unslop helps coding agents audit and refine generic-looking interfaces without replacing one template with another. It prioritizes product clarity, accessibility, and the design system you already have.

| Instead of | Aim for |
| --- | --- |
| Empty badges and vague promises | Specific copy and verifiable information |
| Decorative mockups hiding the feature | A clear view of the actual product |
| Every card and button competing | Intentional hierarchy and a clear primary action |
| Boxes inside boxes and oversized CTA slabs | Purposeful boundaries, natural proportions, and spacing-led groups |
| Tall sections with almost nothing to say | Content-proportional spacing and useful, verified information |
| Labels and links floating without clear alignment | Shared column anchors, coherent groups, and consistent spacing |
| Random fonts, icons, and spacing | Consistent existing tokens and components |
| Silent clicks and endless skeletons | Honest loading, success, and recovery states |

**Not a rebrand. Not a UI framework. Not an automatic class remover.**

## Quick start

### 1. Install the skill

Clone the repository into the global skill directory:

```sh
git clone https://github.com/ygorxwzs-ui/ai-unslop.git ~/.agents/skills/ai-unslop
```

Already have that directory? Update or inspect the existing installation instead of cloning over it.

Place the entire directory at `~/.agents/skills/ai-unslop/`, a global compatibility location recognized by OpenCode V2. No npm package, API, MCP server, or configuration change is required for the skill itself.

For project distribution, place it at `.opencode/skills/ai-unslop/`. Avoid divergent versions with the same ID: project sources can override global sources. Other Agent Skills clients may use the package according to their own discovery rules.

In OpenCode, mention `@ai-unslop` or explicitly ask to load `ai-unslop`. If it is not listed yet, use `/reload`. The technical ID is lowercase; the editorial name is **AI-Unslop**.

### 2. Give it a target

**Audit without editing**

```text
Use @ai-unslop to audit /pricing. Do not change files.
Report only observed issues and how to verify each correction.
```

**Refine an existing component**

```text
Apply @ai-unslop to ProductHero. Preserve the brand and reuse existing
tokens. Implement and test only necessary corrections; do not invent
screenshots or metrics.
```

**Review a screenshot honestly**

```text
Review this screenshot with @ai-unslop. Distinguish visual observations
from behavior and accessibility that cannot be established from an image.
```

## The principles

**19 practical rules. No universal aesthetic.** Each rule includes implementation guidance, exceptions, and acceptance criteria in [the full reference](references/principles.md).

**Less overboxing, not just fewer rounded cards.** Watch for nested image frames, unnecessarily boxed action groups, oversized rectangular buttons, and repetitive square tiles. Remove unjustified boundaries before tweaking corner radii; preserve functional cards and intentional geometric branding.

**Breathing room, not empty acreage.** A heading, a sentence, and a repeated CTA should not become an oversized section by default. Right-size the layout, merge redundant blocks, and add substance only when it is relevant and verified. Never trade whitespace for invented facts or filler.

**Anchored, not floating.** Related labels, values, icons, and links need shared alignment and predictable spacing. Fix the container and group structure before optical nudges; do not center everything or add cards to hide a broken layout.

**Align the frame, the subject, and the caption deliberately.** Matching image boxes do not guarantee consistent product scale or framing. Choose crops and focal positions for the actual assets, preserve essential details, and keep captions aligned without distorting images.

**Selection is not another card.** Native text highlights can have stepped rectangular edges. Preserve selection and copying; fix real contrast, clipping, or typography problems instead of hiding browser feedback or inventing custom highlight boxes.

| Focus | Principles |
| --- | --- |
| Remove noise | Delete filler badges; drop redundant labels; remove arbitrary italics; use monospace only where needed. |
| Show what matters | Show the actual product; enlarge the main feature; make headlines specific; emphasize the primary CTA. |
| Build coherence | Use a design system; group with spacing; use an accent color intentionally; keep icons consistent. |
| Refine the details | Remove purposeless embellishments; harmonize inner and outer radii; improve text contrast; wrap headlines properly; align optically. |
| Respond to the user | Add loading states; animate useful feedback. |

## How it works

```text
Understand -> Inspect -> Observe -> Triage -> Refine -> Verify
```

- **Before editing:** identify the task, preserve the brand, and inspect existing tokens and consumers.
- **During the work:** prioritize task blockers and accessibility; make the smallest complete correction.
- **Before delivery:** check the same states and viewports, report actual evidence, and name anything unverified.

> Useful content and accessibility are never expendable decoration. Keep meaningful labels, real status indicators, and intentional brand choices.

## Documentation

| File | Purpose |
| --- | --- |
| [SKILL.md](SKILL.md) | Triggers, boundaries, workflow, and the 19 principles. |
| [references/principles.md](references/principles.md) | Observation, implementation, acceptance, and exceptions for every principle. |
| [references/implementation.md](references/implementation.md) | Adaptable semantic, CSS, and state recipes. |
| [references/verification.md](references/verification.md) | Delivery checklist and agent evaluation scenarios. |
| [references/sources.md](references/sources.md) | Research references and standards/heuristics distinction. |

<details>
<summary><strong>Scope, safeguards, and numbering</strong></summary>


- The original list contained 19 items, numbered 1 through 18 and then 20. IDs are preserved without inventing a missing item.
- Original typos were normalized to "filler badges", "redundant labels", "main feature", and "make headlines specific".
- Rules are conditional: preserve accessible labels and legitimate branding; do not impose libraries or rewrite business rules.
- Research supports recommendations; it does not prove conversion improvements or certify WCAG conformance.
- No scripts or dependencies: contextual judgment is essential. Regex-based removal of decorative classes can erase useful information or behavior.

</details>

## Roadmap

These are proposals, not shipped features or completed evaluations:

- [ ] **Real before/after case studies:** approved screenshots, identical viewports, concrete changes, and an explanation of what was intentionally preserved.
- [ ] **Explicit priority rubric:** distinguish task/accessibility blockers, comprehension problems, and cosmetic inconsistencies without pretending to calculate an objective "beauty score".
- [ ] **Complete state coverage:** expand guidance for empty, partial-data, offline, permission-denied, and destructive-action states beyond the existing loading/success/error guidance.
- [ ] **Repeatable visual regression fixtures:** a small authorized example interface, fixed data/viewports, keyboard checks, and reduced-motion comparisons using the project's existing test tools.
- [ ] **Agent behavior evaluations:** run the documented scenarios across supported clients/models and publish actual results, including failures and tool limitations.

Prioritize evidence and repeatability over more aesthetic rules. Keep framework-specific recipes optional and avoid adding runtime dependencies to the skill.

## Maintenance

Keep the entry point concise and detailed guidance in references. Before publication, verify local links, frontmatter, and ID coverage; then run behavioral scenarios from [verification.md](references/verification.md) in the target environment. File integrity is not model-behavior evaluation.

<details>
<summary><strong>Version history</strong></summary>


- **1.0.2 - 2026-11-10:** added overboxing, information-density, structural/image-alignment, and text-selection guidance; proportional CTA checks; screenshot-annotation safeguards; and eleven behavioral evaluation scenarios.
- **1.0.1 - 2026-11-09:** translated every document, prompt, comment, and UI example into English; clarified usefulness/accessibility as joint release conditions; corrected source attribution for numeric typography and CTA guidance; added a proposed improvement roadmap.
- **1.0.0 - 2026-11-09:** created 19 revised principles, audit/implementation instructions, recipes, acceptance criteria, references, and evaluation scenarios.

</details>

---

**Found it useful?** [Give AI-Unslop a star](https://github.com/ygorxwzs-ui/ai-unslop/stargazers) or [share a concrete improvement](https://github.com/ygorxwzs-ui/ai-unslop/issues).
