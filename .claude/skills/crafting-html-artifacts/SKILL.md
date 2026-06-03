---
name: crafting-html-artifacts
description: Generates polished, self-contained single-file HTML artifacts (status reports, slide decks, design systems, code reviews, flowcharts, explainers, implementation plans, and interactive editors) using a consistent editorial design language with inline CSS and JS and no external dependencies. Use when the user asks for an HTML report, dashboard, deck, mockup, diagram, one-pager, visual summary, or any shareable .html document instead of plain markdown.
allowed-tools: Read
---

# Crafting HTML artifacts

Produce a single, self-contained `.html` file that someone would actually read — a styled
report, deck, diagram, explainer, or small interactive tool — instead of a wall of
markdown. The look is a consistent editorial design language: ivory canvas, clay accent,
serif headings, generous whitespace.

## When to use this skill

Use it when the user wants a **visual, scannable, or shareable deliverable** rather than
prose or production code:

- **Reports & updates** — status reports, incident post-mortems, implementation plans.
- **Communication** — slide decks, PR write-ups, one-pagers, visual summaries.
- **Understanding** — code reviews, module maps, feature/concept explainers, flowcharts, SVG figures.
- **Design** — design-system references, component contact sheets.
- **Small interactive tools** — triage boards, feature-flag editors, prompt tuners, clickable prototypes.

**Do not** use it for plain conversational answers, for real application code that must
integrate into an existing build/framework, or when the user explicitly asks for markdown
or another format.

## Workflow

1. **Pick the closest template.** Match the request to a use case in
   [reference/template-catalog.md](reference/template-catalog.md) and note the matching file in `examples/`.
2. **Study it.** `Read` that example file to absorb its structure and interaction patterns,
   and skim [reference/design-system.md](reference/design-system.md) for the tokens and component recipes.
3. **Adapt, then emit one file.** Replace the sample content with the user's real subject,
   keep the design tokens and component patterns, and output a single self-contained `.html` file.

When nothing matches exactly, start from the nearest template and combine pieces (e.g. a
report with a chart plus a timeline).

## Design system (quick reference)

Full details in [reference/design-system.md](reference/design-system.md). Start every
artifact from this token block:

```css
:root{
  --ivory:#FAF9F5; --white:#FFFFFF; --slate:#141413;
  --clay:#D97757; --oat:#E3DACC; --olive:#788C5D; --rust:#B04A3F;
  --gray-100:#F0EEE6; --gray-300:#D1CFC5; --gray-500:#87867F; --gray-700:#3D3D3A;
  --serif:ui-serif,Georgia,serif; --sans:system-ui,-apple-system,sans-serif;
  --mono:ui-monospace,'SF Mono',Menlo,monospace;
  --radius-panel:12px; --radius-row:8px; --border:1.5px solid var(--gray-300);
}
```

Core rules:

- Ivory (`--ivory`) canvas, slate (`--slate`) text. **Clay (`--clay`) is the single
  accent** — use it sparingly for emphasis, links, and one highlighted element; `--olive`
  and `--rust` carry status (good / bad).
- **Serif** for headings (often with an italic clay `<em>`), **sans** for body, **mono**
  for eyebrows, labels, code, and small metadata (eyebrows are uppercase + letter-spaced).
- Centered single column: `.page { max-width: 860–980px; margin: 0 auto; }` with roomy padding.
- 1.5px borders (`--border`), `--radius-panel` / `--radius-row` corners, soft hover lift on cards/links.

## Template catalog

Pick from these (richer "pick this when…" notes in
[reference/template-catalog.md](reference/template-catalog.md)):

| Use case | Template (in `examples/`) |
|---|---|
| Compare 3 code approaches side by side | `01-exploration-code-approaches.html` |
| Compare visual / layout / palette options | `02-exploration-visual-designs.html` |
| Implementation plan (timeline, data-flow, risks) | `16-implementation-plan.html` |
| Annotated PR / code review (diff + margin notes) | `03-code-review-pr.html` |
| PR write-up for reviewers (motivation, file tour) | `17-pr-writeup.html` |
| Module map / code understanding (boxes & arrows) | `04-code-understanding.html` |
| Living design system (token swatches) | `05-design-system.html` |
| Component variants contact sheet | `06-component-variants.html` |
| Animation sandbox (tune easing/duration) | `07-prototype-animation.html` |
| Clickable multi-screen flow | `08-prototype-interaction.html` |
| Inline SVG figure sheet | `10-svg-illustrations.html` |
| Annotated flowchart / pipeline | `13-flowchart-diagram.html` |
| Arrow-key slide deck | `09-slide-deck.html` |
| Feature explainer (TL;DR, collapsibles, tabs, FAQ) | `14-research-feature-explainer.html` |
| Concept explainer (live interactive + glossary) | `15-research-concept-explainer.html` |
| Weekly status report (+ small chart) | `11-status-report.html` |
| Incident post-mortem (timeline, logs, follow-ups) | `12-incident-report.html` |
| Ticket triage board (drag → export markdown) | `18-editor-triage-board.html` |
| Feature-flag editor (toggles, deps, copy diff) | `19-editor-feature-flags.html` |
| Prompt tuner (editable template + live samples) | `20-editor-prompt-tuner.html` |

## Adapting a template

- Swap all copy/data for the user's real subject; keep the `:root` block and component structure.
- Resize or duplicate sections as needed; preserve the responsive `@media` rules.
- Keep any placeholder/sample data **obviously fictional** (the examples use the fake brand "Acme").
- For interactive artifacts, reuse the vanilla patterns already in the examples — drag/sort
  in `18`, tabs/collapsibles in `14`, toggles in `19`, live re-render in `20` — no frameworks.

## Output conventions (must follow)

- **One file.** A single `.html`, fully self-contained: all CSS in a `<style>` in `<head>`,
  all JS in an inline `<script>`. Vanilla JS only — no frameworks, no CDNs, no external
  fonts/images/network requests of any kind. (The SVG `xmlns="http://www.w3.org/2000/svg"`
  namespace is fine; it is not a network fetch.)
- **Document shell.** Begin with `<!doctype html>`, `<html lang="en">`, and `<meta charset>`
  plus a viewport meta.
- **Interactive artifacts end with an export.** Any editor/tool must include a button that
  turns the current UI state back into something pasteable/committable (markdown, JSON, or a
  diff) — see `examples/18`, `19`, `20`.
- **License header — do not copy Anthropic's.** The example files carry an Anthropic
  copyright header; **never** put it on the user's output. Use the user's own holder/year if
  known, otherwise a neutral placeholder or omit it entirely. If used, first line:
  `<!-- Copyright <year> <holder> · SPDX-License-Identifier: <license> -->`

## Resources

- [reference/design-system.md](reference/design-system.md) — complete tokens, typography, layout, component recipes.
- [reference/template-catalog.md](reference/template-catalog.md) — every example with a "pick this when…" guide.
- `examples/` — the 20 numbered reference artifacts plus `index.html` (the gallery overview).
