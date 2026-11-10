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

### Recognize overboxing, not just excessive rounding

Generic generated interfaces can overuse sharp rectangles just as easily as rounded cards. Diagnose the structure, not the model that produced it. Claims that a specific model routinely creates this pattern require separate evidence.

Look for:

- **Frames inside frames:** a section surface encloses a card, which encloses a padded image frame, which encloses a separately boxed caption without distinct functions.
- **Oversized CTA slabs:** padding, width, or height makes a short action look like a banner or content card rather than a control.
- **Boxed action groups:** a primary button and secondary link are wrapped in another bordered, filled, or excessively padded rectangle for no reason.
- **Repeated rigid tiles:** unrelated content is forced into identical square cards or equal-height blocks regardless of its natural size and reading order.
- **Arbitrary fixed geometry:** `aspect-ratio: 1`, fixed heights, or large minimum heights create empty space, crop important product details, or stretch simple navigation actions.

For each visible boundary, ask: **Does it establish interaction, containment, status, or a meaningful group that spacing alone cannot communicate?** If not, try removing that boundary and its redundant padding. A layout wrapper may still be necessary for grid, positioning, or semantics; remove its unnecessary styling, not automatically the element.

Start with shared alignment, natural content proportions, and spacing. Keep the main CTA prominent but proportionate to its label, touch target, and neighboring content. Let a secondary action remain visually secondary. Consider one meaningful boundary instead of several nested frames, but do not impose a universal border or card quota.

**Accept:** product imagery has room to communicate, captions remain associated, actions still look actionable, and focus/contrast/touch targets survive. Sharp corners can be intentional; changing every rectangle to a pill is not a correction. Preserve justified cards, dialogs, data tables, image crops, and deliberate geometric branding.

**Screenshot discipline:** distinguish user-drawn highlights from rendered UI. Red annotation rectangles are not proof that the site has red borders. Inspect code or an unannotated capture before making claims about actual borders, padding values, or click areas. A screenshot supports a visual hypothesis, not measured DOM geometry.

### Match section size to information value

Whitespace should clarify relationships, create emphasis, or support reading. It should not make a few generic sentences occupy several screens. The goal is appropriate information density, not maximum density or minimal whitespace.

Look for:

- **Thin sections stretched tall:** a heading, one short paragraph, and a link spread across a large section with no supporting information or deliberate visual role.
- **Disconnected columns:** a short heading on the far left and one sentence on the far right, separated by a gap that weakens their relationship.
- **Repeated thin CTA bands:** a full section repeats the previous section's sales message without answering another question or offering a distinct next step.
- **Artificial height:** fixed heights, `min-height: 100vh`, excessive block padding, or large spacers unrelated to content and task.
- **Sparse decision support:** a business page asks for contact while leaving out available, relevant buying information. Visual cleanliness is not a reason to hide facts people need.

Use this order of correction:

1. Identify the question the section should answer and the information actually available.
2. Remove avoidable fixed/minimum heights and reduce disproportionate gaps/padding using existing tokens. Keep readable line lengths and accessible controls.
3. Bring related copy closer; merge sections that repeat the same purpose, or remove a redundant CTA band. Keep distinct tasks separate when grouping is useful.
4. Where the task needs more substance, add only verified, relevant material already provided or approved: product categories, specifications, ordering process, eligibility, delivery coverage, purchasing terms, or real product/company imagery.
5. If necessary information is missing, request it or report the gap. Do not invent minimum orders, lead times, history, certifications, metrics, or testimonials. Do not replace empty space with decorative icons, cards, or generic paragraphs.

**Accept:** each section answers a distinct useful question; its height follows its content and intentional role; users can scan connected information without unnecessary scrolling. Compare narrow/wide layouts and check that compression has not created crowding. Do not enforce a universal pixels-per-word ratio, section-height cap, or requirement to place everything above the fold.

**Exceptions:** a focused hero, editorial pause, premium product presentation, accessible reading layout, or touch-first workflow may intentionally use generous space. Justify it by the product and task rather than a generic "minimalist" template. Treat screenshot observations as hypotheses; inspect CSS before blaming exact height or padding values.

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
- **Check rectangular decoration too:** a border, background panel, or thick image mat can be an embellishment even without shadows or rounded corners. Apply the overboxing diagnosis in principle 08 before adding another surface.
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

### Review text selection without mistaking it for a component

Blue rectangles behind dragged-over text are normally the browser's selection highlight, not checkboxes, cards, or designed background panels. Different line lengths naturally produce stepped highlight edges. That alone is not a UI defect.

- **Observe:** distinguish native selection from authored `::selection`, inline backgrounds, focus outlines, and screenshot annotations. Look for actual unreadable selected text, clipped accents/descenders, or unintended glyph collisions rather than assuming rectangular highlights are wrong.
- **Inspect:** font loading, computed line-height, font metrics, nested inline spans, overflow, and selected/unselected states in supported browsers. Tight display typography may make highlight bands touch or overlap; screenshot appearance alone does not establish the cause or broken rendering.
- **Implement:** fix demonstrated typography/clipping issues locally. If custom selection is requested and useful, use appropriate selection foreground/background tokens and verify their real contrast. Native selection is a valid default; styling it is not mandatory for a polished interface.
- **Preserve:** copying, dragging to select, keyboard selection, visible focus, and forced-colors behavior. Never use `user-select: none`, transparent selection, blocked copy events, per-word wrappers, or custom JavaScript highlight overlays to hide the issue.
- **Accept:** selected and unselected text remain readable at relevant zoom levels, long headings wrap correctly, and no text is unintentionally clipped. Compare selection within one line and across multiple lines; verify copying where possible. Browser-controlled selection geometry is not a CSS card to reshape with padding or border radius.

See the [MDN selection reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/::selection) for supported properties and browser limitations. Brand consistency does not justify overriding useful platform behavior.

## 17 - Align optically, not just mathematically

- **Observe:** play symbols, arrows, and logos look displaced despite centered boxes.
- **Implement:** align structure with grid/flex and baselines; adjust the internal drawing or apply a small, justified local compensation. Respect the library's optical sizing before introducing transforms.
- **Accept:** inspect at actual size with text, focus, and different pixel densities. Do not move the hit area or reading order to fix a silhouette. Never apply a universal "1 px fix" to every icon [S11].

### Establish anchors before optical polish

"Align by eye" does not mean freely positioning every element. First establish a coherent layout; optical compensation is the final local adjustment, not a substitute for structure.

Look for:

- **Floating groups:** a heading, address, phone number, and social link appear independently placed rather than belonging to recognizable columns or stacks.
- **Drifting edges:** labels and their values start on slightly different axes because of inconsistent wrapper padding, default margins, or unrelated widths.
- **Unexplained vertical offsets:** equivalent column headings start at different levels without content or brand justification.
- **Inconsistent group rhythm:** label-to-value gaps and value-to-secondary-link gaps vary arbitrarily between comparable groups.
- **Mixed text/icon alignment:** arrows and social icons align to unrelated boxes rather than the baseline or optical center appropriate to their labels.

Correct the shared container and column structure first. Use grid/flex, explicit grouping, existing spacing tokens, and logical alignment. In a footer, treat identity, address, and contact as coherent groups; align comparable headings intentionally, keep each group's content on a shared inline-start edge, and place secondary links with their related content.

Do not force a logo top edge, text baseline, and different-sized phone number onto one universal axis. Choose anchors appropriate to each relationship. Unequal column widths or asymmetric composition can be intentional; justify them instead of distributing every item equally across the available width.

Then remove accidental local margins/padding and apply optical adjustments only where the drawing requires them. Do not repair structural drift using absolute positioning, arbitrary transforms, manual spaces, or extra cards. Preserve semantic elements such as address lists and navigation where appropriate.

**Accept:** each element has an understandable relationship to a column, baseline, or content group; comparable groups follow a consistent rhythm; icons remain associated with their labels. Narrow layouts stack in a sensible DOM order without unexplained offsets. Check loaded fonts and zoom before claiming exact alignment. User-drawn red guide lines are evidence of the user's concern, not rendered UI boundaries or measured coordinates.

### Decide what image alignment means

Equal image rectangles do not guarantee comparable product presentation. Before changing CSS, distinguish:

1. **Frame alignment:** media top/bottom edges, column widths, gutters, and alignment with the section container.
2. **Subject alignment:** product scale, visible area, focal position, orientation, and background balance inside each source image.
3. **Caption alignment:** image-to-title spacing, title/metadata baselines, and description flow when text wraps.

Choose which relationships the section needs. A comparable catalog may benefit from similar product scale and focal placement; an editorial/lifestyle collection may intentionally mix compositions. In the supplied type of three-image collection, equal square frames can already be aligned while photographed subjects occupy very different positions. Describe that as a composition/normalization concern, not proof of a broken grid.

Inspect source image dimensions, existing crops, and the product details people need to see. Use a justified shared aspect ratio for comparable frames; do not automatically force square images. Choose `contain` when the whole product must remain visible, accepting intentional surrounding space. Choose `cover` when cropping is appropriate and safe; verify each asset rather than relying on a universal center crop.

Use approved per-image focal positions only when source framing needs them and existing media conventions support them. If CSS cannot achieve suitable composition without losing product details, request a better source image or approved crop. Never stretch an image, invent missing pixels, or imply that differently framed images are a fair size comparison.

Keep headings and metadata associated with the correct image; define sensible wrapping instead of fixing all text heights or absolutely positioning captions. Reserve media space before image load, and inspect narrow layouts, long titles, and loading/error behavior where available.

**Accept:** frame edges and gutters follow the intended grid, important product details remain visible, and scale/focal treatment is consistent enough for the section's task or intentionally varied. Captions remain coherent under wrapping. Do not add matching borders, arrows, fixed heights, or transforms merely to conceal inconsistent source photography.

## 18 - Add loading states

- **Observe:** clicks receive no response, submissions duplicate, skeletons never end, or failures erase data.
- **Implement:** represent idle -> pending -> success/error in the real flow. Use a local indicator, waiting text, and `aria-busy` where appropriate. A persistent status region announces updates without stealing focus. Use determinate progress only with real measurements. Preserve input and support recovery.
- **Accept:** exercise slow networks, failures, and retries. Pending resolves or offers an exit according to the product's timeout/cancellation policy. Stale requests cannot overwrite current results. Client-side protection does not replace server idempotency. Never introduce fake delays to showcase animation [S1, S8].

## 20 - Animate useful feedback

- **Observe:** every section reveals on scroll, exaggerated hover effects, or motion unrelated to an action/state.
- **Implement:** animate to confirm changes or explain spatial relationships; prefer existing duration/easing tokens. Short opacity/transform transitions are often cheaper than geometry animation but do not guarantee performance. Avoid `transition: all`.
- **Accept:** the final state and text remain understandable without animation. `prefers-reduced-motion` removes nonessential motion. Never depend on `animationend` to release an operation. Motion does not delay tasks or cause flashing. WCAG 2.3.3 is AAA; honoring reduced motion is nevertheless a requirement of this skill [S1, S12].
