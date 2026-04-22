# Warp × Sentry — Developer Dashboard With Warmth

Remix. Warp's mono grid + Sentry's lilac purple. Dashboards that don't read as funeral parlors.

## Parent DNA: Warp 60% · Sentry 40%

## 1. Visual Theme & Atmosphere

Pro-tool density meets emotional color. Warp's deep navy surface stack stays — it's where engineers live. Sentry's lilac replaces Warp's teal at the action layer because lilac softens severity without losing technical seriousness. Coral remains as warning.

Mood: technical, calm, persistent.

## 2. Color Palette & Roles

```
/* surfaces from Warp */
--bg:              #0b0d14
--bg-alt:          #11141d
--surface:         #161a25
--surface-2:       #1e2331
--text:            #f1f1f4
--text-muted:      #9aa1b3
--text-dim:        #5f6580
--border:          #232838
--border-strong:   #2e3447

/* accent from Sentry — replaces Warp's teal */
--accent:          #7553f6   /* Sentry-adjacent lilac, brighter for dark bg */
--accent-hover:    #8967ff
--accent-soft:     #584774   /* used for empty-state illustrations */

/* state */
--warning:         #ff7a59   /* Warp coral retained */
--danger:          #f6827d   /* Sentry pink-coral for alerts */
--success:         #5ee78a   /* Warp green retained */
```

Arbitration: Warp's teal lost — too cold next to Sentry's pink-warning state, the two clashed at error/action proximity. Sentry lilac wins because it harmonizes with Warp's coral instead of fighting it. Sentry's `#362d59` background lost to Warp's deeper `#0b0d14` for terminal-feel preservation.

## 3. Typography Rules

- **UI:** `Roobert` (from Warp).
- **Headlines:** `Rubik` weight 600 (from Sentry) — used at 24px+ only, gives marketing pages personality without dominating dashboards.
- **Code + numerals:** `JetBrains Mono` (Warp).

Scale: Warp's tight ramp. 11 / 12 / 13 / 15 / 17 / 20 / 26 / 34 / 44 / 56.

Tabular numerals globally on metrics.

Arbitration: Sentry's Rubik would feel rounded-soft if used at small UI sizes. Cap Rubik to display-only.

## 4. Component Stylings

**Buttons**
- Primary: `--accent` (lilac) fill, `#0b0d14` text, radius 8, padding 8/14, weight 500.
- Secondary: `--surface-2` fill, `--text` color, `--border-strong` outline.
- Destructive: `--danger` fill, `#0b0d14` text.

**Cards / blocks**
- Warp pattern preserved: `--surface` fill, 1px `--border`, radius 10.
- Empty states use `--accent-soft` (Sentry lilac-grey) illustration tint — Sentry's signature move.

**Inputs**
- Warp geometry: `--bg-alt` fill, 1px `--border-strong`, radius 8.
- Focus: 2px `--accent` lilac ring.

**Alert / issue rows**
- Borrow Sentry's pattern: 4px left border in `--warning` or `--danger`, `--surface` fill.
- Severity icon left, title middle, count right (mono, tabular).

## 5. Layout Principles

Warp's full-width app shell with persistent sidebar wins — Sentry's narrower 1280 marketing layout reserved for landing page only.

- App: full-width, sidebar 240px, main content fluid.
- Marketing: 1280 max, 24px gutter, 12-col.
- 4px base. 4/8/12/16/24/32/48 scale.

## 6. Depth & Elevation

Warp's layered surfaces stay. `bg → surface → surface-2 → modal`. Modals add `0 24px 48px rgba(0,0,0,0.55)`.

No conflict with Sentry — both rejected drop shadows on cards.

## 7. Do's and Don'ts

**Do**
- Use lilac as the only chromatic action color.
- Use Sentry's left-border alert-row pattern wherever a list of issues/incidents appears.
- Render numbers in JetBrains Mono tabular.

**Don't**
- Re-introduce Warp's teal. Lilac won; honor it.
- Use Rubik below 24px — kills technical density.
- Add a third chromatic accent.
- Use `--accent-soft` for action — it's reserved for illustration/empty-state only.

## 8. Responsive Behavior

- Sidebar collapses to icon rail at 1024px, full overlay at 768px.
- Issue rows stack severity-icon + title at 640px, count moves to row two.
- Marketing hero scales 56 → 34 → 26.

## 9. Agent Prompt Guide

Bias: Warp navy surface stack, Sentry lilac for action only, Rubik display 24px+, JetBrains Mono tabular numerals, left-border alert pattern, no teal anywhere.

Reject: Warp's teal accent, Rubik in UI controls, drop shadows, light themes, mixing lilac with a second chromatic accent.

## Creative Tensions (documented for team)

- **Action-color identity loss.** Warp users associate the brand with teal. Removing it for lilac is a real cost — the dashboard no longer reads "Warp." Net: marketing pages should still use Warp teal in hero illustration so brand recognition survives; product chrome stays lilac.
- **Severity adjacency.** Sentry's pink-coral danger and Warp's coral warning sit close on the wheel. Always order danger > warning in lists so the warmer hue dominates upward visual flow.

## Parent-brand DNA

Tokens traced:
- From Warp: 28 (surface stack, Roobert, JetBrains Mono, button geometry, kbd, sidebar layout, dark-only discipline, tabular numerals)
- From Sentry: 18 (lilac accent, Rubik display, alert-row left-border pattern, lilac-grey empty-state illustration tint, pink-coral danger, marketing 1280 max-width)

Net DNA: Warp 60% · Sentry 40%.
