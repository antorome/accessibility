# Implement visual personalization

Use this reference when building or reviewing visual settings, a guided configurator, an application extension, or a personal theme tool. Read [Visual needs](visual-needs.md) first and use [GUIDE.md](../GUIDE.md) for the applicable technical checks. These are implementation recommendations and acceptance criteria for the requested feature, not a claim that every product must ship a settings wizard.

## Contents

- [Start with the current host](#start-with-the-current-host)
- [Keep needs and controls distinct](#keep-needs-and-controls-distinct)
- [Build an accessible configuration flow](#build-an-accessible-configuration-flow)
- [Make previews faithful](#make-previews-faithful)
- [Apply settings through supported contracts](#apply-settings-through-supported-contracts)
- [Handle motion and system preferences](#handle-motion-and-system-preferences)
- [Persist and restore deliberately](#persist-and-restore-deliberately)
- [Verify the feature and its benefit](#verify-the-feature-and-its-benefit)
- [Sources and status](#sources-and-status)

## Start with the current host

1. Record the installed application and extension versions or commits. Inspect project instructions, extension discovery, SDK exports, styling contracts, components, preference storage, and available tests. The current checkout and running build determine behavior; historical paths and review findings are leads to verify.
2. Establish whether the framework, dialog/popover library, style engine, or host preference API changed. Do not translate an old hook mechanically or retain selectors for a library no longer used.
3. Inventory the host's native capabilities and defaults before adding overrides. Adopt a supported host setting that already resolves the need. Verify and then remove redundant workarounds; retain a documented fallback only for supported older versions that still need it.
4. Map needs to capabilities. For each control, record what changes, supported values, scope, precedence, application method, limitations, and a verification task. Keep unsupported needs visible. Do not imitate a display-brightness control with an unlabeled contrast or color change.

Use a compact record, not a new settings framework unless the project needs one:

| Field | Example of useful information |
| --- | --- |
| Need and task | Distinguish a failed run from a completed run in the activity list. |
| Adjustment | Persistent status label and distinct icon; optional palette choice. |
| Capability and ownership | Host status component; extension supplies supported preference. |
| Scope and state | Browser profile, app origin, and all applicable list variants. |
| Validation and restoration | Identify each state with color unavailable; disabling restores only owned settings. |

## Keep needs and controls distinct

Provide a manageable set of relevant controls, with progressive detail. Separate controls when their effects solve different needs:

- **Text size and overall scale:** describe whether text alone or the entire interface grows. Treat density, spacing, and font weight separately where supported. Expose a route when the offered range is insufficient and preserve browser/OS magnification.
- **Polarity and luminous surfaces:** offer descriptive light/dark variants, with deliberate button, field, popup, and editor surfaces. Avoid claims such as “no glare,” “eye protection,” or a disease-specific optimum that the feature cannot establish.
- **Text contrast and boundaries:** make readable secondary content part of the baseline. Stronger control boundaries, region separation, and focus indicators should not require brighter text or a different hue palette.
- **Status and color differentiation:** provide usable text, shape, or structural redundancy in the default experience when needed. Optional stronger indicators should be available with either palette, rather than reserved for a “color-blind mode.” A blue/orange pair is not universally suitable for every color-vision difference or context.
- **Motion and transparency:** use separate effective preferences where relevant. Reduced motion must not suppress essential progress, completion, or error information.

Do not assign settings from a diagnosis or prevalence statistic. Do not force every possible control into a simple product. Document intentional coupling when the host cannot separate dimensions, and test the consequence. Presets may be convenient starting points; they are not clinical classifications.

## Build an accessible configuration flow

An optional initial guide can help a person explore adjustments; provide direct access for later changes. Start from existing preferences and a short functional difficulty, without requiring health data. Use the person's usual comfortable viewing conditions; keep them reasonably consistent during a comparison rather than prescribing a universal distance.

Keep the configurator itself readable before configuration: use native controls, clear labels, sufficient target size, visible focus, working zoom, and a reachable cancel/reset path. Verify opening, step changes, Escape where appropriate, closing, and logical return of focus with the actual component library. Do not infer those behaviors from a label or an accessibility attribute alone.

Use the host's supported accessible component kit when it has additional interaction contracts, such as agent-visible controls or action attribution. Preserve human semantics and keyboard behavior, and verify the host's automation bridge when supported; do not replace those contracts with look-alike elements or invented ARIA.

Offer “no useful difference,” “none is comfortable/legible,” or a route to more adjustment. A preselected radio and a Next button do not establish that the user tested the choice. Describe the feature as guided adjustment, not a visual-acuity, color-vision, or medical test.

Where supported, provide a reversible trial in the actual application with clear Apply, Cancel, and Restore actions. Keep a recovery command reachable without reading the affected content. Do not impose a short timeout that itself prevents completion; choose recovery behavior appropriate to the change and target. Check that draft changes, dismissal, and reopening have defined behavior.

## Make previews faithful

Each candidate must represent its own settings independently of the currently active profile. A candidate should resolve identically when opened from any other profile, or when personalization is off. Isolate its variables and rules; global selectors and `!important` must not leak into the candidate. Prefer existing components within a scoped preview, or clearly label a mockup and check its parity with the real application.

Show the states the control actually changes: primary and secondary text, code comments, numbers, a field and error, buttons, focus, text selection, navigation selection, status indicators, and added/deleted content where relevant. Use genuine status shapes and labels. A border around a sample card does not demonstrate the visibility of input boundaries.

Hold content, position, and size comparable when testing a dimension. For luminance/polarity comfort, allow a sequential whole-surface comparison; a small dark card next to a large light area does not reproduce a dark workspace. Make the configurator's own buttons and surfaces honor the chosen policy.

Do not promise a sample's “real size” without checking nested scale, browser zoom, portals, and the actual font. If a comparison becomes clipped at a narrow width, adapt its layout instead of hiding the content being evaluated.

## Apply settings through supported contracts

Use semantic tokens, supported settings, stable component attributes, and public APIs. Avoid recognizing a component's role from a particular color, utility class, incidental DOM shape, or an unbounded selector such as every `[data-status]`. A host may put that attribute on a whole row as well as a small indicator.

If a fallback selector is unavoidable, bound it to the intended component and documented host versions; test both intended matches and unrelated elements that must remain unchanged. In particular, `[style*='color: rgb(...)']` also matches `background-color: rgb(...)`. Treating those as the same property can produce identical text and background. Prefer semantic variables or hooks over increasingly fragile string matching.

Check resolved styles, including inline values, cascade layers, specificity, `!important`, and actual class names. A variant class such as `dark:text-warning` is not the class `text-warning`. Adding selector specificity does not overcome a different cascade-layer priority. A token table alone does not establish which declaration wins.

Put preference application and synchronization in a lifecycle that remains active on every supported surface. Do not attach essential behavior only to a status button, optional panel, collapsed menu, or desktop-only component. Use the current framework's lifecycle and disposal APIs. Inspect the host's actual behavior for enable/disable, remount, live update, full reload, and removal instead of assuming they are equivalent.

Scaling must work for the whole affected layout: main surface, dialogs, popovers, tooltips, editors, fixed/sticky regions, mobile keyboards, and safe areas. Prefer supported host typography/scale settings. A CSS `zoom` fallback is an overall-scale change, not text-only resizing; verify geometry and positioning. Neither a small built-in maximum nor changing units to `rem` alone proves a WCAG pass or failure.

## Handle motion and system preferences

Define one effective source of truth and explicit precedence between supported OS/browser preferences, persisted user choices, and temporary trials. Respect platform-enforced modes such as forced colors; manual app choices must not silently break them. Explain whether “system” follows later preference changes.

Wire reduced motion to CSS animations/transitions and relevant JavaScript behavior, including Web Animations API, smooth scrolling, and animated canvas content where used. `animation: none` does not cancel an independently created `Element.animate()` animation. Avoid blanket cancellation that strands loading states or hides completion feedback.

Check relevant `prefers-color-scheme`, `prefers-contrast`, `prefers-reduced-motion`, `prefers-reduced-transparency`, and `forced-colors` behavior in the actual support matrix. Do not assume every browser exposes every preference. Keep forced-color focus, status, selected states, and control boundaries perceivable when shadows/backgrounds are replaced. Avoid a global `forced-color-adjust: none` workaround.

## Persist and restore deliberately

- State the scope accurately: for example, local storage belongs to an origin and browser profile, not a physical monitor or automatically to an account. Define cross-tab synchronization and per-device behavior if offered.
- Validate stored values with explicit allowed values or own-property checks; do not accept inherited object keys as enum members. Define sensible behavior for old versions, missing values, unavailable storage, and unsupported capabilities.
- Save the prior state once before taking ownership, including whether a setting was absent. Separate draft, applied, and disabled states; do not overwrite the restoration snapshot on every adjustment.
- Define what happens if another control changes a shared preference while the tool is active. Restore only the settings the feature owns, without overwriting unrelated or intervening user changes.
- Test Apply, Cancel, Off, reload, disable, and removal separately where the host supports them. If removal cannot run cleanup, document the recovery path; do not promise exact automatic restoration for a lifecycle the host does not expose.
- Preserve existing saved preferences through migration. Avoid collecting diagnostic labels or health information when functional settings suffice.

## Verify the feature and its benefit

Use a small set of meaningful tests aimed at actual risks. Reuse the project's test tools. Keep these results separate:

| Evidence | What it supports | What it does not establish |
| --- | --- | --- |
| Executed token calculations | The named pairs and operations satisfy the tested contrast thresholds. | Actual component styling, every state, or whole-product conformance. |
| Rendered/integration checks | Settings reach the named components and journeys on the tested host. | Every platform, assistive technology, or individual's comfort. |
| User task and comfort trial | The reported result for that person and context. | Clinical diagnosis or sustained benefit not observed. |

Minimum coverage for a feature of this kind:

1. Check the default experience with the feature off and recovery available. Do not count advanced settings as fixes for unrelated baseline failures.
2. Check each offered palette's intended pairs and all supported high-risk interactions. Use actual blending/color spaces. Exercise preview isolation across prior profiles, and inspect rendered foreground/background pairs after overrides.
3. Exercise representative tasks: read a comment or number, find a control, identify a failed/waiting/completed state, distinguish a diff, and recover the focus or caret. Adapt these tasks to the target rather than forcing a code sample into every product.
4. Test relevant text resizing, narrow/reflow layouts, application scale plus browser zoom, and overlays. Reach both the start and actions of the configurator. Exercise keyboard navigation, close/reopen, and focus return.
5. Test effective reduced motion with the system preference off and on; test supported forced colors and preference changes. Check mobile/alternate surfaces and essential controllers when optional UI is absent.
6. Verify persistence, migration, restoration, and error paths with the actual host. Record untested lifecycle events instead of treating a storage-unit test as end-to-end coverage.
7. Ask for task/effort feedback after a reversible trial when a person is available. Do not manufacture errors, timing results, or comfort scores. A quick choice does not establish all-day comfort.

Report the tested versions and exact scope. “The tested token pairs pass contrast thresholds” is an appropriate calculation result; “every combination meets WCAG AA” is broader than those tests establish. Keep unsupported needs and pending runtime or user trials visible. [Evaluation scenarios](evaluations.md) exercise these distinctions when maintaining the skill.

## Sources and status

Reviewed **2026-11-23**. The feature design and acceptance workflow above are project recommendations informed by the linked sources; they are not additional normative WCAG criteria.

- [W3C: Accessibility Requirements for People with Low Vision](https://www.w3.org/TR/low-vision-needs/) — a Working Draft describing user needs, not a conformance standard.
- [WCAG 2.2](https://www.w3.org/TR/WCAG22/) and the exact criteria linked in [GUIDE.md](../GUIDE.md#review-checklist) — the technical baseline where applicable.
- [CSS Cascading and Inheritance, sorting order](https://www.w3.org/TR/css-cascade-5/#cascade-sort) — layer/importance precede selector specificity.
- [CSS Color 5, color mixing](https://www.w3.org/TR/css-color-5/#color-mix) — a CSS Working Draft describing color-space interpolation; verify the implemented behavior. A different blend model is not an equivalent calculation.
- [MDN: Element.animate()](https://developer.mozilla.org/en-US/docs/Web/API/Element/animate) — programmatic animation creation and playback.
- [Media Queries Level 5](https://www.w3.org/TR/mediaqueries-5/) (Working Draft) and [CSS Color Adjustment](https://www.w3.org/TR/css-color-adjust-1/) (Candidate Recommendation) — preference and forced-color mechanisms; verify support in the target.
