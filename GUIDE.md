# Practical guide

Create a visual foundation, review an existing interface, and verify improvements. Use this guide to choose checks, propose changes, and record the evidence.

[Scope and evidence](#scope-and-evidence) · [Colors and previews](#colors-and-previews) · [Review checklist](#review-checklist) · [Apps and workspace](#applications-and-personal-workspace) · [Report](#report) · [Review methods and references](#review-methods-and-references)

## Scope and evidence

Establish the task from the available context. Identify whether the target is a product being developed or the user's personal tools, then record the platform, requested coverage, material, and permitted changes. A palette, component, or single screen is a valid scope. The agent's host and open repository do not select the target.

| Available material | Useful review | What remains unproven |
| --- | --- | --- |
| Brief, logo, or a few colors | Palette directions and explicit candidate pairings. | Actual application uses and interaction. |
| Design values or tokens | Specified colors, typography, component states, and layout intent. | Rendered behavior and runtime accessibility. |
| Screenshot | Visible presentation and possible barriers. | Original color values, semantics, keyboard behavior, and other states. |
| Source repository | Shared causes, styles, markup, and existing checks. | Rendered outcomes unless the application can also be exercised. |
| Running page or application | Available rendered states, styles, interaction, and supported checks. | Unvisited screens, unavailable accounts, other environments, and unperformed manual tests. |
| Theme or appearance settings | Configured colors, text settings, and supported personal changes. | Effective rendering until observed, overrides, and behavior outside those settings. |

For an existing product, inventory the relevant page/screen and component families: navigation, content, forms, dialogs, tables, charts, and their variants. Include the themes the product actually offers and meaningful states such as focus, selected, expanded, validation error, loading, and empty. Inspect distinct implementations and backgrounds even when their colors have the same value. Record third-party embeds or canvas content that available tools cannot inspect.

A whole-product request deserves a coverage plan across the product. Sampling may be necessary; say what was sampled and why. A single URL defaults to that page and its safe reachable states, not unlimited domain crawling. Prefer representative complete journeys in an approved test environment, without triggering real transactions. [WCAG-EM](https://www.w3.org/TR/wcag-em-2/) provides useful evaluation methodology; a sample is not proof about everything outside it.

Record the date, target revision or URL, application/OS versions where relevant, viewport or window size, display/text scaling, theme, state, and tools actually used. Identify whether app evidence comes from a device, simulator, design, or supplied capture. Keep the playbook revision when available. Source inspection, manual browser checks, and automated results are different forms of evidence; do not present one as another. [WAI explains why automated tools cannot establish accessibility alone](https://www.w3.org/WAI/test-evaluate/tools/selecting/).

## Colors and previews

### Start small; inspect actual use when it exists

For a new proposal, start with a background, primary text, secondary text, an action/accent color, and its foreground. Add surfaces, focus, status colors, and other roles only as needed. Reuse existing names when working in a project. A palette-only request does not need a comprehensive token hierarchy.

For an existing interface, examine its uses within scope instead of stopping at swatches. Many elements can share a small set of styles. Group corrections where the shared source is demonstrated, while retaining exceptions for different backgrounds, themes, and states. Do not globally replace every occurrence of the same hex value.

Aesthetic coherence is a design recommendation. Contrast is a measurable property of a specific pairing. Do not require every color to contrast with every other color, or call an entire palette universally accessible.

### Measure the right thing

Use an available contrast checker or a reproducible calculation following the [WCAG definition](https://www.w3.org/TR/WCAG22/#dfn-contrast-ratio). Record the foreground, background, font size/weight when relevant, method, and result. Use unrounded values to decide against a threshold; rounded values are for display only.

For rendered checks, use resolved styles or effective theme values and establish the background, including relevant transparency and layering. A computed `background-color: transparent` is not a known white background. Gradients, images, blending, video, and overlapping layers need an appropriate check or a pending result. Do not infer precise WCAG results from anti-aliased screenshot pixels. See [text contrast guidance](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html).

For CSS color spaces beyond sRGB, use a checker that supports the actual values or a documented conversion/fallback; preserve the color space and method. Do not treat OKLCH lightness as WCAG relative luminance. Check the actual exported values, not just an earlier candidate. A simulation of color-vision differences is a useful illustration, not a pass/fail certification.

### Work with the brand

Keep locked logos and brand assets unchanged. Derive functional variants or change a foreground/background combination where needed. Text in a logotype has a specific text-contrast exception; ordinary UI text does not inherit it by using a brand color. Do not treat every decorative border as a required control boundary. Apply the criterion's actual scope and exceptions.

When locked choices cannot satisfy an intended use, explain the conflict and show the smallest viable alternatives. Do not silently relax a threshold. Approval selects the design direction; measurement verifies the relevant pairing.

### Preview brief

Show one recommended direction and up to two alternatives when they offer a meaningful choice. Use the existing design tool, component environment, browser, or target application. When file creation is available, a small local HTML preview can show the proposal alongside the report. Label a mockup as such; it does not verify rendering in the target application.

Show swatches **and** representative content: a paragraph, secondary text, link, primary button, field with an error, and a card. For an existing product, favor its real components and text. For a personal editor or terminal theme, use the representative content in [Applications and personal workspace](#applications-and-personal-workspace). Include focus and other affected states, and existing themes where relevant. Keep comparison content and dimensions consistent so the viewer is judging the colors rather than a redesign.

Provide before/after values, intended combinations, measured ratios, and a short explanation of the trade-off. Unmeasured pairs must be marked pending, not given estimated passing numbers. Expose technical detail below the visual decision. The preview itself needs semantic text, named controls, visible keyboard focus, zoom support, and labels that do not rely on color. Avoid remote scripts, trackers, and unnecessary external assets.

If rendering is unavailable, provide a palette table and an explicit preview brief, and say that no rendered preview was produced. After selection, use the target's existing style, token, or theme/settings format. Prefer [DTCG 2025.10](https://www.designtokens.org/tr/2025.10/format/) when a portable token exchange is needed, not as a required migration for every project.

### Starter example

A small light-theme starting point:

| Role | Value | Intended use |
| --- | --- | --- |
| Background | `#FFFFFF` | Page background and foreground on the action color. |
| Primary text | `#1F2937` | Body text on the background. |
| Secondary text | `#4B5563` | Supporting text on the background. |
| Action | `#1D4ED8` | Action background; also an underlined text link on the background. |

The following **opaque sRGB pairs only** were calculated using the WCAG relative-luminance formula. Display ratios are rounded; the passing decisions use the underlying values.

| Foreground / background | Contrast | Normal-text minimum of 4.5:1 |
| --- | --- | --- |
| `#1F2937` / `#FFFFFF` | 14.68:1 | Checked |
| `#4B5563` / `#FFFFFF` | 7.56:1 | Checked |
| `#FFFFFF` / `#1D4ED8` | 6.70:1 | Checked |
| `#1D4ED8` / `#FFFFFF` | 6.70:1 | Checked |

Focus, borders, other surfaces, hover/selected states, status colors, and dark themes still need design and verification when used. These numbers do not establish usability or whole-interface conformance.

A worked correction: normal-size text `#8A8A8A` on `#FFFFFF` measures **3.45:1**, below the 4.5:1 minimum. Changing that text to `#5F5F5F` yields **6.39:1** for this pair. This illustrates a candidate fix, not evidence that every use of a shared style has been rechecked.

## Review checklist

The technical baseline is selected **WCAG 2.2 A and AA** criteria, not a claim to cover every criterion. Linked Understanding documents explain the normative criteria; they are not extra requirements or the only valid implementation techniques. Record the exact criterion and any applicable exception for a confirmed failure.

For each relevant row, use an available check and retain evidence. With design-only inputs, review the specification where possible and leave runtime questions pending. HTML, ARIA, CSS pixels, and browser procedures below describe web content; for native interfaces, first follow [Applications and personal workspace](#applications-and-personal-workspace) to choose the appropriate interpretation and method.

### Color and reading

| Check | What to verify |
| --- | --- |
| **Text contrast — 1.4.3 AA** | Normal text at least **4.5:1**; large text at least **3:1**. Large means at least 18 pt (24 CSS px), or 14 pt bold (approximately 18.67 CSS px), with equivalent treatment for the relevant scripts. Check labels, placeholders, secondary text, and affected interactive states. Apply incidental/inactive and logotype exceptions only where they actually apply. [Source](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html). |
| **Non-text contrast — 1.4.11 AA** | Necessary visual information identifying controls, states, and graphics generally needs **3:1** against adjacent colors. Inactive controls, unmodified user-agent appearance, and essential presentations have specific exceptions. Decorative borders are not automatically required boundaries; non-adjacent normal/hover colors do not automatically need 3:1 against each other. [Source](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html). |
| **Not color alone — 1.4.1 A** | Errors, selected items, statuses, chart series, and instructions need another usable cue when color would otherwise be the only distinction. Prefer persistent underlines for inline links as a project recommendation, not a blanket claim that every non-underlined link fails WCAG. [Source](https://www.w3.org/WAI/WCAG22/Understanding/use-of-color.html). |
| **Text resizing — 1.4.4 AA** | Increase text to **200%**, with no loss of content or function, subject to the criterion's captions/images-of-text exceptions. Check controls and fixed-height containers, not just paragraphs. [Source](https://www.w3.org/WAI/WCAG22/Understanding/resize-text.html). |
| **Reflow — 1.4.10 AA** | At **320 CSS px wide** for vertically scrolling content, avoid two-dimensional scrolling and loss of content/function. The corresponding condition for horizontally scrolling content is **256 CSS px high**. Check zoomed layouts; apply the genuine two-dimensional-content exceptions, such as certain tables/maps, to those parts rather than the whole page. [Source](https://www.w3.org/WAI/WCAG22/Understanding/reflow.html). |
| **Text spacing — 1.4.12 AA** | Override line height to **1.5×** font size, paragraph spacing to **2×**, letter spacing to **0.12×**, and word spacing to **0.16×**, together, without loss of content/function. These are settings the interface must tolerate, not mandatory defaults. Apply the criterion to supported text/style technologies and relevant writing systems. [Source](https://www.w3.org/WAI/WCAG22/Understanding/text-spacing.html). |
| **Real text — 1.4.5 AA** | Prefer real text where the technology can provide the presentation; check customizable/essential exceptions, including logotypes. Do not turn readable content into an image merely to preserve a layout. [Source](https://www.w3.org/WAI/WCAG22/Understanding/images-of-text.html). |

### Interaction and supporting structure

| Check | What to verify |
| --- | --- |
| **Keyboard — 2.1.1 A; 2.1.2 A** | Exercise the selected journey without a pointer: equivalent functionality, no unintended keyboard traps, and usable entry/exit from dialogs. Follow platform key conventions. Inspect the exceptions for genuinely path-dependent input rather than assuming every mouse implementation is exempt. [Keyboard](https://www.w3.org/WAI/WCAG22/Understanding/keyboard.html), [traps](https://www.w3.org/WAI/WCAG22/Understanding/no-keyboard-trap.html). |
| **Visible focus — 2.4.7 AA; 1.4.11 AA** | Identify where keyboard focus is throughout the journey. Check author-defined indicators against applicable adjacent colors; do not remove the native outline without a working replacement. A screenshot of the initial screen cannot prove this. [Source](https://www.w3.org/WAI/WCAG22/Understanding/focus-visible.html). |
| **Unobscured focus — 2.4.11 AA** | Focused components must not be entirely hidden by author-created content. Check sticky navigation, banners, and overlays. Keeping them completely unobscured is a stronger recommendation; do not confuse the AA threshold with the AAA requirement. [Source](https://www.w3.org/WAI/WCAG22/Understanding/focus-not-obscured-minimum.html). |
| **Hover/focus content — 1.4.13 AA** | Additional content such as tooltips must meet the criterion's dismissibility, hoverability, and persistence conditions and exceptions. Test moving into it, dismissing it, and reaching the equivalent information with a keyboard. [Source](https://www.w3.org/WAI/WCAG22/Understanding/content-on-hover-or-focus.html). |
| **Targets and dragging — 2.5.8 AA; 2.5.7 AA** | Check targets against **24 × 24 CSS px**, or the exact spacing/equivalent/inline/user-agent/essential exceptions. Do not fail every inline text link. Dragging needs a single-pointer alternative unless an exception applies; keyboard support alone does not establish this. [Targets](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html), [dragging](https://www.w3.org/WAI/WCAG22/Understanding/dragging-movements.html). |
| **Structure and order — 1.3.1 A; 1.3.2 A; 2.4.1 A; 2.4.3 A** | Inspect headings, labels, table relationships, reading/focus order, and ways to bypass repeated blocks. Compare the DOM/accessibility tree with the visual presentation. A heading's visual size does not establish its semantic level. [Relationships](https://www.w3.org/WAI/WCAG22/Understanding/info-and-relationships.html), [sequence](https://www.w3.org/WAI/WCAG22/Understanding/meaningful-sequence.html), [bypass](https://www.w3.org/WAI/WCAG22/Understanding/bypass-blocks.html), [focus order](https://www.w3.org/WAI/WCAG22/Understanding/focus-order.html). |
| **Image alternatives — 1.1.1 A** | Identify the image's role in context. Decorative images may need empty alternatives; functional images need their purpose; informative images need equivalent information. Complex graphics may need a summary and an accessible table or longer explanation. Do not invent unseen content or treat the mere presence of `alt` as sufficient. [Decision tree](https://www.w3.org/WAI/tutorials/images/decision-tree/). |
| **Forms, names, and feedback — 3.3.1 A; 3.3.2 A; 2.5.3 A; 4.1.2 A; 4.1.3 AA** | Check labels/instructions, useful text errors, accessible names that include visible labels where required, exposed roles/states, and programmatically available status messages. A placeholder is not a persistent label. Prefer native controls over added ARIA; verify announcements with available assistive technology rather than assuming a DOM attribute proves the experience. [Labels](https://www.w3.org/WAI/tutorials/forms/labels/), [label in name](https://www.w3.org/WAI/WCAG22/Understanding/label-in-name.html), [errors](https://www.w3.org/WAI/WCAG22/Understanding/error-identification.html), [status](https://www.w3.org/WAI/WCAG22/Understanding/status-messages.html), [ARIA guidance](https://www.w3.org/WAI/ARIA/apg/practices/read-me-first/). |
| **Movement and flashing — 2.2.2 A; 2.3.1 A** | Check pause/stop/hide controls for applicable moving or updating content. Review flashes using the actual frequency/area/luminance conditions, not a casual visual guess or a blanket ban on animation. Do not expose someone to suspected hazardous flashing just to test it. [Movement](https://www.w3.org/WAI/WCAG22/Understanding/pause-stop-hide.html), [flashes](https://www.w3.org/WAI/WCAG22/Understanding/three-flashes-or-below-threshold.html). |

### Useful improvements beyond the baseline

These are **project recommendations**, not automatic AA failures. Evaluate them when relevant, state their basis, and do not force a redesign or extra feature without a user benefit.

| Recommendation | How to use it |
| --- | --- |
| **Respect display and motion preferences** | Test relevant `prefers-reduced-motion`, `prefers-contrast`, and `forced-colors` behavior in the supported environment. Preserve useful borders/focus and system colors; do not globally opt out with `forced-color-adjust: none`. Test existing light/dark themes, but do not report the absence of dark mode as an AA failure. [Media Queries Level 5](https://www.w3.org/TR/mediaqueries-5/), [CSS Color Adjustment](https://www.w3.org/TR/css-color-adjust-1/). |
| **Comfortable typography and stronger focus** | Review thin strokes, dense copy, and readability in actual fonts. Prefer a generous focus treatment. **2.4.13 Focus Appearance is AAA**, not AA; its area and contrast conditions are not simply a universal two-pixel-outline rule. Do not declare a WCAG failure solely because text is below 16 px. [Focus appearance](https://www.w3.org/WAI/WCAG22/Understanding/focus-appearance.html). |
| **Allow user color overrides** | Check that user-chosen text/background colors do not hide content or functionality. A built-in theme editor is not necessarily needed; platform or user-agent overrides can provide the adjustment. Inspired by the WCAG 3 draft's text-color-adjustable provision. [Dated draft](https://www.w3.org/TR/2026/WD-wcag-3.0-20260303/). |
| **Do not degrade the pointer or rely on depth alone** | Prefer the platform pointer; where customized, verify that it remains findable and usable. Add an additional cue when visual depth is the only indication of meaning. These are useful ideas from the same WCAG 3 draft, not final WCAG 3 conformance tests. [Dated draft](https://www.w3.org/TR/2026/WD-wcag-3.0-20260303/). |

WCAG 3 remains work in progress at the source review below. Do not market a WCAG 3 score, silently substitute APCA for WCAG 2.x contrast, or promote a draft suggestion to a release-blocking rule. New ideas belong here when they have a clear benefit, primary evidence, and a practical check.

## Applications and personal workspace

### Match the review to the target

For a **product interface**, inspect the design, code, or running app within scope. For a **personal workspace**, inspect the user's editor, terminal, or other application's supported appearance settings. Keep personal preferences separate from product-source changes and shared project settings.

Apply the common visual checks to desktop and mobile apps using [WCAG2ICT](https://www.w3.org/TR/wcag2ict/), an informative interpretation of WCAG for non-web software, and relevant official platform guidance. Use browser inspection for web content and platform accessibility inspection for native controls. Do not require a DOM or ARIA from a native interface. For sizing and scaling, document the platform's units and their relationship to the criterion rather than equating screenshot pixels with CSS pixels. Record which interpretation was used; runtime and assistive-technology checks remain pending until performed.

A phone connection is optional. With supplied mobile screenshots, designs, or settings, offer a limited visual review and supported adjustment instructions. Check original color values when available; do not invent precise ratios from a capture. With authorized access to source, a simulator, or a device, extend the review to available states. Identify the evidence used, and keep untested touch, scaling, focus, and assistive-technology behavior pending. Connecting devices or changing system-wide settings requires separate authorization.

### Personal themes and appearance

Identify the application and version, active theme/profile, affected surfaces, and available settings. Consult the installed setting definitions or official documentation before proposing keys or file paths. Start from the current theme and use a small set of shared colors where possible.

| Area | Check in representative use |
| --- | --- |
| **Code and text** | Read body text, comments, strings, keywords, and inline suggestions on their actual backgrounds. Keep secondary content readable. Check semantic highlighting or language-specific overrides when present. |
| **Selection and navigation** | Inspect selected text, search matches, active lines, caret, keyboard focus, and completion menus. Recheck text contrast on highlighted backgrounds. |
| **Diffs and diagnostics** | Keep additions, deletions, errors, warnings, and conflicts understandable through text, symbols, or structure as well as color. Verify the text within each highlighted area. |
| **Panels and terminal** | Check tabs, sidebars, labels, messages, and terminal output, including standard/bright colors, selection, and cursor where supported. Inspect each surface rather than assuming it inherits the editor palette. |
| **Typography and scale** | Compare interface and code sizes, spacing, weight, and distinguishable characters such as `0/O` and `1/l/I`. Try supported scaling without clipping content. Treat comfort preferences separately from measured barriers. |

For example, VS Code distinguishes interface, syntax, and semantic [theme customization](https://code.visualstudio.com/docs/configure/themes), documents [terminal appearance](https://code.visualstudio.com/docs/terminal/appearance) separately, and supports different [user, workspace, and profile settings](https://code.visualstudio.com/docs/configure/settings). Verify equivalent capabilities in the actual target instead of assuming matching keys across editors.

### Preview, apply, and restore

Show a representative code sample, diff, messages, and terminal output where relevant. Keep content and layout consistent between before/after variants. Use the existing preview workflow; a labeled local mockup can support a choice but is not proof of the application's rendering.

Deliver the important changes and exact supported setting values, a theme fragment, or short UI instructions. Prefer personal settings or a dedicated profile; explain the affected scope and any known synchronization effects. Record old values, including whether a setting was absent, and a restoration method before applying approved changes. Preserve unrelated entries and file conventions instead of replacing an entire preferences file. Do not alter shared project settings unless explicitly included.

Verify the effective result after application, including relevant overrides. User acceptance of a preview is not verification. When a visual barrier is confirmed but cannot be changed through supported settings, keep it as a finding with that limitation, rather than marking it fixed or hiding it. This review covers the inspected appearance and behavior, not the whole app or operating system.

## Report

Produce one report with the action plan inside it. Use the user's language. Keep a compact summary first and the evidence below it, using expandable sections only when the renderer supports them.

Use **✓ Checked**, **✕ Fix**, and **? Pending**, with explicit text rather than color alone. Checked applies to the named check and state, not the product. Fix requires evidence. Pending means untested or inconclusive, with a reason and next step. Keep justified non-applicability out of the headline result. A mixed finding group is not fixed while any confirmed failure remains.

Suggested structure; omit empty sections rather than manufacturing findings:

```text
# Accessibility review — [target]
Scope: [target/platform, material, screens/journeys, size/scaling, theme, state, version/date]

## Changes that matter
1. [Outcome for users] — [shared cause, affected areas, proposed change]
   Verify: [concrete check and expected outcome]

## Your decision
[Only meaningful design choices or decisions requiring new authorization]

## Pending
[Unavailable or inconclusive check → reason → next action]

## Evidence
[Finding ID; location/state; observed vs expected; source/basis;
 method and result; confirmed cause or hypothesis; linked evidence]

## After changes
[Rechecked fixes, remaining failures, new issues, and changed coverage]
```

Lead with roughly three to five substantial changes when that is useful; it is not a quota or a cap. Include all material blockers. Prioritize blocked journeys and hard-to-perceive essential content over cosmetic refinements or raw finding counts. Keep smaller independent issues in the detail. Never imply that fixing the summary necessarily resolves every finding.

Maintain compact coverage in the detail: each applicable checklist area should have evidence or a pending reason. Distinguish a check that could not run from one that ran inconclusively, even though both appear as Pending. For numerical findings retain actual values; for interaction findings retain the reproduction steps. Attribute a file or shared token only when inspected. Keep original check identifiers and tool versions with recorded results.

After changes, rerun the same relevant checks on affected variants, not merely the initial screenshot. Preserve the original scope, or explicitly explain a change. Record regressions, new failures, and remaining manual checks. If a change cannot be rechecked, it remains pending verification. Use an existing regression test where it adds value; do not add dozens of superficial assertions or a new testing framework by default.

## Review methods and references

### Review methods

Inspect rendered presentation and semantics with the browser or platform accessibility tools appropriate to the target. Exercise selected journeys using the relevant input methods and available assistive technology. Compare design, source, or theme values with the effective result. Use the appearance controls and inspection capabilities actually exposed by the application.

Reuse relevant checks and test journeys already available in the project. Record the method, version, scope, and original results. A check that returns insufficient evidence remains pending.

For colors, compare known foreground/background values with a suitable checker or an executed calculation using the WCAG formula. Verify exported values and their intended uses. Explore visual alternatives in the project's design environment or a local preview.

When assistive-technology testing is available, record what was actually exercised. Include feedback from people who use it. Source inspection and accessibility-tree inspection support the review but cannot substitute for an unperformed interaction test.

### Primary references and maintenance

Source review: **2026-09-07**. Record the guide revision used for a review when available.

[WCAG 2.2](https://www.w3.org/TR/WCAG22/) supplies the technical criteria referenced in the checklist. [WAI tutorials](https://www.w3.org/WAI/tutorials/) and the linked Understanding documents explain practical application. [WCAG-EM 2.0](https://www.w3.org/TR/wcag-em-2/) informs scope and evidence. [WCAG2ICT](https://www.w3.org/TR/wcag2ict/) helps interpret accessibility concepts outside the web; native applications also require platform-specific evaluation. The [applications and personal workspace](#applications-and-personal-workspace) section links the official editor references used for its examples. [WCAG 3's March 2026 draft](https://www.w3.org/TR/2026/WD-wcag-3.0-20260303/) informs the explicitly provisional recommendations above. [DTCG 2025.10](https://www.designtokens.org/tr/2025.10/format/) defines a portable token exchange format.

Verify primary sources when updating guidance or resolving material ambiguity. Record changed recommendations in the commit and identify their basis as a published criterion, a project recommendation, or a draft idea.
