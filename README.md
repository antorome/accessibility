# Accessibility

**Create readable interfaces. Find and fix visual accessibility barriers.**

An on-demand skill for developers, designers, and coding agents. Create color palettes, review web and app interfaces, and improve the readability of your editor or terminal. Preview changes and verify them with the available tools.

[Get started](#get-started) · [Create or review](#create-or-review) · [Guide](GUIDE.md) · [Contribute](#contribute)

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

Copy the five project files while preserving the folder layout. Keep the target project's existing instructions. Project trust and local settings may affect discovery.

Without skill discovery, give your agent access to `SKILL.md` and `GUIDE.md` and explicitly ask it to follow them for the task. A repository URL alone does not load their contents. You can also follow [GUIDE.md](GUIDE.md) directly for a developer-led review.

</details>

## Create or review

| Mode | Start with | Get back |
| --- | --- | --- |
| **Create** | A brief, brand colors, a logo, or a theme idea | A small palette, intended combinations, a visual proposal, and implementation guidance. |
| **Review and improve** | A URL, application, repository, design, screenshot, palette, or appearance settings | Prioritized changes, an action plan, evidence, and color proposals where useful. |

A palette, component, screen, or personal theme can be a complete task. For an existing product, review its real use within the agreed scope: page/screen families, components, themes, and states. Shared styles can resolve issues across many elements. Rechecking changes is part of the same workflow.

Name what you want reviewed: the product you develop, or the tools you use. Reviewing an editor's appearance concerns personal preferences, not the application open in that editor. The skill infers the context from your request.

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

Accessibility covers **visual interfaces and personal appearance settings**: color and contrast, typography, scaling, layout, focus, controls, charts, and display preferences. Related keyboard, image-alternative, and form checks are included when relevant.

For websites, use the web checklist. For desktop and mobile apps, use the shared visual guidance with platform-appropriate checks. For personal tools, propose supported theme and text settings with a way to restore them. App limitations outside those settings remain visible in the report.

Designs show intended presentation; source or theme files reveal configured values; a running interface allows interaction checks. Supplied mobile screenshots can support a limited review without connecting a device. The report identifies inspected screens, states, themes, versions, and gaps.

The guide draws on selected WCAG 2.2 criteria, non-web interpretation guidance, and practical recommendations. Findings do not establish whole-product conformance or certification. Full native-app evaluation needs platform-specific testing; system-wide setup, hardware, audio, and documents are outside this scope.

## Files

| File | Purpose |
| --- | --- |
| [README.md](README.md) | Installation, examples, and contribution guidance. |
| [SKILL.md](SKILL.md) | Activation metadata, workflow, evidence requirements, and implementation boundaries. |
| [GUIDE.md](GUIDE.md) | Checks, color proposals, examples, report format, and references. |
| [agents/openai.yaml](agents/openai.yaml) | Codex invocation policy. |
| [LICENSE](LICENSE) | MIT license. |

## Contribute

Open an [issue](https://github.com/antorome/accessibility/issues) for a reproducible problem, a question, or a missing user need. Submit a focused pull request for an improvement. Contributions from people who use assistive technology are especially welcome.

Keep documentation in English. Keep workflow instructions in `SKILL.md`, technical guidance in `GUIDE.md`, and installation and maintenance instructions here. Improve existing sections before adding files. Keep task-specific previews and reports with their reviews and preserve licensing and attribution requirements when reusing material.

For a changed check, include the user need, a primary source, when it applies, a failing example, a corrected example, and a verification method. Explain what you tested and remove private data. Check links, anchors, thresholds, exceptions, and example instructions before submitting. Update source-review dates only for references actually rechecked.

For a packaging change, validate the YAML and relative references, then check discovery, explicit invocation, and the absence of implicit activation in the affected environment. Report the client version and distinguish executed tests from documentation review. Installation references were reviewed on **2026-09-07**; cross-client runtime testing is not yet recorded.

Maintained by [antorome](https://github.com/antorome) and contributors. Original material is [MIT licensed](LICENSE). Referenced standards retain their own terms.
