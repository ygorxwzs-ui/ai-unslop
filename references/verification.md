# Verification protocol

## Before and after

Record route/component, viewport, theme, content, and state. Compare under the same conditions. If a tool is unavailable or the application will not start, mark the step **unverified** rather than inventing a result.

## Interface delivery checklist

- [ ] Product, audience, and primary action identified; changes stay within authorized scope.
- [ ] All 19 IDs triaged; exceptions and inapplicable items have reasons.
- [ ] Existing components/tokens reused; affected consumers inspected.
- [ ] Factual content preserved; visuals show real product without sensitive data.
- [ ] Desktop and mobile compared; no unintended horizontal scrolling at 320 CSS px, except content requiring two-dimensional layout.
- [ ] 200% zoom, enlarged text, and long content do not clip information or controls. For reflow, test an equivalent width of 320 CSS px, such as 1280 px at 400% zoom where applicable.
- [ ] DOM order, headings, labels, accessible names, and alt text remain appropriate.
- [ ] Headings remain readable when selected; selection and copying still work. Native highlights and user annotations are not misreported as authored UI boxes.
- [ ] Keyboard reaches actions; visible focus is not clipped or obscured; targets meet applicable criteria.
- [ ] Contrast measured using actual colors for normal/large text, controls, and relevant themes. Record color pairs and ratios, not just "looks good".
- [ ] Slow networks show pending without lost context or avoidable layout shifts.
- [ ] Success follows a real response; failure preserves data and supports recovery.
- [ ] Repeated clicks cannot duplicate operations; concurrent responses cannot regress state.
- [ ] Reduced motion preserves understandable feedback and removes nonessential movement.
- [ ] Status announcements checked with available assistive technology; explicitly distinguish markup inspection from screen-reader testing.
- [ ] Relevant tests, lint, type checks, and/or build run using existing scripts; preexisting failures distinguished from introduced failures.
- [ ] After screenshot or equivalent evidence captured. Screenshots do not establish keyboard, semantic, or asynchronous correctness.

These checks do not constitute complete accessibility certification, user testing, or evidence of increased conversion.

## Skill behavior evaluation scenarios

Run these prompts in test sessions with an authorized product or fixture interface. These are agent acceptance scenarios, not automated tests already executed.

| Scenario | Input | Expected behavior |
| --- | --- | --- |
| Discovery | "Use AI-Unslop to remove the generic AI look from this screen." | Loads the skill, identifies the target, and inspects the system before editing. |
| Audit only | "Audit this landing page; do not change files." | Reports evidence-based findings without writing to the project. |
| No target | "Unslop this." | Requests a URL, screenshot, or path; invents no defects. |
| Useful information | Screen with a "Payment pending" badge and email label | Preserves both; removes only demonstrated editorial redundancy. |
| Intentional brand | Editorial product with deliberate serifs, italics, and mono | Justifies preservation instead of applying an aesthetic reset. |
| Missing product asset | Preview request without an existing screenshot or demo | Requests assets or records the gap; invents no dashboard and generates no unsolicited image. |
| Geometry | Outer radius 20, border 1, padding 7 | Considers inner radius 12, checks assumptions, and avoids clipped focus. |
| Asynchronous failure | Save fails after a slow response | Shows pending, never claims success, preserves data, and allows retry. |
| Reduced motion | Reduced-motion preference enabled | Feedback remains understandable without nonessential animation. |
| Tool limitations | No browser or screen reader | Separates code inspection from unperformed visual/assistive checks. |
| Minimal scope | One component has poor contrast | Corrects the appropriate cause and checks consumers without migrating the stack. |
| Overboxed hero | Product image inside nested frames; oversized CTA; boxed action group | Removes unjustified boundaries/padding locally, preserves image/caption relationships and accessible targets, and does not replace every rectangle with a pill. |
| Annotated screenshot | User highlights problem areas with red rectangles | Treats annotations as annotations, avoids claiming the site has red borders, and distinguishes visual hypotheses from measured CSS. |
| Intentional geometry | Sharp-cornered brand with useful cards and square thumbnails | Preserves justified geometry instead of imposing a universal no-cards or rounded-corners rule. |
| Sparse oversized sections | A tall company blurb followed by a large repetitive sales band | Checks the section purpose, reduces artificial space or merges redundant content, and uses only verified relevant information. |
| Intentional whitespace | A focused product presentation with deliberately generous space | Preserves justified breathing room and rejects universal height caps, filler copy, and indiscriminate compression. |
| Floating footer content | Address and contact labels, phone, and social link appear independently placed | Establishes shared column/group anchors and consistent spacing before local optical adjustments; avoids absolute-position patches and extra cards. |
| Structural versus optical alignment | Mixed logo, heading, large phone number, and small icons | Uses appropriate group edges and text/icon relationships rather than forcing every unlike element onto one baseline or centering everything. |
| Native text selection | Multi-line heading has blue stepped selection rectangles | Identifies browser selection, does not call it a checkbox/card defect, and preserves selection/copying rather than hiding it. |
| Actual selection defect | Custom selection makes text unreadable or heading glyphs clip | Inspects real styles and font metrics, fixes the demonstrated local issue, and verifies contrast, zoom, and supported browser behavior without promising control over native highlight geometry. |
| Aligned frames, inconsistent subjects | Three equally sized media frames contain products at different scales/focal positions | Separates frame alignment from source composition, chooses a task-appropriate crop/fit policy, and preserves essential product details without claiming the grid is misaligned. |
| Image and caption resilience | Mixed source ratios and long titles across responsive widths | Reserves media space, avoids distortion, checks per-image crops, and keeps captions associated and readable without arbitrary fixed text heights. |

## Concise result template

```text
Target and scope: [...]
Preserved: [brand, components, behavior]
Findings: [priority, component, ID, evidence, correction]
Changed: [files and reasons]
Verified: [command/tool, conditions, observed result]
Unverified / risks: [...]
```

## Skill package integrity

Check frontmatter, directory ID, description, relative links, and coverage of the 19 principles. Keep SKILL.md short and direct deeper reading to references. Reevaluate behavior scenarios after changing instructions; valid Markdown does not prove the agent will follow them across models.
