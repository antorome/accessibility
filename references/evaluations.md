# Evaluate the skill without conversation history

These scenarios check whether an agent can use this repository to produce useful work without an earlier discussion, a known diagnosis, or a reviewer telling it which defects to find. They are evaluation specifications, not evidence that a product or the skill has passed them.

## Method

Start a fresh context with the skill and the task's raw artifacts. Supply the relevant repository, application, screenshots, or settings, their versions, and the user's request. Do not supply the expected findings below to the task agent. Give the evaluator those expectations separately. Keep raw outputs, inspected revisions, calculations, diffs, and runtime evidence with the evaluation record.

Separate a documentation-following exercise from execution in a real app. A useful implementation plan is not a working extension; a working extension is not demonstrated personal benefit. Do not use a score or checklist completion percentage as an accessibility certification.

## Scenario set

| ID | Task or raw situation | Expected behavior | Failure to catch |
| --- | --- | --- | --- |
| E01 | “Make this app accessible.” No request for advanced settings. | Review the default experience and applicable journeys; preserve scope. Propose optional customization only with a stated benefit. | Adding a settings wizard while leaving basic text, focus, or color-only status failures in the default UI. |
| E02 | Text has adequate measured contrast; the person reports that the bright background is uncomfortable. | Distinguish luminance, polarity, text contrast, and context. Explore supported adjustments and a reversible task trial. | Declaring the difficulty solved by a 4.5:1 pass, prescribing a disease-specific dark preset, or claiming a screenshot measures emitted light. |
| E03 | The person wants clearer control boundaries and less luminous surfaces. | Explore borders/region separation independently of text brightness and hue; verify actual controls. | One “maximum contrast” switch that changes every dimension, or strong outlines around every decorative element. |
| E04 | “Adjust my browser and operating system so I can read comfortably.” An unrelated product repo is open. | Identify relevant screen/OS/browser/app layers; use supported settings, existing authorization, exact scope, and restoration. | Editing the unrelated app, inventing setting keys, or claiming a change was applied without access. |
| E05 | A small control set is being designed for people with varied visual needs. | Offer usable defaults, independent controls where justified, an insufficient/no-difference response, direct later adjustment, and representative task checks. | A diagnostic questionnaire, forced clinical labels, only an aesthetic vote, or a claim of optimal/all-day comfort after a quick choice. |
| E06 | A configurator is opened after another profile has already been applied. | Check candidate styles in every relevant prior state; isolate previews and compare with the resulting app. Include actual fields, focus, status indicators, and buttons. | Global rules overwrite sample colors; the chosen profile's own dialog violates its surface policy; only swatches are tested. |
| E07 | An extension uses inline-color substring selectors and generic status attributes. | Inspect property and component identity, unintended matches, cascade layers, and current class names; prefer semantic host hooks. | A `color:` search also matching `background-color:`, rotating a whole status row, or reporting a token as effective without resolving overrides. |
| E08 | Reduced motion can be selected in the app while the system preference is off. The host has CSS and JavaScript animations. | Trace the effective preference to both implementations; exercise a meaningful animated journey without hiding essential feedback. | Testing only `animation: none`, assuming it cancels `Element.animate()`, or treating a checkbox as evidence of coverage. |
| E09 | The host has changed framework, overlay library, or preference APIs since an old extension review. | Inspect the current checkout and build; verify each old finding; use supported APIs and remove obsolete workarounds after rechecking their purpose. | Porting obsolete React/Radix assumptions to a different framework, inventing a new SDK capability, or preserving stale selectors because the old checker passes. |
| E10 | The extension's controller is attached to a button hidden in a mobile menu; a theme can also change elsewhere. | Check controller lifetime on supported surfaces, preference precedence, external changes, and synchronization. | Essential behavior stops while an optional component is unmounted, or theme class and color tokens diverge. |
| E11 | A custom scale setting affects dialogs, popovers, and the main viewport. | Test narrow layouts, applicable resizing/reflow, combined zoom, reachable actions, keyboard/focus return, and real overlay positioning. | Declaring all scaling correct because text is larger, or declaring failure solely because the built-in control stops at 150%. |
| E12 | The person applies, changes, cancels, reloads, disables, and removes a profile. Storage contains an old or invalid value. | Define and test each supported transition, validate values, preserve prior state and unrelated changes, document unavailable cleanup. | Overwriting the restore snapshot on every choice, accepting inherited enum keys, or treating Off and uninstall as equivalent without a lifecycle contract. |
| E13 | A palette script passes, but the UI uses another blending space, translucent surfaces, or state overrides. | Match the calculation to actual compositing and resolved styles; distinguish token, rendered, interaction, and user-trial evidence. | A whole-product AA claim, unperformed browser tests presented as passes, or fabricated precise ratios from smoothed screenshot pixels. |
| E14 | An educational table contains color-vision, near-vision, migraine, and screen-symptom prevalence. | Keep denominators, dates, definitions, sources, overlap, and uncertainty. Use evidence to inform coverage, then validate functional needs. | Adding percentages, treating worker surveys as all-population disability rates, or estimating theme demand from disease prevalence. |
| E15 | A button is identifiable without a decorative border; no dark theme exists. | Apply the exact criterion and exception; make stronger boundaries or an extra theme a recommendation when useful. | Inventing an automatic AA failure for every missing border, every small font, or the absence of a built-in dark mode. |

For implementation evaluations, include an unseen variation of the artifact rather than merely asking the agent to recite the row. Change the starting profile, component role, mobile mounting behavior, or host API so success requires inspecting evidence. A regression test should assert the intended outcome and relevant non-target behavior, not just mirror the implementation.

## A reusable task for a new agent

Adapt the paths to the test environment. This is a task prompt; keep the scoring rubric outside the task agent's context:

```text
Use the accessibility skill in [repository/path]. Read its instructions
and the references relevant to this request. Inspect [current host] and
[current extension] at the supplied revisions.

Improve the extension so users can adjust visual legibility and comfort
for actual work. Preserve unrelated behavior and existing preferences.
Use the host's supported capabilities. Implement the changes within the
authorized scope, run the available meaningful checks, and report what
works, what was measured, and what remains untested.
```

When only analysis is being evaluated, explicitly request an implementation plan instead and record that limitation. Do not let that plan-only exercise stand in for build, integration, or user testing.

## Evaluation record

Record:

- Task prompt, skill revision, target revisions, and exactly which artifacts the agent could access.
- Fresh-context status; whether prior findings or expected answers were withheld.
- Routes/references selected and important decisions made from actual evidence.
- Executed checks and their outputs; unperformed checks and why they remain pending.
- Missed needs, false positives, unsupported assumptions, and required corrections.
- Implemented behavior versus proposed behavior, including an independent review where practical.

Use per-case **met**, **missed**, or **not exercised**, with evidence. Re-run only the relevant case or a fresh variation after a substantive correction. Do not claim all scenarios passed when only a subset was exercised. Historical client discovery/invocation checks apply to their recorded version; changing this documentation does not silently repeat them.
