# Linear × Claude — Editorial SaaS with a Soul

Remix example. Linear's surgical density + Claude's warm editorial restraint. Inherits Linear geometry, swaps accent to terracotta, keeps Inter for UI but adds Tiempos for headlines.

## Parent DNA: Linear 55% · Claude 45%

## 1. Visual Theme & Atmosphere

Dashboard scan patterns meet long-form reading rhythm. Body reads like an editorial; UI feels like Linear. Terracotta punctuates — never dominates. Clients who say "like Linear but friendlier" land here.

Mood: precise, warm, quietly confident.

## 2. Color Palette & Roles

```
/* neutrals from Linear — cold whites for dashboard clarity */
--bg:              #ffffff
--bg-alt:          #fafafa
--surface:         #f4f4f5
--text:            #0f0f14
--text-muted:      #6b6b76
--text-dim:        #a0a0ab
--border:          #e4e4e7
--border-strong:   #d4d4d8

/* accent from Claude — warmth where Linear would go surgical */
--accent:          #c96442
--accent-hover:    #b55738
--accent-soft:     #e89268

/* dark mode inherits Linear's density discipline */
--bg-dark:         #0f0f14
--surface-dark:    #1a1a20
--text-dark:       #f5f5f5
```

Arbitration: Claude's `#f4f3ee` cream lost to Linear's `#ffffff` for dashboard scan. Claude's terracotta won over Linear's `#5e6ad2` purple — terracotta reads as emotional warmth, purple as tech-startup default.

## 3. Typography Rules

- **Display / h1 / h2:** Tiempos Headline, weight 500 (from Claude).
- **h3–h6, body, UI:** Inter, weights 400/500/600 (from Linear).
- **Mono:** Berkeley Mono (from Linear).

Scale: Linear's tight ramp. 11 / 13 / 14 / 16 / 18 / 22 / 28 / 36 / 48 / 64.

Tiempos activates only at 28px+. Anything smaller stays Inter for density.

Arbitration: Claude's warmer body serif would break dashboard scan. Inter stays. But Linear's all-Inter display felt cold for editorial surfaces — Tiempos lands at the top of the scale only.

## 4. Component Stylings

**Button (primary)**
- Geometry from Linear: radius 6, padding 8/14, weight 500.
- Color from Claude: `--accent` fill, cream-adjacent `#f5f5f5` text.

**Button (secondary)**
- `--surface` fill (Linear), `--text` color, `--border` outline.

**Card**
- Linear: `--bg-alt` fill, 1px `--border`, radius 8, no shadow.
- Hover: border shifts `--border-strong` (Linear's move, not Claude's).

**Input**
- Linear geometry: 1px border, radius 6, padding 8/12.
- Focus: 2px `--accent` ring (Claude's warm-accent focus), 2px offset.

**Keyboard hints**
- Linear's `kbd` style — mono characters, 11px, `--surface` background, 4px radius.

**Long-form article surfaces**
- Use Claude's layout principles here — 680px max, 18px body, generous vertical rhythm.
- Pull-quotes in Tiempos italic, `--accent-soft` left rule.

## 5. Layout Principles

Two modes. Team picks which applies per page.

**App / dashboard mode (Linear discipline)**
- Max 1200px, 24px gutter, 12-column.
- 4px base unit. Dense.

**Editorial / marketing mode (Claude restraint)**
- Max 680px for long-form, 1180px for app shells.
- Generous vertical rhythm. 96px section breaks.

## 6. Depth & Elevation

Flat by default. Border-based depth. Shadows reserved for popovers + dropdowns only (`0 2px 8px rgba(15, 15, 20, 0.04)`).

Both parents agreed here — no conflict.

## 7. Do's and Don'ts

**Do**
- Use Tiempos at 28px+ only.
- Rotate between app-mode and editorial-mode layouts by page type.
- Use terracotta as punctuation — one accent moment per viewport.
- Keep UI density Linear-tight.

**Don't**
- Mix purple and terracotta. Terracotta won; honor it.
- Use Tiempos below 22px (reads as decorative, not functional).
- Introduce drop shadows on cards.
- Switch to cream body (`#f4f3ee`) in dashboards.

## 8. Responsive Behavior

- App-mode collapses to Linear's mobile patterns (bottom nav, stacked tables).
- Editorial-mode keeps 18px body, serif h1 scales 64 → 36.

## 9. Agent Prompt Guide

Bias: Linear geometry everywhere, terracotta accent, Tiempos at display only, dual-mode layout (app vs editorial), 1px border depth.

Reject: Linear purple (replaced), cream dashboard backgrounds, Tiempos in UI controls, drop shadows on cards, over-generous whitespace in app mode.

## Creative Tensions (documented for team)

- **Density conflict.** Dashboards want Linear-dense, editorial wants Claude-generous. Arbitrate per page type — not per component.
- **Accent temperature.** Terracotta is noticeably warmer than Linear purple. Error states that were pink-adjacent now risk clashing. Danger is kept at Linear's `#ff6b6b`.

## Parent-brand DNA

Tokens traced:
- From Linear: 24 (background colors, scale, button geometry, card borders, kbd, dashboard layout, mono stack, dark mode discipline)
- From Claude: 18 (accent, Tiempos, pull-quote style, editorial-mode layout, warm error recovery, focus-ring color, 680px long-form max, micro-copy tone)

Net DNA: Linear 55% · Claude 45%.
