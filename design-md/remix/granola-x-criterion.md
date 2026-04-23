# Granola × Criterion — Premium Notes With Gravitas

Remix. Granola's warm cream + frosted glass + Criterion Collection's film-archive editorial rigor. For premium consumer apps that want to feel like a curated library, not a productivity tool.

## Parent DNA: Granola 55% · Criterion 45%

## 1. Visual Theme & Atmosphere

Granola sets the mood — warm off-white surface, soft glass on hover, generous breathing room. Criterion brings the chrome — numbered editions, monospace catalog labels, restrained spine-of-book typography, dense metadata blocks.

The result is a notetaker that reads like the Criterion Channel's library page. Cream paper, archival labels, single accent.

Mood: considered, archival, quietly premium.

## 2. Color Palette & Roles

```
/* base from Granola — warm cream paper */
--bg:              #faf8f2
--bg-alt:          #f4f0e6
--surface:         #ece6d5
--surface-glass:   rgba(255,253,247,0.72)
--text:            #1a1614
--text-muted:      #5c544a
--text-dim:        #8a8378
--border:          #e0d8c4
--border-strong:   #c8bea4

/* accent from Criterion — single archival red */
--accent:          #b32418
--accent-hover:    #931a10
--accent-soft:     #f4d6d2

/* dark mirror — Criterion spine-black */
--bg-dark:         #14110d
--bg-dark-alt:     #1f1b15
--surface-dark:    #2a251d
--text-dark:       #f4f0e6
--text-dark-muted: #b8ad97
--border-dark:     #3a3328
```

Arbitration: Granola's cream wins all surfaces — Criterion's pure white would lose the archival warmth. Criterion red replaces Granola's softer brand pink as the single accent. One accent, used like a librarian's stamp.

## 3. Typography Rules

- **Display / h1 / catalog heads:** Editorial serif (e.g. Tiempos Headline, Lyon Display) at 36px+, weight 500.
- **h2–h4 + body:** Tiempos Text or Lyon Text, weight 400 / 500. Body sits at 17/26.
- **Catalog labels + numerals + edition numbers:** GT America Mono (Criterion-adjacent), 12px, 1px tracking.
- **UI controls + chrome:** same serif body, no separate sans.

Scale: Granola's editorial ramp. 12 / 13 / 15 / 17 / 20 / 24 / 32 / 44 / 64.

Mono fires only on metadata blocks — edition number, recorded date, file size, catalog tag. Never in body.

Arbitration: Granola's warm sans body would read too soft against Criterion chrome. Lyon / Tiempos Text wins for body. Criterion's all-caps catalog labels stay — they're the spine.

## 4. Component Stylings

**Note card / catalog entry**
- `--bg-alt` fill, 1px `--border`, radius 6, no shadow.
- Top-row metadata strip in mono 12px: edition number, date, duration, tags. Spaced like a Criterion spine.
- Title in serif 24px below the strip.
- Hover: `--surface-glass` fill, backdrop-blur 12px. Granola's signature glass move.

**Button (primary)**
- Serif body, weight 500. Radius 4 (Criterion-tighter than Granola's pill).
- Fill `--accent`, text `--bg`. Padding 10/18.

**Button (secondary)**
- Transparent fill, 1px `--border`, `--text` color. Same geometry.

**Input**
- 1px `--border`, radius 4, padding 10/14, serif body.
- Focus: 2px `--accent` ring, 2px offset. No glow.

**Section heading**
- Mono catalog label above (12px, 1.5px tracking, `--text-muted`).
- Serif h2 below (32px, weight 500).
- 1px `--border-strong` rule under the pair, 16px below.

## 5. Layout Principles

- App: 1240px max, 32px gutter, 12-column.
- Reading / single-note: 680px column, centered.
- Catalog grid: 4 columns desktop, 2 columns tablet, 1 column mobile.
- 8px base. 8 / 16 / 24 / 32 / 48 / 64 / 96.

Granola's vertical rhythm holds. Criterion's contribution is the metadata strip above every card — every entry has a spine.

## 6. Depth & Elevation

Two-tier depth.

- Surfaces: flat, border-based. Granola's pattern.
- Hover / active: `--surface-glass` with `backdrop-filter: blur(12px) saturate(1.1)`. Granola's move.
- No shadows except modals (`0 16px 48px rgba(26,22,20,0.16)`).

Criterion contributes flatness — print-stock has no elevation. Granola contributes the glass moment. They alternate, never compose.

## 7. Do's and Don'ts

**Do**
- Lead every catalog entry with a mono metadata strip.
- Use the archival red for one element per viewport — primary CTA, current-edition badge, or active filter.
- Apply glass only on hover / active, never as a default surface.
- Keep body in serif — sans would break the library mood.

**Don't**
- Use the red for body links or secondary buttons.
- Stack two cards in glass mode simultaneously.
- Drop sans into UI controls.
- Add categorical color — this design is monochrome plus one red.

## 8. Responsive Behavior

- Catalog grid 4 → 2 → 1 column.
- Reading column padding-only below 720px.
- Metadata strip wraps to two lines at < 480px; mono shrinks to 11px.
- Glass hover converts to tap-flash on touch devices.

## 9. Agent Prompt Guide

Bias: warm cream surfaces, serif body + UI, mono metadata strips above every card, archival red as the single accent, glass-on-hover only, 8px base grid, catalog labels in 12px small caps mono.

Reject: pure white backgrounds, sans-serif body, multi-color accent palettes, default-state glass surfaces, drop shadows on cards, button radius > 6, abandoning the metadata strip on cards.

## Creative Tensions (documented for team)

- **Warmth vs rigor.** Granola wants softness; Criterion wants chrome. Resolution: Granola owns surface color and hover glass; Criterion owns typography hierarchy and metadata pattern.
- **Glass on cream.** Backdrop blur over warm paper can muddy the read. Cap blur at 12px and saturate at 1.1 — anything more loses the cream signature.
- **Serif UI legibility.** Serif body in form controls fights modern muscle memory. Test inputs at 15px minimum.

## Parent-brand DNA

Tokens traced:
- From Granola: 22 (cream surface palette, glass hover, warm dark mirror, 8px base, 1240px shell, hover-blur depth, soft border palette, generous vertical rhythm, single-column reading mode)
- From Criterion: 18 (archival red accent, mono catalog labels, metadata strip pattern, serif body + UI, 4px button radius, flat depth, spine-style section dividers, edition-number numerals, 1.5px label tracking)

Net DNA: Granola 55% · Criterion 45%.
