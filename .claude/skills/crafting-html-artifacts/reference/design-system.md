# Design system reference

The shared visual language for every artifact. The goal is an *editorial* feel — a printed
report or a well-set magazine page, not a SaaS dashboard. When in doubt, copy the exact
markup from the closest file in `examples/` and change only the content.

## Contents

- [Design tokens](#design-tokens)
- [Typography](#typography)
- [Color usage](#color-usage)
- [Layout](#layout)
- [Borders, radii, elevation](#borders-radii-elevation)
- [Component recipes](#component-recipes)
- [Interaction patterns](#interaction-patterns)
- [Responsiveness](#responsiveness)
- [Do / don't](#do--dont)

## Design tokens

The canonical set used by the content artifacts (e.g. `examples/05-design-system.html`,
`examples/11-status-report.html`). Paste this `:root` block at the top of every file:

```css
:root{
  --ivory:#FAF9F5;   /* page background */
  --white:#FFFFFF;   /* panels, cards */
  --slate:#141413;   /* primary text */
  --clay:#D97757;    /* the single accent */
  --clay-d:#B85C3E;  /* darker clay for hover/active (optional) */
  --oat:#E3DACC;     /* warm fill / secondary surface */
  --olive:#788C5D;   /* positive / "good" status */
  --rust:#B04A3F;    /* negative / "bad" status, alerts */
  --gray-100:#F0EEE6;
  --gray-300:#D1CFC5;
  --gray-500:#87867F;
  --gray-700:#3D3D3A;
  --serif:ui-serif, Georgia, serif;
  --sans:system-ui, -apple-system, sans-serif;
  --mono:ui-monospace, 'SF Mono', Menlo, monospace;
  --radius-panel:12px;
  --radius-row:8px;
  --border:1.5px solid var(--gray-300);
}
```

> Variant: the gallery index (`examples/index.html`) uses an equivalent set with names
> `--paper` (= `--white`), `--g100`…`--g700` (= `--gray-100`…`--gray-700`), and a wider
> `.wrap` (max-width 1120px). Prefer the `--gray-*` names above for new artifacts; just stay
> consistent within a file.

## Typography

Three families, each with a job:

- **`--serif`** — headings and large display text. Weight `500` (not bold), tight tracking
  (`letter-spacing:-0.01em` to `-0.018em`). Emphasis inside a heading is an italic clay
  `<em>`: `h1 em{ font-style:italic; color:var(--clay); }`.
- **`--sans`** — body copy and UI. Base `font-size:15px`, `line-height:1.55–1.6`. Enable
  `-webkit-font-smoothing:antialiased` on `body`.
- **`--mono`** — eyebrows, labels, metadata, filenames, code. Small (`10–13px`); for
  eyebrows use `text-transform:uppercase; letter-spacing:0.08–0.12em; color:var(--gray-500)`.

Rough scale seen in the examples: display `h1` ~38–62px (use `clamp()` for hero pages),
section `h2` ~27px, card/title ~19px, body 15px, small/meta 11–13px.

## Color usage

- **Ivory canvas, slate text, white panels.** Never a pure-white page background — `--ivory`
  is the paper.
- **Clay is precious.** One accent color. Use it for links, a single highlighted figure, the
  active state, and italic heading emphasis — not for large fills. `--oat` is the warm
  neutral fill when you need a second surface.
- **Status semantics:** `--olive` = good/on-track/added; `--rust` = bad/at-risk/removed.
  Keep status color on small elements (dots, pills, left-borders), not whole blocks.
- **Grays** carry structure: `--gray-300` for borders, `--gray-500` for muted/meta text,
  `--gray-700` for secondary body text, `--gray-100` for subtle fills/zebra rows.

## Layout

- Centered single column: `.page{ max-width:860px; margin:0 auto; }` (use ~980px for
  denser, table-heavy artifacts; ~1120px only for gallery-style grids).
- Page padding roughly `56px 24px 120px` (top, sides, generous bottom).
- Vertical rhythm via section margins (~40–72px between major sections); let whitespace do
  the work rather than dividers everywhere.

## Borders, radii, elevation

- Borders are **1.5px**, color `--gray-300` (`var(--border)`). Use borders, not shadows, as
  the default separator.
- Radii: panels/cards `--radius-panel` (12–14px), rows/pills/small controls `--radius-row`
  (8px), fully-round pills `999px`.
- Elevation is reserved for hover: cards lift with
  `transform:translateY(-3px); box-shadow:0 10px 30px rgba(20,20,19,.10); border-color:var(--slate);`
  on `:hover`, transitioned over ~150ms.

## Component recipes

Grounded in the example files — open the named file for exact markup.

- **Eyebrow / kicker** (`examples/index.html`): a mono, uppercase, letter-spaced label in
  `--gray-500`, optionally preceded by a short clay rule
  (`::before{ content:""; width:24px; height:1.5px; background:var(--clay); }`).
- **Masthead** — serif `h1` with an italic clay `<em>`, a `--gray-700` intro paragraph
  (max-width ~620px), sitting above a `1.5px solid var(--gray-300)` bottom border.
- **Card grid** (`examples/index.html`) — `display:grid; grid-template-columns:repeat(auto-fill,minmax(316px,1fr)); gap:20px;`
  cards are white, 1.5px border, `--radius-panel`, with the hover lift above.
- **Panel & rows** (`examples/05`, `11`) — a white panel (`--radius-panel`, `--border`)
  containing rows separated by `--gray-100` hairlines; row corners `--radius-row`.
- **Status pill / badge** — small pill (`border-radius:999px`, mono ~11px) tinted with
  `--olive` / `--rust` / `--oat`; or a left border-accent on a row.
- **Tables** — header row in mono/uppercase `--gray-500`; body rows separated by
  `--gray-100`; optional `--gray-100` zebra; numbers right-aligned.
- **Timeline** (`examples/12`, `16`) — a vertical line (`--gray-300`) with colored node
  dots (`--clay`/`--olive`/`--rust`) and text to the right.
- **Bar chart, no library** (`examples/11`) — flex row of `<div>` bars with pixel heights
  and token fills (`--olive`/`--clay`/`--oat`); label below in mono.
- **Code block** — `--gray-100` (or `--slate` for dark) background, mono, `--radius-row`;
  inline added/removed lines tinted with `--olive`/`--rust` at low opacity (see `examples/03`).
- **Buttons** — solid clay primary (`background:var(--clay); color:var(--white)`), or
  outline (`--border`, transparent); `--radius-row`; hover → `--clay-d` / `border-color:var(--slate)`.
- **SVG diagrams** (`examples/04`, `10`, `13`) — inline `<svg>` with token strokes/fills;
  reuse the small utility classes (`.ln`, `.lc`, `.fl`, `.cl`, …) seen in `examples/index.html`.

## Interaction patterns

All vanilla JS, inline, no dependencies. Reuse these from the examples:

- **Slide deck** (`examples/09`) — `<section>` per slide, arrow-key handler toggling an
  `.active` class.
- **Collapsibles / tabs / FAQ** (`examples/14`) — class-toggle on click; `<details>` is fine too.
- **Drag-to-reorder / sort** (`examples/18`) — pointer/drag handlers moving nodes between columns.
- **Toggles with dependencies** (`examples/19`) — checkbox state + a warning when a
  prerequisite is off.
- **Live re-render** (`examples/20`) — `input` event recomputes a preview from a template.
- **Export button** — every interactive artifact ends with a control that serializes UI
  state to markdown/JSON/diff and copies it to the clipboard.

## Responsiveness

- Mobile-first enough to be usable: collapse multi-column grids to one column under ~640–880px
  via `@media (max-width:…)`. Keep the existing breakpoints when adapting a template.
- Use `clamp()` for hero headings so display type scales down gracefully.

## Do / don't

- **Do** keep it self-contained, restrained, and text-led; let one clay accent and good
  spacing carry the design.
- **Do** match the chosen template's existing structure and class names — change content, not architecture.
- **Don't** add frameworks, web fonts, CDNs, icon packs, or any network request.
- **Don't** flood the page with color — clay is an accent, not a fill.
- **Don't** carry over the example's Anthropic copyright header onto the user's output.
