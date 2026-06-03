# Template catalog

Every reference artifact in `examples/`, grouped by the kind of work it replaces. Find the
closest match, then `Read` that file and adapt it. Descriptions are the curated copy from
the gallery (`examples/index.html`).

## Contents

- [Exploration & planning](#exploration--planning)
- [Code review & understanding](#code-review--understanding)
- [Design](#design)
- [Prototyping](#prototyping)
- [Illustrations & diagrams](#illustrations--diagrams)
- [Decks](#decks)
- [Research & learning](#research--learning)
- [Reports](#reports)
- [Custom editing interfaces](#custom-editing-interfaces)

## Exploration & planning

*When you're not sure what you want yet — fan out across directions and lay them side by
side, then turn the pick into a plan.*

| Template | What it is | Pick this when |
|---|---|---|
| `01-exploration-code-approaches.html` | **Three code approaches** — side-by-side comparison of three ways to solve the same problem, with trade-offs called out inline. | The user wants to weigh multiple implementations against each other before committing. |
| `02-exploration-visual-designs.html` | **Visual design directions** — a handful of layout and palette options rendered live so you can react to them, not imagine them. | Exploring UI/visual options the user should *see*, not read about. |
| `16-implementation-plan.html` | **Implementation plan** — milestones on a timeline, a data-flow diagram, inline mockups, the risky code, and a risk table. | Handing off a plan an implementer will actually follow. |

## Code review & understanding

*Diffs and call-graphs are spatial; markdown flattens them. Render the change or the module
so its shape is visible at a glance.*

| Template | What it is | Pick this when |
|---|---|---|
| `03-code-review-pr.html` | **Annotated pull request** — a diff with margin notes, severity tags and jump links. | Presenting review feedback on a concrete diff. |
| `17-pr-writeup.html` | **PR writeup for reviewers** — motivation, before/after, a file-by-file tour with the *why*, and where to focus. | The author explaining a PR so reviewers know what to look at. |
| `04-code-understanding.html` | **Module map** — an unfamiliar package as boxes and arrows, hot path highlighted, entry points listed. | Explaining how an unfamiliar codebase/module fits together. |

## Design

*HTML is the medium a design system ships in, so it's the natural format to discuss it —
tokens become swatches, components become contact sheets.*

| Template | What it is | Pick this when |
|---|---|---|
| `05-design-system.html` | **Living design system** — colors, type scale and spacing tokens rendered as swatches you can copy from. | Documenting or proposing design tokens / a style foundation. |
| `06-component-variants.html` | **Component variants** — every size, state and intent of one component on a single sheet. | Reviewing all the states of a single component at once. |

## Prototyping

*Motion and interaction can't be described, only felt. A throwaway page with the real curve
or click-through says it in five seconds.*

| Template | What it is | Pick this when |
|---|---|---|
| `07-prototype-animation.html` | **Animation sandbox** — the transition in isolation with sliders for duration and easing. | Tuning an animation/transition before wiring it in. |
| `08-prototype-interaction.html` | **Clickable flow** — a few screens linked together with enough fidelity to feel the interaction. | Validating a multi-step flow or navigation. |

## Illustrations & diagrams

*Inline SVG gives the agent a real pen — vector art you can tweak by hand or paste into the
final document.*

| Template | What it is | Pick this when |
|---|---|---|
| `10-svg-illustrations.html` | **SVG figure sheet** — diagrams for a post, drawn inline so they can be tweaked and copied out one by one. | Producing reusable figures/illustrations for a doc or post. |
| `13-flowchart-diagram.html` | **Annotated flowchart** — a pipeline drawn as a real flowchart; click a step for what runs, timings, failure paths. | Showing a process/pipeline with branches and detail-on-click. |

## Decks

*A handful of `<section>` tags and twenty lines of JS is a slide deck — arrow-key through it
in a meeting, no Keynote, no export step.*

| Template | What it is | Pick this when |
|---|---|---|
| `09-slide-deck.html` | **Arrow-key slide deck** — a short presentation as one HTML file; left/right to navigate. | The user wants slides from a thread, doc, or summary. |

## Research & learning

*Collapsible sections, tabbed samples, and a margin glossary make a new topic navigable in a
way a linear dump never is.*

| Template | What it is | Pick this when |
|---|---|---|
| `14-research-feature-explainer.html` | **How a feature works** — TL;DR box, collapsible steps, tabbed config snippets, FAQ. | Explaining how a specific feature/system in a repo works. |
| `15-research-concept-explainer.html` | **Concept explainer** — a concept taught with a live interactive, a comparison table, and a hover-linked glossary. | Teaching a general concept with an interactive aid. |

## Reports

*Recurring documents benefit most from a little structure and color — a small chart and a
colored timeline turn a skim into a read.*

| Template | What it is | Pick this when |
|---|---|---|
| `11-status-report.html` | **Weekly status** — what shipped, what slipped, and a small chart, formatted for a quick skim. | Periodic status / progress updates. |
| `12-incident-report.html` | **Incident timeline** — a post-mortem with a minute-by-minute timeline, log excerpts, and the follow-up checklist. | Post-mortems / incident write-ups. |

## Custom editing interfaces

*When it's hard to describe what you want in a text box, build a throwaway editor — and
always end with an export button that turns the UI state back into something pasteable.*

| Template | What it is | Pick this when |
|---|---|---|
| `18-editor-triage-board.html` | **Ticket triage board** — drag tickets across Now / Next / Later / Cut, then copy the ordering out as markdown. | Prioritizing/sorting a set of items interactively. |
| `19-editor-feature-flags.html` | **Feature flag editor** — toggles grouped by area, dependency warnings, and a "copy diff" for changed keys. | Editing a set of toggles/config with relationships. |
| `20-editor-prompt-tuner.html` | **Prompt tuner** — an editable template with highlighted variable slots; sample inputs re-render live as you type. | Iterating on a template/prompt with live previews. |
