# Visual needs and functional adjustments

Use this reference to connect a visual difficulty to independent adjustments and a realistic verification task. Use [GUIDE.md](../GUIDE.md) for technical criteria and exceptions; this reference does not add WCAG requirements or clinical tests.

## Contents

- [Start with the task](#start-with-the-task)
- [Map needs to adjustments](#map-needs-to-adjustments)
- [Choose the route and layer](#choose-the-route-and-layer)
- [Offer usable controls](#offer-usable-controls)
- [Verify and preserve recovery](#verify-and-preserve-recovery)
- [Sources and interpretation](#sources-and-interpretation)

## Start with the task

Establish what the person needs to read, find, distinguish, or operate. Use existing context before asking questions. Ask about a difficulty only when the answer would materially change the proposal; do not require a diagnosis or medical history. For a general product, use representative visual needs as evaluation scenarios instead of assuming one user's preferences describe everyone.

Record the device, usual viewing distance, lighting, relevant applications, existing adjustments, and a representative task. Check a phone and a monitor at their usual distances: identical pixel values or screenshots do not establish equivalent readability. Do not infer a condition from a theme preference, halo complaint, or need for larger text.

Distinguish three outcomes: technical accessibility, functional usefulness, and aesthetic preference. A report that text becomes uncomfortable after sustained reading is functional evidence even though it is subjective. “I prefer this palette's appearance” is a design preference. Neither alone establishes a WCAG failure or pass. [WAI's visual barriers][visual] explain why size, color, brightness, and field of view require different adaptations.

## Map needs to adjustments

Treat these as candidate adjustments, not prescriptions. Combine them only when useful; leave unrelated settings unchanged. Validate with the actual user when individual usefulness is the objective.

| Functional difficulty | Independent adjustments to consider | Representative verification | Limitations and trade-offs |
| --- | --- | --- | --- |
| **Small detail or unclear characters** | Text size, stroke weight, familiar font, text/display scaling, zoom, spacing. | Read real labels, figures, and easily confused characters; enlarge content and complete the same task. | More enlargement leaves less context visible. Check clipping and [reflow][reflow]; a larger screenshot is not a device test. |
| **Text or controls merge into the background** | Foreground/background contrast, stronger strokes, opaque surfaces, local contrast for essential states. | Read secondary text and identify inputs, errors, selection, and focus on each actual surface. | A measured [contrast ratio][contrast] is pairing-specific. Passing it does not prove comfort, and overall brightness is a separate variable. |
| **Bright surfaces, polarity, or reported halos interfere with reading** | Display brightness, light/dark polarity, background/text colors, and surface intensity, separately. | Compare the same passage and controls in ordinary lighting; ask about legibility and discomfort, including when switching apps. | No universal dark/light prescription. Do not diagnose halos or promise to remove them. Preserve readable text when reducing luminance. [Needs guidance][needs]. |
| **Colors or states are difficult to distinguish** | Labels, symbols, patterns, direct chart labels, and distinguishable palettes; supported personal filters when useful. | Identify success/error, chart series, changes, and selected items without guessing from hue. | [Color-independent meaning][color] remains necessary. Filters can alter images; simulations illustrate differences but cannot certify a person's experience. |
| **Control boundaries or groups are unclear** | Selective borders, solid fills, spacing, headings, explicit selected states, reduced transparency. | Locate a field, its label, a primary action, and the group each belongs to. | Keep borders separate from brightness and text contrast. Outlining everything can create clutter; [grouping guidance][grouping] supports several alternatives. |
| **Cursor, focus, reading position, or nearby information is lost** | Findable pointer/caret, visible focus, stable layout, related information kept nearby, magnification and reading layout. | Switch windows, find the insertion point, zoom, resume reading, and notice feedback associated with an action. | Enlarging content can worsen orientation when only a small area is visible. A notification elsewhere on screen is not necessarily noticed. [Visual barriers][visual]. |
| **Motion or temporal changes are difficult to tolerate** | Reduced nonessential motion, pause controls, stable transitions, and supported cursor-blink settings. | Exercise navigation with motion reduced; verify that changes of state remain understandable. | Separate animation, content flashes, and panel flicker. Never expose someone to suspected hazardous flashing to test tolerance. [Motion guidance][motion]. |
| **Effort builds during sustained work** | Revisit size, spacing, density, glare, polarity, interruptions, and task presentation; consider supported reading assistance. | Repeat a representative work period voluntarily; record completion, errors, effort, and discomfort before and after. | A short preview cannot prove sustained benefit. Do not label a visual adjustment a treatment or assume all symptoms originate in interface design. |

## Choose the route and layer

**For developers**, establish a readable, operable default and compatibility with platform adjustments. Essential labels, visible states, and usable scaling belong in the base interface. Offer advanced personalization when it adds value; it must not be the only way to repair known default barriers. Follow [personalization guidance](personalization.md) for optional controls and preference behavior.

**For a person's environment**, adapt supported settings across the relevant layers. Prefer the narrowest effective scope, while checking interactions with other layers. Do not assume a browser change affects native apps or an OS setting reaches every application.

| Layer | Inspect and consider | Establish before applying |
| --- | --- | --- |
| **Screen and surroundings** | Usual distance, reflections, ambient light, supported brightness controls, display arrangement. | Device and display actually used; what is observed, user-reported, or measured. A screenshot cannot measure physical luminance, glare, or panel flicker. |
| **Operating system** | Text/display scaling, pointer/caret, magnification, contrast/color options, motion and transparency. | OS version, supported settings, affected displays/apps, and prior values. Check manufacturer documentation. |
| **Browser** | Page zoom, text sizing, reading presentation, color preferences and existing extensions. | Browser/version, page versus browser-interface scope, site exceptions, and policy restrictions. |
| **Application or content** | Theme, typography, surfaces, controls and states; product code only when included. | Application/version, effective overrides, and whether settings are personal, shared, or synchronized. |

Consult official documentation before naming setting keys, file paths, or UI steps. Platform examples include [Windows visual adjustments][windows], [Mac display accessibility][apple], and [Android accessibility principles][android]. These are starting points, not interchangeable configuration recipes.

## Offer usable controls

If initial guidance helps, offer a few choices linked to the stated difficulty, then make individual controls directly available. Do not trap users in a diagnostic quiz or require repeated onboarding to adjust a value. Use descriptive labels such as “larger text” or “clearer control boundaries”; avoid disease-named presets that imply one configuration suits everyone with that condition.

Keep size, polarity, text contrast, border strength, transparency, and motion separable where supported. Respect relevant system/browser preferences and document conflicts; [CSS preference signals][preferences] indicate requested presentation, not diagnoses. Check implementation support rather than assuming every signal exists on every platform.

The adjustment interface must remain readable and operable with zoom, keyboard, touch, and relevant assistive technology. Show current values, understandable effects, and an accessible reset. Provide a practical fallback when a requested adjustment is unsupported.

## Verify and preserve recovery

Compare the same content and task under comparable conditions. Record technical results separately from reported usefulness; do not mark personal benefit verified when only an agent has inspected a preview. Use [evaluation scenarios](evaluations.md) to test the workflow without claiming medical efficacy.

Before changing settings, retain previous values, including absence or inheritance, and a restoration route. Verify effective behavior after applying changes, including overrides and synchronization. Keep reset reachable if the proposed appearance becomes hard to use.

Use authorization already provided for the requested work. Ask only when a material extension, shared configuration, or other unapproved action requires it. If access is unavailable, provide verified instructions and state what remains untested. A limitation is not a successful adjustment.

## Sources and interpretation

Sources reviewed **2026-11-23**. The matrix is practical synthesis, not a validated clinical scale. W3C's low-vision-needs document is **work in progress**, not a normative standard; its functional distinctions inform the proposals. WAI supplemental patterns and platform guidance are recommendations. Apply the published criteria and exceptions in the main guide when reporting WCAG results. For educational prevalence and its limits, see [Visual evidence](visual-evidence.md).

[visual]: https://www.w3.org/WAI/people-use-web/abilities-barriers/visual/
[needs]: https://www.w3.org/TR/low-vision-needs/
[reflow]: https://www.w3.org/WAI/WCAG22/Understanding/reflow.html
[contrast]: https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html
[color]: https://www.w3.org/WAI/WCAG22/Understanding/use-of-color.html
[grouping]: https://www.w3.org/WAI/WCAG2/supplemental/patterns/o2p03-page-structure/
[motion]: https://www.w3.org/WAI/WCAG22/Understanding/animation-from-interactions.html
[preferences]: https://www.w3.org/TR/mediaqueries-5/
[windows]: https://support.microsoft.com/en-us/accessibility/windows/make-windows-easier-to-see
[apple]: https://support.apple.com/guide/mac-help/unac089/mac
[android]: https://developer.android.com/guide/topics/ui/accessibility/principles
