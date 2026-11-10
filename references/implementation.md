# Implementation recipes

Independent examples, not a new design system or globally applicable snippets. Adapt names and values to existing tokens, components, and stack. Illustrative snippets do not replace product tests.

## Hierarchy, grouping, and headlines - 05, 07, 08, 16

```css
/* Illustrative names: map these to the project's real tokens. */
.feature { display: grid; gap: var(--space-section); }
.feature__copy { display: grid; gap: var(--space-related); }
.feature__title {
  max-inline-size: 22ch;
  margin: 0;
  text-wrap: balance;
}
.feature__preview {
  display: block;
  inline-size: 100%;
  block-size: auto;
}
```

Unsupported browsers retain normal wrapping. Do not make 22ch a universal width. Set real image `width`/`height` attributes to reserve space; `alt` should convey relevant information without repeating the entire caption. Do not distort screenshots to fit the layout.

## Copy, fonts, and semantics - 02, 03, 04, 09

Before: an "AI-powered" badge + "A *revolutionary* experience" heading + "Learn more" button.

After, if the capability is real: "Compare proposals by price and deadline" + a comparison preview + "Compare proposals". Never promise "cut costs by 80%" without evidence.

```html
<label for="project-name">Project name</label>
<input id="project-name" name="projectName" autocomplete="off">
```

A nearby heading or placeholder does not replace this label. Do not apply `font-style: normal` to every `em`. For numeric columns, adapt:

```css
.amount { font-variant-numeric: tabular-nums; text-align: end; }
```

## Text-selection feedback - 15, 16

Prefer native selection unless customization is justified. If the project already defines selection tokens, adapt a scoped rule such as:

```css
.hero-copy::selection {
  color: var(--selection-text);
  background-color: var(--selection-background);
}
```

These illustrative tokens must exist and their contrast must be measured. Check nested spans and the browser's highlight inheritance rather than assuming this selector styles every descendant identically. Do not apply radius, margins, or padding to reshape selection rectangles: they are not supported selection-box layout properties.

Inspect the heading's actual font and line-height if glyphs collide or clip. Change only demonstrated typography defects; do not inflate line spacing merely to make stepped native highlights look like cards. Retain platform fallback, test supported browsers, and allow user forced-color settings. Never disable selection or copying as a visual fix.

## CTA, focus, and accent - 10, 11, 15

Reuse the house button and its states. For native HTML, use `<a href="...">` for a destination and `<button type="submit">` for submission. Never turn a `div` into a button for appearance alone.

```css
.primary-action {
  color: var(--on-accent);
  background: var(--accent);
}
.primary-action:focus-visible {
  outline: 2px solid var(--focus-ring);
  outline-offset: 3px;
}
```

These tokens must exist and their contrast must be verified. Outline thickness alone does not guarantee accessible focus: consider adjacency, clipping, and obstruction. Reuse system dimensions and variants instead of introducing another global button.

## Remove redundant boxes before tuning corners - 08, 10, 13

First determine whether the boundary is needed. Do not apply this recipe globally: reuse the project's spacing and button variants, and preserve accessible target dimensions.

```css
/* A layout group does not automatically need its own visible card. */
.hero-actions {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: var(--space-related);
}
.hero-product-image {
  display: block;
  inline-size: 100%;
  block-size: auto;
}
```

For the affected component, remove redundant frame borders, surface fills, and padding from the original rules rather than adding layers of overrides. Keep layout/semantic wrappers if needed. Preserve a figure caption close to its image without automatically giving it another panel.

Use the existing content-sized primary button variant instead of a fixed-width CTA slab; retain full-width buttons when they improve mobile interaction. Do not shrink controls below applicable target-size requirements. Natural image proportions are a starting point, not a ban on intentional art direction or useful thumbnail crops.

## Right-size sparse sections - 07, 08, 09

Inspect the source rules before editing: a tall-looking section may result from padding, minimum height, grid alignment, or neighboring content. Do not guess numeric values from a screenshot.

- Remove unnecessary fixed/minimum section heights at their source; let document flow size short informational sections.
- Use existing compact section-spacing tokens where the content does not justify a hero-sized treatment. Do not invent a global spacing reset.
- Keep a short heading and its explanation close enough to read as one group; avoid extreme column separation merely to fill the container.
- Merge duplicate sales bands when they add no new information or action. Preserve legitimate repeated access to the same CTA on long pages.
- If useful verified information is available, structure it as concise copy, a relevant list, specifications, or real imagery rather than manufacturing another card grid.
- Recheck mobile order, line lengths, zoom, focus, and the relationship between the section and footer. More density must not mean smaller text or smaller touch targets.

## Concentric corners - 14

```css
.preview-frame {
  --outer-radius: 20px;
  --frame-border: 1px;
  --frame-padding: 7px;
  border: var(--frame-border) solid var(--border);
  border-radius: var(--outer-radius);
  padding: var(--frame-padding);
}
.preview-frame__image {
  display: block;
  inline-size: 100%;
  block-size: auto;
  border-radius: max(0px, calc(
    var(--outer-radius) - var(--frame-border) - var(--frame-padding)
  ));
}
```

The child's radius is 12px: 20 - 1 - 7. This assumes uniform insets, circular radii, and an image touching the content-box edges. Do not apply the formula indiscriminately to buttons inside cards: they are not necessarily concentric surfaces.

## Icons and alignment - 12, 17

```html
<button type="button" aria-label="Close panel">
  <svg aria-hidden="true" focusable="false" viewBox="0 0 24 24">
    <path d="m6 6 12 12M18 6 6 18" fill="none"
          stroke="currentColor" stroke-width="2" />
  </svg>
</button>
```

Use the installed icon component instead of duplicating this SVG. With visible "Close panel" text, keep the icon decorative; a redundant `aria-label` is usually unnecessary. Apply optical adjustments to the drawing, not the clickable area.

## Anchor related content before optical adjustments - 08, 17

For an affected footer or multi-column section, reuse the existing container and breakpoint conventions. A grid with start-aligned groups and token-based gaps can establish structure; each group's label, values, and links should then form a local stack. Reset only accidental margins in that component, not all headings or paragraphs globally.

- Align comparable group headings deliberately; do not assume all differently sized elements share the same visual top or text baseline.
- Use `align-items: baseline` for text/icon relationships when appropriate, or local optical centering for an icon button. Do not use one alignment rule indiscriminately for both.
- Keep the contact number and its action icon in one meaningful row, with social links in the same contact group rather than separately positioned blocks.
- Preserve a readable phone number and target size. Structural alignment should not require equal font sizes, identical column widths, or surrounding boxes.
- Stack groups at the project's existing narrow breakpoint and verify DOM order, text wrapping, focus, and long addresses. Avoid absolute positioning or transforms as layout repairs.

## Align image frames, subjects, and captions separately - 06, 07, 17

Inspect the source assets first. For comparable catalog entries, reuse the existing media component and grid. A shared `aspect-ratio` reserves a common frame only when appropriate; it does not normalize the photographed subject automatically.

- Keep frame edges and gutters consistent through grid layout, not per-image transforms or arbitrary margins.
- For full-product views, consider `object-fit: contain` with an intentional background. For safely cropped lifestyle imagery, consider `cover` and verify the focal area per asset.
- Use `object-position` only when the crop needs adjustment; it cannot recover details already missing from a source image.
- Preserve width/height attributes or an appropriate reserved aspect ratio to avoid load-time shifts. Never stretch images to match a row.
- Keep captions in document flow with consistent local gaps. If the layout intentionally aligns wrapped titles/metadata, use the existing grid pattern; do not guess a universal fixed text height.
- Check the actual crops at narrow and wide sizes. When source photography cannot be reconciled honestly, request improved assets rather than hiding essential details.

## Asynchronous states - 18

Minimum contract to adapt without adding a state library:

| State | Interface | Behavior |
| --- | --- | --- |
| Idle | Specific enabled action | Awaits a real interaction |
| Pending | "Saving..." and a local indicator | Prevents duplicates; preserves content and focus |
| Success | Real confirmation, such as "Project saved" | Confirms only after a valid response |
| Error | Explanation and a retry path | Preserves input and restores the action |

Keep the status region outside the busy region so the waiting announcement itself is not deferred:

```html
<form id="project-form" aria-busy="false">
  <!-- Preserve the product's real fields and validation. -->
  <button type="submit">Save project</button>
</form>
<p id="save-status" role="status" aria-atomic="true"></p>
```

The real handler must prevent reentry, set busy, update status, run the existing operation, handle success/failure, and clear busy during finalization. Never simulate success with timers. If `aria-disabled` preserves focus, actually prevent activation: the attribute alone does not block events. Check the application's focus policy before choosing it over `disabled`.

For concurrent searches, cancel or discard stale responses according to existing patterns. Connect field errors with `aria-describedby` and `aria-invalid` where appropriate. Reserve assertive alerts for genuinely interruptive situations; never announce every progress frame.

## Feedback with reduced motion - 20

```css
.save-feedback {
  transition: opacity var(--duration-fast) var(--ease-standard);
}
@media (prefers-reduced-motion: reduce) {
  .save-feedback { transition: none; }
}
```

Apply reduction to components that actually animate, including skeletons and indicators. A static indicator with "Saving..." is still useful. For JavaScript animation, honor the same preference through the project's existing mechanism. Avoid global resets that break components depending on animation events.
