# Sources, research, and limits

Research conducted on November 9, 2026. These links identify specifications or supporting foundations. Examples and recommendations are original syntheses, not direct quotations or universal guarantees of results.

## Primary and specialist sources

| ID | Source | Application |
| --- | --- | --- |
| S1 | [W3C - WCAG 2.2](https://www.w3.org/TR/WCAG22/) | Semantics, color, reflow, focus, targets, status; distinguish A, AA, and AAA. |
| S2 | [W3C - Contrast Minimum](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html) | Normal/large text, backgrounds, exceptions, and contrast ratios. |
| S3 | [W3C - Non-text Contrast](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html) | Necessary parts of controls and graphics. |
| S4 | [Nielsen Norman Group - Proximity Principle](https://www.nngroup.com/articles/gestalt-proximity/) | Grouping by distance and preserving mobile relationships. |
| S5 | [Nielsen Norman Group - Layer-Cake Pattern](https://www.nngroup.com/articles/layer-cake-pattern-scanning/) | Descriptive headings and hierarchy for scanning. |
| S6 | [Nielsen Norman Group - Memorable Imagery](https://www.nngroup.com/articles/7-tips-memorable-imagery/) | Concrete visuals, product context, and visual competition. |
| S7 | [MDN - text-wrap](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/text-wrap) | Balanced headings, fallback, and browser limitations. |
| S8 | [W3C - Status Messages](https://www.w3.org/WAI/WCAG22/Understanding/status-messages.html) | Announcing waiting, success, and failure without stealing focus; avoiding excessive announcements. |
| S9 | [GOV.UK - Text input](https://design-system.service.gov.uk/components/text-input/) | Visible labels, hints, and field associations. |
| S10 | [Material - Typography](https://m3.material.io/styles/typography/overview) | Type roles, tokens, and consistency; not copying visual identity. |
| S11 | [Material - Applying icons](https://m3.material.io/styles/icons/applying-icons) | Families, optical weight, sizes, text, and localization. |
| S12 | [MDN - prefers-reduced-motion](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-motion) | Reducing, removing, or replacing nonessential motion. |
| S13 | [W3C - CSS Backgrounds and Borders, corner shaping](https://www.w3.org/TR/css-backgrounds-3/#corner-shaping) | Radius geometry, borders, and corner behavior. |

Supplements: [GOV.UK - Button](https://design-system.service.gov.uk/components/button/) for action wording and hierarchy; [MDN - font-variant-numeric](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/font-variant-numeric) for tabular numerals; [OpenCode V2 - Skills](https://opencode.ai/v2/docs/skills) for installation and discovery.

## Standards versus judgment

Selection supplement: [MDN - ::selection](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/::selection) documents highlight styling, supported properties, inheritance, accessibility considerations, and browser limitations. Native highlight shape is not itself evidence of a layout defect.

- **Standards:** applicable WCAG criteria and specified technology behavior. Understanding pages explain the standard; normative wording lives in the WCAG recommendation.
- **Supported heuristics:** proximity, clear headings, product prioritization, and consistent iconography. Apply according to task, content, and brand; studies do not prove every interface will respond identically.
- **Editorial synthesis:** removing empty badges, repeated labels, arbitrary italics/mono, and using accent/decorative effects intentionally. These are not style prohibitions or WCAG requirements.
- **Geometric derivation:** inner radius equals outer radius minus inset for uniform concentric cases. The specification explains CSS corners, not a universal formula for every nested component.
- **Examples:** recipe values, classes, and copy are illustrative, not approved tokens, real measurements, or code tested in a user's product.

## Updates

Check primary sources before changing thresholds, CSS features, or accessibility recommendations. Never update numbers from a blog or search snippet alone. Confirm compatibility against the project's supported browsers. Record relevant changes in README; do not require research dependencies for normal skill use.
