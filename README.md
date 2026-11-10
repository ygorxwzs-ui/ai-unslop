# AI-Unslop

An Agent Skill that replaces generic AI-generated styling with product clarity, intentional hierarchy, and reliable feedback without imposing a single aesthetic.

## Installation and usage

Place the entire directory at `~/.agents/skills/ai-unslop/`, a global compatibility location recognized by OpenCode V2. No npm package, API, MCP server, or configuration change is required for the skill itself.

For project distribution, place it at `.opencode/skills/ai-unslop/`. Avoid divergent versions with the same ID: project sources can override global sources. Other Agent Skills clients may use the package according to their own discovery rules.

In OpenCode, mention `@ai-unslop` or explicitly ask to load `ai-unslop`. If it is not listed yet, use `/reload`. The technical ID is lowercase; the editorial name is **AI-Unslop**.

### Example prompts

```text
Use @ai-unslop to audit /pricing. Do not change files.
Report only observed issues and how to verify each correction.
```

```text
Apply @ai-unslop to ProductHero. Preserve the brand and reuse existing
tokens. Implement and test only necessary corrections; do not invent
screenshots or metrics.
```

```text
Review this screenshot with @ai-unslop. Distinguish visual observations
from behavior and accessibility that cannot be established from an image.
```

## Contents

| File | Purpose |
| --- | --- |
| [SKILL.md](SKILL.md) | Triggers, boundaries, workflow, and the 19 principles. |
| [references/principles.md](references/principles.md) | Observation, implementation, acceptance, and exceptions for every principle. |
| [references/implementation.md](references/implementation.md) | Adaptable semantic, CSS, and state recipes. |
| [references/verification.md](references/verification.md) | Delivery checklist and agent evaluation scenarios. |
| [references/sources.md](references/sources.md) | Research references and standards/heuristics distinction. |

## Scope decisions

- The original list contained 19 items, numbered 1 through 18 and then 20. IDs are preserved without inventing a missing item.
- Original typos were normalized to "filler badges", "redundant labels", "main feature", and "make headlines specific".
- Rules are conditional: preserve accessible labels and legitimate branding; do not impose libraries or rewrite business rules.
- Research supports recommendations; it does not prove conversion improvements or certify WCAG conformance.
- No scripts or dependencies: contextual judgment is essential. Regex-based removal of decorative classes can erase useful information or behavior.

## Recommended next improvements

These are proposals, not shipped features or completed evaluations:

1. **Real before/after case studies:** approved screenshots, identical viewports, concrete changes, and an explanation of what was intentionally preserved.
2. **Explicit priority rubric:** distinguish task/accessibility blockers, comprehension problems, and cosmetic inconsistencies without pretending to calculate an objective "beauty score".
3. **Complete state coverage:** expand guidance for empty, partial-data, offline, permission-denied, and destructive-action states beyond the existing loading/success/error guidance.
4. **Repeatable visual regression fixtures:** a small authorized example interface, fixed data/viewports, keyboard checks, and reduced-motion comparisons using the project's existing test tools.
5. **Agent behavior evaluations:** run the documented scenarios across supported clients/models and publish actual results, including failures and tool limitations.

Prioritize evidence and repeatability over more aesthetic rules. Keep framework-specific recipes optional and avoid adding runtime dependencies to the skill.

## Maintenance

Keep the entry point concise and detailed guidance in references. Before publication, verify local links, frontmatter, and ID coverage; then run behavioral scenarios from [verification.md](references/verification.md) in the target environment. File integrity is not model-behavior evaluation.

### History

- **1.0.1 - 2026-11-09:** translated every document, prompt, comment, and UI example into English; clarified usefulness/accessibility as joint release conditions; corrected source attribution for numeric typography and CTA guidance; added a proposed improvement roadmap.
- **1.0.0 - 2026-11-09:** created 19 revised principles, audit/implementation instructions, recipes, acceptance criteria, references, and evaluation scenarios.
