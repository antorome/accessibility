# Accessibility

**Build readable products. Offer useful visual adjustments. Adapt personal environments.**

A color palette is part of how an interface works. Together with typography, spacing, icons, and focus indicators, it determines whether people can read content, distinguish controls, understand a chart, or notice an error. IDEs, applications, and operating systems often present themes as a matter of personal taste. Appearance matters, but a theme also determines whether an interface is comfortable to use or difficult to read, especially for people with low vision or differences in color perception.

Making those choices well takes knowledge and time. Before AI-assisted development, researching accessibility guidance, comparing color combinations, implementing changes, and checking every state required more manual work. Not every developer or product designer had specialist training or the resources to do it thoroughly. Those constraints were real, even though users still needed readable interfaces.

AI can now help bring that work into the everyday development process. Agents can inspect styles, propose palettes, measure contrast, update shared components, and run repeatable checks. Readability and accessibility should be standard requirements in every digital product, with routine checks automated wherever possible, rather than optional polish or a special theme users must find and enable. Automation does not guarantee accessibility: the result still needs verification in the actual interface and feedback from the people who use it.

This repository helps developers put that approach into practice and helps people adapt the tools they use. The goal is to make accessible design easier to apply from the start, maintain it as a product changes, and connect personal adjustments to the tasks that are difficult to see or perform.

The on-demand skill is a dependency-free set of instructions and references for developers, designers, users, and coding agents. It is not a browser overlay or a medical assessment. It guides work through the available platform tools; it does not itself control a monitor or operating system.

[Get started](#get-started) · [Choose your use case](#choose-your-use-case) · [Create or review](#create-or-review) · [Guide](GUIDE.md) · [Visual needs](references/visual-needs.md) · [Evidence](references/visual-evidence.md) · [Contribute](#contribute)

## Choose your use case

There are two audiences. Developers have two distinct kinds of work:

| Audience and route | Goal | Deliverable |
| --- | --- | --- |
| **Developer: accessible defaults** | Make the app or website readable and operable in its ordinary experience. | Applicable checks, focused implementation changes, and evidence across relevant states. |
| **Developer: optional personalization** | When wanted, let users adapt presentation to differing visual needs. | Supported independent adjustments, a usable configurator or settings UI, faithful previews, restoration, and integration checks. |
| **Person: personal environment** | Make an existing working environment easier to see and use. | Supported screen, OS, browser, and app adjustments at the appropriate layer, with a task trial and restoration. |

Optional personalization does not replace accessible defaults, and not every product needs its own theme editor. Existing browser, OS, and application preferences may already supply an adjustment. The skill first identifies the target and capability rather than prescribing a particular implementation.

Start from a **functional difficulty**, such as reading small comments, distinguishing a failed task, locating a field boundary, tolerating a luminous surface, or recovering the caret. Keep luminance, polarity, text contrast, control boundaries, color differentiation, scale, and motion distinct when their effects serve different needs. Do not assign a theme from a diagnosis or a population statistic.

The result follows **need → supported adjustment → applied result → technical check → task/comfort outcome → restoration**. A contrast pass, an aesthetic preference, and a useful personal adjustment are different forms of evidence. Subjective comfort matters, but a quick comparison cannot establish all-day benefit.

## Get started

Install the repository as a skill, then invoke it with the interface or personal settings you want to improve. Choose a folder for your environment:

| Environment | Personal installation folder | Invoke in agent chat |
| --- | --- | --- |
| [Codex CLI / IDE](https://developers.openai.com/codex/skills) | `~/.agents/skills/accessibility/` | `$accessibility` |
| [Claude Code](https://code.claude.com/docs/en/skills) | `~/.claude/skills/accessibility/` | `/accessibility` |
| [Cursor](https://cursor.com/docs/skills) | `~/.cursor/skills/accessibility/` | `/accessibility` |
| [Grok Build](https://docs.x.ai/build/features/skills-plugins-marketplaces) | `~/.grok/skills/accessibility/` | `/accessibility` |
| [Pi coding agent](https://pi.dev/docs/latest/skills) | `~/.pi/agent/skills/accessibility/` | `/skill:accessibility` |

For example, in a POSIX shell, install for Codex with:

```sh
skill_dir="$HOME/.agents/skills/accessibility"
mkdir -p "$(dirname "$skill_dir")"
git clone https://github.com/antorome/accessibility.git "$skill_dir"
```

For another environment, change `skill_dir` to the corresponding folder above, using `$HOME` for `~`. Keep the full repository together, with `SKILL.md` directly inside the `accessibility` folder. Review the files before use. An existing destination must be inspected rather than overwritten.

Start an agent session with access to the target material, then invoke the skill with a task. For Codex:

```text
$accessibility Review this project's interface. Preserve the brand.
Show the important changes, an action plan, and what remains unchecked.
Preview proposed color changes. Leave application source files unchanged
until I approve the plan.
```

Use `/accessibility` in Claude Code, Cursor, or Grok Build; use `/skill:accessibility` in Pi. The report follows your language.

### Activation

Accessibility is configured for **explicit invocation**. Installing it in a personal folder makes it available across projects; it does not make it an always-on audit.

[SKILL.md](SKILL.md) sets `disable-model-invocation: true` for Claude Code, Cursor, Grok Build, and Pi. [agents/openai.yaml](agents/openai.yaml) sets `policy.allow_implicit_invocation: false` for Codex. These settings control skill selection, not tool permissions or authorization to modify source files or settings. The linked platform documentation and [Codex's metadata reference](https://github.com/openai/codex/blob/6750f5bd1356fe1553c0fcc9f2632704f3055946/codex-rs/skills/src/assets/samples/skill-creator/references/openai_yaml.md) describe the behavior; [Grok's skill reference](https://github.com/xai-org/grok-build/blob/main/crates/codegen/xai-grok-pager/docs/user-guide/08-skills.md) documents its frontmatter fields.

If the command is missing, check the folder and filename, restart the session, and check the environment's skill settings. In Pi, skill commands must be enabled. Some environments also discover other agents' skill directories; avoid duplicate installations under the same name.

<details>
<summary><strong>Project-only installation or direct use</strong></summary>

For a project-only installation, place the full skill folder under the target project's corresponding directory:

| Environment | Project folder |
| --- | --- |
| Codex | `.agents/skills/accessibility/` |
| Claude Code | `.claude/skills/accessibility/` |
| Cursor | `.cursor/skills/accessibility/` |
| Grok Build | `.grok/skills/accessibility/` |
| Pi | `.pi/skills/accessibility/` |

Copy the full repository contents, including `references/` and `agents/`, while preserving the folder layout. Keep the target project's existing instructions. Project trust and local settings may affect discovery.

Without skill discovery, give your agent access to the full repository and explicitly ask it to read `SKILL.md` and follow its links for the task. A repository URL alone does not load their contents. You can also follow [GUIDE.md](GUIDE.md) directly for a developer-led review.

</details>

## Create or review

| Mode | Start with | Get back |
| --- | --- | --- |
| **Create** | A brief, brand colors, a logo, or a theme idea | A small palette, intended combinations, a visual proposal, and implementation guidance. |
| **Review and improve** | A URL, application, repository, design, screenshot, palette, or appearance settings | Prioritized changes, an action plan, evidence, and color proposals where useful. |

A palette, component, screen, or personal theme can be a complete task. For an existing product, review its real use within the agreed scope: page/screen families, components, themes, and states. Shared styles can resolve issues across many elements. Rechecking changes is part of the same workflow.

Name what you want reviewed: the product you develop, or the tools you use. Reviewing an editor's appearance concerns personal preferences, not the application open in that editor. The skill infers the context from your request.

For implementation requests, the agent should complete the authorized work and relevant checks. A review-only prompt can deliberately ask for a proposal first; the skill does not require an extra approval step for changes already requested.

<details>
<summary><strong>Create a color palette</strong></summary>

Invoke the skill with:

```text
Create a small palette for a booking application using the brand colors
provided. Derive functional variants where needed. Show one recommended
palette and up to two meaningful alternatives on text, links, a button,
and a form field. Include measured foreground/background combinations.
```

See the [starter palette](GUIDE.md#starter-example) for an example with measured contrast ratios.

</details>

<details>
<summary><strong>Review an application screen</strong></summary>

```text
Review the visual accessibility of this desktop or mobile app screen.
Use the supplied design, screenshots, code, or running interface.
Prioritize readability, scaling, controls, and important states.
Show the changes that matter and distinguish verified findings from
questions that need a running app or device. Do not edit files yet.
```

A phone connection is not required for a screenshot-led review. Findings
remain limited to the material available; untested interaction stays pending.

</details>

<details>
<summary><strong>Improve your editor or terminal</strong></summary>

```text
Review my editor and terminal appearance, not the project open in them.
Improve code, comments, diffs, selection, panels, and text sizing while
preserving the overall character of my theme. Use supported settings.
Show a before/after proposal, the exact changes, and how to restore the
previous values. Keep this personal; leave project files and settings
unchanged. Do not apply changes until I approve them.
```

See [applications and personal workspace](GUIDE.md#applications-and-personal-workspace).

</details>

<details>
<summary><strong>Adapt an operating system, browser, and apps</strong></summary>

```text
Use accessibility to help me read and find controls in my working
environment. The bright surfaces are uncomfortable and field boundaries
are hard to distinguish. Inspect the available screen, OS, browser, and
app settings. Use the appropriate layer and keep these needs separate.
Apply the supported personal changes within this request, preserve
unrelated settings, and record how to restore them. Compare representative
tasks and distinguish technical checks from my feedback after a trial.
```

The agent records what it can actually inspect or change. It does not infer physical luminance or a diagnosis from a screenshot. See [Visual needs](references/visual-needs.md).

</details>

<details>
<summary><strong>Build or improve a visual-settings extension</strong></summary>

```text
Use accessibility to implement visual personalization for this app.
Read the current app and extension contracts before choosing a design.
Keep the default experience accessible; offer only useful additional
adjustments. Support functional needs, faithful comparisons, direct later
settings, reversible trials, persistence, and restoration. Prefer current
host APIs and remove obsolete workarounds after verifying their purpose.
Implement and test the changes, and report token calculations, rendered
behavior, and user-trial outcomes separately. Do not claim untested results.
```

Read [Personalization implementation](references/personalization.md). These instructions are intended to work without a previous conversation or a list of historical bugs. [Evaluation scenarios](references/evaluations.md) describe how to check that behavior in fresh contexts.

</details>

<details>
<summary><strong>Apply an approved plan</strong></summary>

After reviewing the proposal:

```text
Apply the agreed changes and selected color proposal. Preserve project
conventions and unrelated work. Recheck affected components, themes,
and states, then update the report with the results and remaining work.
Stay within the approved scope and use the existing tools.
```

</details>

## What you receive

One report combines the findings and action plan, with evidence below the summary. Color proposals use representative content in the target application, design environment, or a local HTML preview. Mockups are labeled separately from previews in the actual application. When a check or preview cannot be performed, the report states the gap.

*Example summary:*

> ### Changes that matter
>
> **1. Improve secondary text contrast.** Adjust the shared style used by cards and forms, then check each surface where it appears.
>
> **2. Keep keyboard focus visible.** Restore the focus treatment on navigation and dialog controls.
>
> **3. Explain form errors.** Add a clear message next to each affected field so errors can be understood without relying on red.
>
> **Your decision:** compare the proposed color variants.
>
> **Scope:** selected public screens, mobile and desktop. The signed-in area is pending.
>
> **Details:** affected components, evidence, verification steps, and remaining findings.

Results use **✓ Checked**, **✕ Fix**, and **? Pending**, always with text. Each result names what was examined. Pending items include a reason and the next check. Design decisions are shown separately.

See the [report format](GUIDE.md#report) and [preview instructions](GUIDE.md#preview-brief).

## Scope

Accessibility covers **visual interfaces, optional visual personalization, and personal visual environments**: color and contrast, typography, scaling, layout, focus, controls, charts, display preferences, and supported screen/OS/browser/app adjustments. Related keyboard, image-alternative, and form checks are included when relevant.

For websites, use the web checklist. For desktop and mobile apps, use the shared visual guidance with platform-appropriate checks. For personal environments, identify the need and supported capability, preserve prior settings, and test representative use. For configurators and extensions, inspect the current host version, actual components, lifecycle, and effective settings. Unsupported needs remain visible in the report.

Designs show intended presentation; source or theme files reveal configured values; a running interface allows interaction checks. Supplied mobile screenshots can support a limited review without connecting a device. The report identifies inspected screens, states, themes, versions, and gaps.

The guide draws on selected WCAG 2.2 criteria, non-web interpretation guidance, functional user needs, and practical recommendations. Findings do not establish whole-product conformance or certification. Full native-app evaluation needs platform-specific testing. General system administration, hardware repair, clinical diagnosis/treatment, audio accessibility, and document accessibility are outside this visual scope. Physical luminance, glare, or panel-flicker measurements require appropriate access and methods; a theme change cannot establish them.

### Educational evidence

[Visual evidence](references/visual-evidence.md) explains relevant conditions and traits, selected prevalence estimates, their populations and dates, and evidence limits. Prevalence is not incidence, symptom prevalence is not a disability rate, and overlapping estimates must not be added. The reference informs coverage and education; it does not predict which setting an individual needs or how many users will prefer a theme.

## Files

| File | Purpose |
| --- | --- |
| [README.md](README.md) | Installation, examples, and contribution guidance. |
| [SKILL.md](SKILL.md) | Activation metadata, workflow, evidence requirements, and implementation boundaries. |
| [GUIDE.md](GUIDE.md) | Checks, color proposals, examples, report format, and references. |
| [references/visual-needs.md](references/visual-needs.md) | Functional difficulties, independent adjustments, four environment layers, and task validation. |
| [references/personalization.md](references/personalization.md) | Implementation and verification of settings, configurators, and host extensions. |
| [references/visual-evidence.md](references/visual-evidence.md) | Educational evidence and prevalence with population, date, sources, and uncertainty. |
| [references/evaluations.md](references/evaluations.md) | Fresh-context evaluation scenarios and evidence-recording method. |
| [agents/openai.yaml](agents/openai.yaml) | Codex invocation policy. |
| [LICENSE](LICENSE) | MIT license. |

## Contribute

Open an [issue](https://github.com/antorome/accessibility/issues) for a reproducible problem, a question, or a missing user need. Submit a focused pull request for an improvement. Contributions from people who use assistive technology are especially welcome.

Keep documentation in English. Keep routing and workflow in `SKILL.md`, technical checks in `GUIDE.md`, focused task references in `references/`, and installation and maintenance instructions here. Link every task reference directly from `SKILL.md` and load it only when relevant. Improve existing sections before adding files. Keep task-specific previews and reports with their reviews and preserve licensing and attribution requirements when reusing material.

For a changed check, include the user need, a primary source, when it applies, a failing example, a corrected example, and a verification method. Explain what you tested and remove private data. Check links, anchors, thresholds, exceptions, and example instructions before submitting. Update source-review dates only for references actually rechecked.

For a changed adaptation workflow, use relevant [evaluation scenarios](references/evaluations.md), including a fresh-context task with raw artifacts and no leaked findings. Keep evaluation specifications separate from actual results. For prevalence, retain the original population, definition, date, uncertainty, and source; do not infer market size or a clinical recommendation from it.

For a packaging change, validate the YAML and relative references, then check discovery, explicit invocation, and the absence of implicit activation in the affected environment. Report the client version and distinguish executed tests from documentation review.

Some generic skill validators do not recognize the platform-specific `disable-model-invocation` field. Check it against the linked client documentation and validate the rest of the structure separately; do not remove explicit-invocation policy merely to satisfy a narrower validator. Preserve `agents/openai.yaml` for Codex's policy.

Historical project-level discovery checks for the earlier five-file package used Claude Code 2.1.319 and Codex CLI 0.163.0: explicit invocation loaded `SKILL.md` and `GUIDE.md` from the project folder, and an unrelated request did not activate the skill. These are not a re-test of the expanded reference package. Re-run affected client checks when packaging changes. Cursor, Grok Build, and Pi have not been tested here.

Maintained by [antorome](https://github.com/antorome) and contributors. Original material is [MIT licensed](LICENSE). Referenced standards retain their own terms.
