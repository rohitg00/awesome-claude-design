# The Verge — Neon Brutalist

Reference DESIGN.md for hard-edge editorial publishing with saturated single-hue accent.

## 1. Visual Theme & Atmosphere

Neon brutalist. Hard edges, deliberate-ugly type mixing, oversized numerals, a single saturated hue doing all the heavy lifting. Confident, loud, built to be remembered.

Mood: decisive, opinionated, zero apology.

## 2. Color Palette & Roles

```
--bg:              #ffffff
--bg-inverse:      #000000
--text:            #000000
--text-inverse:    #ffffff
--accent:          #ff6600
--accent-hover:    #e55c00
--border:          #000000
--rule:            #000000
```

One accent. One neutral pair. That's it.

## 3. Typography Rules

- **Display:** `Polysans Median`, fallback `Neue Haas Grotesk Display`. Weight 700. Letter-spacing −2%.
- **Editorial body:** `Polysans Neutral`, fallback `Söhne`.
- **Pull quotes / callouts:** editorial serif (`GT Super`, `Portrait`), italics allowed.
- **Numerals / dates:** oversized, tracked wide, tabular.

Scale: 13 / 16 / 20 / 28 / 44 / 68 / 108 / 168. Go enormous for headlines.

Mix sans and serif aggressively — the tension is the aesthetic.

## 4. Component Stylings

**Buttons**
- Primary: `--accent` fill, black text, radius 0, padding 14/24, weight 700, uppercase.
- Hover: black fill, white text. Snaps instantly, no transition.

**Cards / articles**
- No card. Rules separate items — 2px black horizontal lines.
- Category tag above headline in uppercase `--accent` color.

**Nav**
- Full-width black bar, white logo, orange active indicator.
- Category links in uppercase, tracked.

**Images**
- Cropped tight, edge-to-edge. No rounded corners. Captions in mono.

## 5. Layout Principles

- Full-bleed content sections.
- 12-column grid with asymmetric article layouts (2-col + 1-col pull).
- 2px rules everywhere instead of whitespace.
- Oversized numerals as page anchors (issue numbers, dates).

## 6. Depth & Elevation

Flat. Zero shadows. Depth comes from 2px rules, inversion (black on white → white on black), and size contrast.

## 7. Do's and Don'ts

**Do**
- Mix serif and sans in the same headline.
- Use oversized numerals as graphic elements.
- Invert sections aggressively (white → black → orange).

**Don't**
- Round any corner.
- Introduce a secondary accent.
- Soften with drop shadows or blur.
- Use Inter anywhere (it's too neutral).

## 8. Responsive Behavior

- Headlines scale 168 → 48 on mobile.
- 2px rules remain 2px.
- Asymmetric layouts collapse to single column, rules stay.

## 9. Agent Prompt Guide

Bias: black + white + one saturated hue, oversized headlines, 2px rules, aggressive sans/serif mixing, 0px radius, full-bleed sections.

Reject: rounded corners, soft shadows, pastel palettes, Inter as display face, glassmorphism.
