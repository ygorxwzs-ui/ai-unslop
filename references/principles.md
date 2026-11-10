# Operational principles

Every rule requires observation, a minimal correction, and validation. Numbers are IDs, not a fixed execution order. Sources [S1]-[S13] are listed in [sources.md](sources.md). Aesthetic rules are heuristics, not WCAG requirements.

## 01 - Delete filler badges

- **Observe:** badges such as "Revolutionary", "AI-powered", or "Next-gen" that add no information.
- **Implement:** remove the badge and close the resulting gap. Keep truthful, useful status, beta, plan, count, and warning indicators.
- **Accept:** each remaining badge answers a user question. Status does not rely on color alone. Never remove a filter or control merely because it resembles a badge.
- **Basis:** synthesis of hierarchy and reduced visual competition [S5, S6].

## 02 - Drop redundant labels

- **Observe:** "Features" above "Our features", or an icon, category, and title repeating the same information.
- **Implement:** remove editorial repetition, not accessible names. Preserve visible input labels, units, table headers, captions, and context needed outside the original visual position.
- **Accept:** fields remain identifiable without placeholders; icon-only buttons retain accessible names. Heading structure and associations remain correct [S1, S9].

## 03 - Remove arbitrary italics

- **Observe:** one slanted word in every heading without a meaningful distinction.
- **Implement:** remove local decorative spans/classes. Preserve meaningful `<em>`, work titles, conventional terminology, and the brand's editorial language.
- **Accept:** hierarchy works without random font switching; do not globally reset `em` or `i`. Use existing weights and sizes when sufficient [S10].

## 04 - Use monospace only where needed

- **Observe:** paragraphs, navigation, and labels set in mono merely to look technical.
- **Implement:** use the existing interface font; retain mono for code, commands, identifiers, and data requiring character columns. For numeric tables, consider `font-variant-numeric: tabular-nums` before changing font families.
- **Accept:** long text stays readable, identifiers remain distinguishable, and numeric columns align. A deliberately monospace brand does not require migration [S10; numeric-font supplement].

## 05 - Use a design system

- **Observe:** equivalent colors, gaps, radii, and variants defined inconsistently.
- **Implement:** inspect DESIGN.md, theme files, CSS variables, and the local component library first. Change a shared token only when all consumers need that adjustment; otherwise fix the local variant.
- **Accept:** new values have explicit roles and reuse existing scales. Do not introduce a framework or copy Material/GOV.UK branding merely because they are references [S10].

## 06 - Show the actual product

- **Observe:** abstractions, invented dashboards, and illegible mockups replacing a functional demonstration.
- **Implement:** use an approved screenshot, working component, or real flow with clearly identified demo data. Prioritize one task and its outcome. Protect personal data; crop without misrepresenting capabilities. Provide dimensions/aspect ratio and appropriate text alternatives.
- **Accept:** the visual helps explain the product. Without a real asset, request one or record the gap; never fabricate evidence. Do not lazy-load the main product image by default [S6].

## 07 - Enlarge the main feature

- **Observe:** the key capability has the same weight as secondary details or appears in an incomprehensible thumbnail.
- **Implement:** give the central flow, preview, tool, or result more room; reduce competition before increasing size. Keep the CTA visible in context.
- **Accept:** the main content is recognizable at relevant widths without overflow, lost controls, or distortion. "Larger" does not mean consuming the entire first viewport [S5, S6].

## 08 - Group with spacing

- **Observe:** everything lives in cards, separators repeat, or related and unrelated content share identical spacing.
- **Implement:** use `gap`, stacks, and logical properties with existing tokens. Keep within-group spacing smaller than between-group spacing. Preserve DOM order when stacking on mobile.
- **Accept:** headings stay close to the content they introduce. Retain borders/surfaces when needed for interaction, tables, or contrast rather than removing them automatically [S4].

## 09 - Make headlines specific

- **Observe:** "Elevate your experience", "The future is here", or "Everything you need".
- **Implement:** name an action/capability + object + context or verifiable benefit. Example: "Organize orders by delivery deadline". Never invent time savings or guaranteed outcomes.
- **Accept:** headings alone explain the page and sections with an appropriate semantic hierarchy. Preserve the product's language, terminology, and accuracy [S5].

## 10 - Emphasize the primary CTA

- **Observe:** many equally prominent buttons, vague CTAs, or decoration stronger than the action.
- **Implement:** use the existing primary variant, specific text such as "Create project", and quieter secondary actions. Use links for navigation and buttons for actions. The same action may repeat on long pages without creating competing priorities within one group.
- **Accept:** keyboard, focus, hover, pending, and error states work. Meet the WCAG 2.2 AA target-size criterion of 24 x 24 CSS px or its applicable exceptions, including spacing; prefer larger targets where appropriate. No false urgency, manipulated consent, or hidden costs [S1; button supplement].

## 11 - Use an accent color intentionally

- **Observe:** missing color hierarchy or multiple saturated colors competing for attention.
- **Implement:** reuse the brand accent for action/selection. Without one, choose and document a context-appropriate token; never add color merely to satisfy a checklist. Keep error, warning, and success meanings distinct.
- **Accept:** on-accent text, focus, and states have sufficient contrast in each theme. Color is never the sole indicator; an intentional monochrome interface may not need a new accent [S1-S3].

## 12 - Keep icons consistent

- **Observe:** accidental mixing of outlines, fills, emoji, weights, and optical sizes.
- **Implement:** reuse the installed family and its sizes/weights. Hide decorative icons from the accessibility tree; name controls. Do not replace logos with generic icons or erase intentional active-state distinctions.
- **Accept:** meaning, alignment, and density are coherent, including RTL where applicable. Label ambiguous icons; consistency does not require identical geometry [S11].

## 13 - Remove purposeless embellishments

- **Observe:** glows, blobs, particles, grids, frames, or shadows applied to every surface.
- **Implement:** remove effects competing with content or hurting performance. Preserve intentional visual identity, affordances, focus, functional elevation, and necessary separation.
- **Accept:** the task becomes clearer while the brand remains recognizable. Do not make the entire product gray or remove every border as dogma [S5, S6].

## 14 - Harmonize inner and outer radii

- **Observe:** nested corners do not follow the spacing between surfaces.
- **Implement:** for concentric rectangles with circular radii and uniform insets, use `inner_radius = max(0, outer_radius - inset)`. If padding starts at the inner edge of a bordered container, the outer-edge-to-child inset is `border + padding`.
- **Accept:** inspect rendered geometry. Elliptical/percentage radii, asymmetric insets, and CSS radius normalization require per-corner/axis analysis; the formula is not universal. Do not use `overflow: hidden` when it clips focus or popovers [S13].

## 15 - Improve text contrast

- **Observe:** nearly invisible secondary text, placeholders, or links; text over images/gradients.
- **Implement:** measure actual composited colors, accounting for opacity, theme, and background. Normal text requires at least 4.5:1. Large text requires 3:1, starting at 18 pt (24 CSS px) regular or 14 pt (approximately 18.67 CSS px) bold. Never round a failing result up to a pass.
- **Accept:** check states and changing backgrounds. Necessary control/graphic parts require 3:1 against adjacent colors where applicable. Logo, incidental-content, and inactive-control exceptions do not justify unreadable active text. Color checks alone do not establish full WCAG conformance [S1-S3].

## 16 - Wrap headlines properly

- **Observe:** isolated words, awkward hard breaks on mobile, or clipping with enlarged fonts.
- **Implement:** adjust reading width and type scale; try `text-wrap: balance` for short headings with normal wrapping as fallback. Avoid viewport-dependent `<br>` and `nowrap`; retain justified editorial breaks.
- **Accept:** test loaded fonts, 320 CSS px, zoom, and longer/translated text. `ch` is approximate, not a guaranteed letter count. Balancing has browser and line-count limitations [S7].

## 17 - Align optically, not just mathematically

- **Observe:** play symbols, arrows, and logos look displaced despite centered boxes.
- **Implement:** align structure with grid/flex and baselines; adjust the internal drawing or apply a small, justified local compensation. Respect the library's optical sizing before introducing transforms.
- **Accept:** inspect at actual size with text, focus, and different pixel densities. Do not move the hit area or reading order to fix a silhouette. Never apply a universal "1 px fix" to every icon [S11].

## 18 - Add loading states

- **Observe:** clicks receive no response, submissions duplicate, skeletons never end, or failures erase data.
- **Implement:** represent idle -> pending -> success/error in the real flow. Use a local indicator, waiting text, and `aria-busy` where appropriate. A persistent status region announces updates without stealing focus. Use determinate progress only with real measurements. Preserve input and support recovery.
- **Accept:** exercise slow networks, failures, and retries. Pending resolves or offers an exit according to the product's timeout/cancellation policy. Stale requests cannot overwrite current results. Client-side protection does not replace server idempotency. Never introduce fake delays to showcase animation [S1, S8].

## 20 - Animate useful feedback

- **Observe:** every section reveals on scroll, exaggerated hover effects, or motion unrelated to an action/state.
- **Implement:** animate to confirm changes or explain spatial relationships; prefer existing duration/easing tokens. Short opacity/transform transitions are often cheaper than geometry animation but do not guarantee performance. Avoid `transition: all`.
- **Accept:** the final state and text remain understandable without animation. `prefers-reduced-motion` removes nonessential motion. Never depend on `animationend` to release an operation. Motion does not delay tasks or cause flashing. WCAG 2.3.3 is AAA; honoring reduced motion is nevertheless a requirement of this skill [S1, S12].
