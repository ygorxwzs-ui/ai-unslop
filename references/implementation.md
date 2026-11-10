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
