# Mercury — Banking Editorial Warmth

Reference DESIGN.md for fintech that wants to feel calm and considered, not chrome-and-glass cold. Cream canvas, indigo action, dashboard density that still reads like editorial.

## 1. Visual Theme & Atmosphere

Banking trust through editorial restraint. The page is paper, not plastic. Cream backgrounds, warm-gray ink, one indigo CTA. Information density borrows from Linear; tone borrows from a financial broadsheet. Numbers are legible, surfaces are quiet, the brand lets the data stand.

Mood: trustworthy, deliberate, modern, unhurried.

## 2. Color Palette & Roles

```
--bg-primary:      #f6f5f2   /* warm canvas, page */
--bg-secondary:    #ebe8e0   /* surface lift */
--bg-tertiary:     #ded9ca   /* tonal divider, secondary CTA */
--surface:         #ffffff   /* card, table */
--text-primary:    #2a2924   /* ink */
--text-secondary:  #5a5548   /* warm gray */
--text-muted:      #8a8478
--accent:          #5266eb   /* indigo, primary CTA + link */
--accent-hover:    #4255d4
--border:          #ded9ca
--border-strong:   #c9c3b3
--success:         #2f7d57
--warning:         #c98a42
--danger:          #b54a3a
```

Rule: indigo is the only saturated color on the page. Use it for primary action and link underline. Warm grays do everything else.

## 3. Typography Rules

- **Headlines:** `Arcadia Display`, fallback `Tiempos Headline`, `Iowan Old Style`, `Georgia`. Weight 400. Letter-spacing −1%.
- **Body + UI:** `Arcadia`, fallback `Inter`, system-ui. Weight 400/500. Line-height 1.5.
- **Numerals:** Arcadia tabular variant on every account balance, transaction row, chart label. Never proportional figures on money.
- **Mono:** `IBM Plex Mono` for transaction IDs and code.

Scale: 13 / 14 / 16 / 18 / 22 / 28 / 36 / 48 / 72.

## 4. Component Stylings

**Buttons**
- Primary: indigo fill, white text, full pill (radius 999), padding 10/20, weight 500. No shadow.
- Secondary: `--bg-tertiary` fill, ink text, full pill. Hover: `--border-strong`.
- Ghost: ink text, indigo on hover.

**Cards**
- Surface white on `--bg-primary`, 1px `--border`, radius 8px. No shadow.
- Account cards: balance in 36px tabular, label in 13px uppercase eyebrow.

**Inputs**
- Pill shape, 1px `--border`, padding 10/16. Focus: 2px indigo ring, 2px offset.

**Tables**
- Tabular numerals, hairline `--border` between rows, sticky header in 12px uppercase eyebrow on `--bg-secondary`.

## 5. Layout Principles

- App shell 1280px max, 24px gutter.
- Marketing pages 1080px max, generous vertical rhythm.
- 4px base. 4 / 8 / 12 / 16 / 24 / 32 / 48 / 96.
- Sidebar persistent at 240px, content right of it.

## 6. Depth & Elevation

Flat. Depth from cream tone shifts and 1px borders. Modals only use shadow: `0 12px 32px rgba(42, 41, 36, 0.10)`. No card lift, no neumorphism.

## 7. Do's and Don'ts

**Do**
- Tabular figures everywhere money appears.
- Pair indigo CTA with a tonal cream secondary, never two saturated buttons.
- Let cream do the lifting between sections; resist boxing every group.

**Don't**
- Use crypto-startup gradients or neon.
- Set transaction tables in proportional figures.
- Introduce a second saturated accent for "balance" or "alerts". Use warm-gray hierarchy.
- Add card shadows to dashboard tiles.

## 8. Responsive Behavior

- Sidebar collapses to icon rail at 1024px, hidden behind hamburger below 768px.
- Tables become stacked KV cards below 640px, balance kept in 22px tabular.
- Marketing headlines scale 72 → 36 on mobile.

## 9. Agent Prompt Guide

Bias: cream background, warm-gray ink, single indigo accent, full-pill buttons, tabular numerals on every money surface, hairline tables, persistent left sidebar, editorial vertical rhythm.

Reject: pure-white SaaS canvas, multiple saturated accents, drop-shadowed cards, proportional figures on balances, gradient hero treatments, glass-morphism over financial data.
