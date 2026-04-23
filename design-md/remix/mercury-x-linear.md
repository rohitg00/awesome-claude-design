# Mercury × Linear — Surgical Density On Warm Paper

Remix. Mercury's cream-canvas fintech warmth + Linear's surgical UI density. For B2B finance dashboards, billing consoles, and treasury tools that need Linear-grade information density without losing the trust-broadcasting warmth Mercury earned.

## Parent DNA: Mercury 55% · Linear 45%

## 1. Visual Theme & Atmosphere

Mercury sets the canvas — cream paper, warm gray ink, indigo as the only saturated voice. Linear sets the geometry — 4px base, dense tables, keyboard-first affordances, command-bar muscle memory, hairline borders.

The page reads like a financial broadsheet that opens into a Linear-grade dashboard. Editorial restraint above the fold; surgical density inside the app.

Mood: trustworthy, deliberate, fast, unhurried at rest, instant under fingers.

## 2. Color Palette & Roles

```
/* canvas from Mercury — warm fintech paper */
--bg:              #f6f5f2
--bg-alt:          #ebe8e0
--surface:         #ffffff
--surface-alt:     #fbfaf6
--text:            #2a2924
--text-muted:      #5a5548
--text-dim:        #8a8478
--border:          #ded9ca
--border-strong:   #c9c3b3

/* accent from Mercury — indigo holds (fintech trust) */
--accent:          #5266eb
--accent-hover:    #4255d4
--accent-soft:     #e2e6fb

/* signals from Mercury */
--success:         #2f7d57
--warning:         #c98a42
--danger:          #b54a3a

/* dark mode adopts Linear's discipline, warmer than pitch */
--bg-dark:         #15140f
--bg-dark-alt:     #1d1c16
--surface-dark:    #25241d
--text-dark:       #f6f5f2
--text-dark-muted: #a8a394
--border-dark:     #34322a
```

Arbitration: Mercury's cream wins all surfaces — Linear's pure white would kill the warmth. Mercury indigo wins over Linear purple — fintech trust signal cannot break. Linear's discipline shows in dark mode (warmer Mercury cream-on-coal, but Linear-tight contrast).

## 3. Typography Rules

- **Display / h1 (marketing, statements):** Arcadia Display (Mercury), fallback Tiempos Headline. Weight 400, letter-spacing -1%.
- **App headings + body:** Inter (Linear), weights 400 / 500 / 600. Body 14/22 in app, 16/26 in marketing.
- **Numerals (every dollar, every row, every chart):** Arcadia tabular variant (Mercury) — never proportional figures on money. Tabular fallback to `font-variant-numeric: tabular-nums`.
- **Mono:** Berkeley Mono (Linear) for transaction IDs, command-bar input, code.

Scale: Linear's tight ramp + Mercury's display top. 11 / 13 / 14 / 16 / 18 / 22 / 28 / 36 / 48 / 72.

Display serif fires above 36px only. App UI stays Inter for density. Tabular numerals are non-negotiable on money.

## 4. Component Stylings

**Button (primary)**
- Geometry: Linear-tight on app surfaces (radius 6, padding 8/14, weight 500). Mercury-pill on marketing (radius 999, padding 10/20, weight 500).
- Fill `--accent`, text `#ffffff`. No shadow. Hover: `--accent-hover`, no lift.

**Button (secondary)**
- App: `--surface` fill, 1px `--border`, `--text` color. Linear pattern.
- Marketing: `--bg-alt` fill, no border, pill radius. Mercury pattern.

**Card / dashboard tile**
- `--surface` (white) on `--bg`, 1px `--border`, radius 8, no shadow.
- Account tiles: balance in 36px Arcadia tabular, label in 12px uppercase eyebrow `--text-muted`, hairline `--border` separator above row data.

**Input**
- App: 1px `--border`, radius 6, padding 8/12. Linear geometry.
- Forms (signup, transfer): pill radius 999, padding 10/16. Mercury geometry.
- Focus on both: 2px `--accent` ring, 2px offset.

**Tables (the centerpiece)**
- Linear density: 14px Inter body, hairline `--border` between rows, 12px uppercase eyebrow header on `--bg-alt`, sticky header.
- Mercury discipline: tabular numerals on every money column, right-aligned. Account / category columns left-aligned. Currency symbol always present.
- Row height 36px. Hover row: `--surface-alt`. Selected row: 1px `--accent` left border.

**Command bar**
- Linear pattern. Trigger ⌘K. Floating panel, `--surface` fill, 1px `--border-strong`, radius 12, max-width 640px. Mono input. Result rows in 14px Inter with 12px mono shortcut hints right-aligned.

**Keyboard hints**
- Linear `kbd` style: mono characters, 11px, `--bg-alt` background, 4px radius, 1px `--border`.

**Statement / receipt surface**
- Mercury editorial mode: 720px max width, Arcadia Display heading, 16px body, generous vertical rhythm (96px section breaks).

## 5. Layout Principles

Two modes. Page-type dictates.

**App / dashboard mode (Linear discipline)**
- 1280px max app shell, 240px persistent sidebar, content right of it.
- 24px gutter, 12-column.
- 4px base. 4 / 8 / 12 / 16 / 24 / 32 / 48.
- Dense. Tables breathe through hairlines, not padding.

**Marketing / statement mode (Mercury restraint)**
- 1080px max, 24px gutter.
- Reading column 720px on long-form (statements, agreements, blog).
- 96px section breaks. Vertical rhythm earns the trust.

## 6. Depth & Elevation

Flat. Depth comes from cream surface tone shifts (`--bg-alt` lift from `--bg`, `--surface` white over both) and 1px hairline borders. Both parents agree here.

Shadows reserved for floating affordances only:
- Modals / command bar: `0 12px 32px rgba(42,41,36,0.10)` (Mercury warmth).
- Popovers / dropdowns: `0 4px 12px rgba(42,41,36,0.06)`.

Never on cards, tiles, buttons, or table rows.

## 7. Do's and Don'ts

**Do**
- Tabular numerals on every money figure, every chart label, every table cell.
- Use indigo for one CTA per viewport — pair with cream secondary, never two saturated buttons.
- Pick app-mode or marketing-mode per page; don't blend within a page.
- Use Linear's command bar pattern (⌘K) on every app surface — muscle memory matters.
- Cream-on-coal for dark mode, never pitch black.

**Don't**
- Use Linear purple — replaced by Mercury indigo for fintech trust.
- Set transaction tables in proportional figures.
- Apply pill-radius buttons inside dashboard tables.
- Add card shadows or hover lift.
- Use Arcadia Display below 36px (reads decorative, not functional).
- Introduce a second saturated accent for "balance up" or "alerts" — use warm-gray hierarchy + signal colors only.

## 8. Responsive Behavior

- App shell: sidebar collapses to icon rail at 1024px, full drawer at 768px.
- Dashboard tables become stacked cards below 768px, balance + label + delta per card.
- Marketing display serif scales 72 → 48 → 36.
- Statement reading column padding-only below 720px, body holds at 16px.
- Command bar full-width sheet on mobile.

## 9. Agent Prompt Guide

Bias: cream warm canvas, Mercury indigo as the only saturated color, Linear-tight 4px base + 14px Inter body in app surfaces, Arcadia tabular numerals on every money figure, hairline 1px borders for depth, command bar (⌘K) on every app screen, dual-mode layout (app vs marketing), pill buttons in marketing only, sharp-radius buttons in app.

Reject: Linear purple, pill radius inside tables, proportional figures on money, drop shadows on cards or tiles, second saturated accent, Arcadia in app UI controls, pure white surfaces, glass / blur, hover lift, gradients of any kind.

## Creative Tensions (documented for team)

- **Density vs warmth.** Linear wants every pixel earning; Mercury wants the page to breathe. Resolution: app-mode picks Linear, marketing-mode picks Mercury, never one inside the other on the same surface.
- **Button radius mismatch.** Mercury's pill CTAs feel premium in marketing but wrong inside a dashboard table. Sharp radius wins inside the app shell; pill wins in marketing — enforce by surface, not by component.
- **Indigo vs purple.** Indigo and Linear purple sit close on the wheel. Designers will reach for purple from muscle memory. Token-lock indigo and remove purple from the swatch library.
- **Tabular numerals everywhere.** Even non-money tables (counts, percentages) must use tabular. The discipline reads as fintech-grade — break it and the trust drops.

## Parent-brand DNA

Tokens traced:
- From Mercury: 26 (cream surface palette, warm-gray ink ramp, indigo accent + hover + soft, signal palette, Arcadia Display, Arcadia tabular numerals, pill button radius for marketing, sidebar persistent at 240px, account tile pattern, statement reading column 720px, modal shadow tone, dark-mode warmth, hairline borders on cream)
- From Linear: 21 (Inter UI body, Berkeley Mono, 4px base scale, tight 36px row height, command bar ⌘K pattern, kbd hint style, sharp 6px button radius, app shell 1280px, 12-column 24px gutter, hover row pattern, sticky table headers, dark-mode density, eyebrow header treatment)

Net DNA: Mercury 55% · Linear 45%.
