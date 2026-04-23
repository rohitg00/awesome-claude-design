# Notion × Duolingo — Friendly Education SaaS

Remix. Notion's warm neutral document surface + Duolingo's saturated greens, rounded corners, and tactile feedback. For learning platforms, courses, and education tools that want to feel like a serious workspace and a friendly tutor at once.

## Parent DNA: Notion 55% · Duolingo 45%

## 1. Visual Theme & Atmosphere

Notion sets the writing surface — warm white, charcoal text, generous reading column, restrained chrome. Duolingo brings encouragement — saturated leaf green for progress and CTAs, rounded geometry, tactile button affordances, streak / XP / progress affordances that gamify without infantilizing.

The result is a study app that feels like a Notion doc you can high-five.

Mood: focused, warm, encouraging.

## 2. Color Palette & Roles

```
/* document base from Notion */
--bg:              #ffffff
--bg-alt:          #fbfaf8
--surface:         #f1efea
--text:            #37352f
--text-muted:      #6f6b62
--text-dim:        #a09c92
--border:          #e9e7e2
--border-strong:   #d6d3cc

/* progress + CTA from Duolingo */
--accent:          #58cc02
--accent-hover:    #4cad00
--accent-deep:     #3d8a00
--accent-soft:     #e8f8d8

/* secondary signals from Duolingo */
--streak:          #ff9600
--danger:          #ff4b4b
--xp:              #1cb0f6

/* dark mode — softer than Notion's pitch dark */
--bg-dark:         #25241f
--surface-dark:    #322f29
--text-dark:       #f1efea
--border-dark:     #3e3a32
```

Arbitration: Notion's warm white wins all reading and document surfaces — Duolingo's white is too cold. Duolingo's leaf green replaces Notion's blue for progress and CTAs. Duolingo's orange / red / blue stay confined to streak, danger, and XP signals — never general UI.

## 3. Typography Rules

- **Display / h1:** Inter Display, weight 700, 40px+. Friendlier than Notion's Lyon serif default.
- **h2–h4:** Inter, weight 600 / 700.
- **Body:** Inter, weight 400, 16/26. Document-feel, not chat-feel.
- **UI labels + buttons + numerals:** Inter, weight 600. Never thin weights on CTAs.
- **XP / streak / score numerals:** Inter, weight 800, tabular.

Scale: Notion's reading ramp + Duolingo's heavier display weights. 12 / 14 / 16 / 18 / 20 / 24 / 32 / 40 / 56.

No serif. Both parents agreed sans wins — Notion's Lyon serif felt too literary for a learning context.

## 4. Component Stylings

**Button (primary CTA)**
- Duolingo geometry: radius 16, padding 14/24, weight 700.
- Fill `--accent`, text `#ffffff`, weight 700.
- Tactile bottom shadow: `0 4px 0 0 var(--accent-deep)`. Pressed state shifts to `0 0 0 0` and translateY(2px). Duolingo signature.

**Button (secondary)**
- Same geometry. Transparent fill, 2px `--border-strong`, `--text` color, weight 700.
- Bottom shadow: `0 4px 0 0 var(--border-strong)`. Same pressed behavior.

**Card / lesson tile**
- Notion pattern: `--bg-alt` fill, 1px `--border`, radius 12.
- Hover: `--surface` fill, 1px `--border-strong`. No tactile shadow on cards — only on buttons.

**Input**
- Notion: 1px `--border`, radius 8, padding 10/14.
- Focus: 2px `--accent` ring, 2px offset.

**Progress bar**
- Track: `--surface`, height 12, radius 999.
- Fill: `--accent`, radius 999. Inner highlight `rgba(255,255,255,0.32)` top 4px.

**Streak / XP badge**
- Pill, radius 999, padding 6/12, weight 700, mono numeral.
- Streak: `--streak` fill, white text. XP: `--xp` fill, white text.

**Document surface**
- Notion's reading column — 720px, 16px body, 1.6 line-height, callouts in `--bg-alt` with 1px `--border`.

## 5. Layout Principles

Two zones per page.

**Reading / lesson content**
- Notion: 720px max, centered, 16px body.

**Practice / exercise / dashboard**
- Duolingo: 480px centered card stack on desktop, full-width on mobile, generous 32px+ padding inside cards.

App shell: 1180px max, 240px nav rail, 8px base scale (8 / 16 / 24 / 32 / 48 / 64 / 96).

## 6. Depth & Elevation

Two depth modes.

- Document surfaces: flat, border-only. Notion discipline.
- Interactive controls (buttons, exercise tiles): tactile bottom-shadow depth. Duolingo's `0 4px 0 0` move.

Cards stay flat. Modals: `0 20px 48px rgba(55,53,47,0.18)`. No glass, no blur.

## 7. Do's and Don'ts

**Do**
- Reserve tactile bottom-shadow for buttons and exercise tiles only.
- Use leaf green for CTAs and progress, never decoration.
- Keep streak / XP / danger colors confined to their signal contexts.
- Body in Inter 16px, document-style line-height 1.6.

**Don't**
- Apply tactile shadow to cards — kills the document feel.
- Use Duolingo's owl mascot literally. Borrow the affordances, not the IP.
- Drop multiple categorical colors into general UI.
- Use serif body — broke the learning context.

## 8. Responsive Behavior

- Reading column padding-only below 768px.
- Practice card stack: full-width with 16px gutter on mobile.
- Nav rail collapses to bottom tab bar at 768px.
- Tactile button shadow scales to `0 3px 0 0` at < 480px.
- Streak / XP badges stay pill-shaped, shrink to 11px font.

## 9. Agent Prompt Guide

Bias: warm white document base, Inter throughout, leaf green for CTAs and progress only, tactile bottom-shadow on buttons (`0 4px 0 0` style), 720px reading column for lessons, 480px card stack for practice, streak / XP / danger colors confined to signal context, rounded radius 12–16 on interactive elements.

Reject: serif body, tactile shadows on cards, mascot illustrations of any kind, multi-color decoration, Notion's cold-white surfaces, button radius < 12, thin font weights on CTAs, glass / blur / drop shadows on cards.

## Creative Tensions (documented for team)

- **Friendly vs serious.** Duolingo can read as childish if pushed too far; Notion can read as cold if held too rigid. Resolution: Notion owns documents, Duolingo owns interactions — never mix on the same surface.
- **Tactile button on a Notion card.** Tempting and wrong. The tactile move is for things you press / answer / commit. Cards are for reading.
- **Color discipline.** Duolingo's full palette is loud. Confine to: green for go, orange for streak, red for wrong, blue for XP. Anything else is a regression.

## Parent-brand DNA

Tokens traced:
- From Notion: 22 (warm white surface palette, charcoal text ramp, 720px reading column, document callout pattern, 1px border depth, card radius 12, nav-rail shell, dark mode warm-not-pitch, soft border palette, generous reading line-height)
- From Duolingo: 18 (leaf green accent, tactile bottom-shadow buttons, button radius 16, weight 700 CTAs, progress bar pattern, streak / XP / danger signal colors, pill badges, exercise card stack, full-width mobile practice surface)

Net DNA: Notion 55% · Duolingo 45%.
