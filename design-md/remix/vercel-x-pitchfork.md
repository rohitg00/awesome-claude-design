# Vercel × Pitchfork — Editorial Docs With An Opinion

Remix. Vercel's grayscale-only restraint + Pitchfork's `#ff5d1f` orange and editorial serif. For docs, changelogs, and developer-marketing pages that want to read like a magazine review without losing technical credibility.

## Parent DNA: Vercel 60% · Pitchfork 40%

## 1. Visual Theme & Atmosphere

Vercel's chrome holds the page — single grayscale ramp, Geist everywhere, sharp grid. Pitchfork's contribution is editorial confidence: oversized review-style headlines, an orange that punctuates pull-quotes and section markers, and a willingness to let a paragraph run.

The result reads like a Pitchfork feature about a Vercel deploy. Cold neutrals, hot opinion.

Mood: opinionated, calm, technically literate.

## 2. Color Palette & Roles

```
/* grayscale ramp from Vercel — single source */
--bg:              #ffffff
--bg-alt:          #fafafa
--surface:         #f4f4f5
--text:            #000000
--text-muted:      #52525b
--text-dim:        #a1a1aa
--border:          #e4e4e7
--border-strong:   #d4d4d8

/* dark mirror */
--bg-dark:         #000000
--bg-dark-alt:     #0a0a0a
--surface-dark:    #18181b
--text-dark:       #ffffff
--text-dark-muted: #a1a1aa
--border-dark:     #27272a

/* sole accent from Pitchfork */
--accent:          #ff5d1f
--accent-hover:    #e64a0e
--accent-soft:     #ffead9
```

Arbitration: Vercel's monochrome wins everything except the single accent slot. Pitchfork orange replaces every place Vercel would otherwise reach for a blue / green / purple hint — section markers, link hover, pull-quote rule, code-fence caption. One color, used with restraint.

## 3. Typography Rules

- **Display / h1 / review-style heads:** Tiempos Headline (Pitchfork-adjacent serif) at 56px+, weight 600.
- **h2–h6 + body + UI:** Geist Sans (Vercel), weights 400 / 500 / 600.
- **Code + numerals:** Geist Mono (Vercel).

Scale: Vercel's tight ramp extended at the top for editorial heads. 12 / 14 / 16 / 18 / 20 / 24 / 32 / 48 / 64 / 88.

Serif fires above 48px only. Below that, Geist holds — docs density requires it.

Arbitration: Pitchfork's all-serif body would collapse code-block legibility. Geist body wins. Pitchfork serif gets the marquee slot — h1 and review-style callouts only.

## 4. Component Stylings

**Button (primary)**
- Vercel geometry: radius 6, padding 8/14, weight 500.
- Fill `--text` (black), text `--bg` (white). Pitchfork orange reserved for links, not CTAs.

**Button (secondary)**
- Transparent fill, 1px `--border`, `--text` color.

**Card**
- Vercel pattern: `--bg-alt` fill, 1px `--border`, radius 8, no shadow.
- Hover: border to `--border-strong`. Never a colored border on hover.

**Input**
- Vercel: 1px border, radius 6, padding 8/12.
- Focus: 2px `--accent` ring, 2px offset.

**Pull-quote / review callout**
- Tiempos at 28px, weight 500, italic optional.
- 4px left rule in `--accent`. 24px left padding. Quote sits in its own 8/16 grid cell.

**Section marker**
- Small caps, 12px Geist, `--accent` color, 1px tracking. Pitchfork-style "REVIEW", "BENCHMARK", "CHANGELOG" labels above each section heading.

## 5. Layout Principles

- Marketing / changelog: 1180px max, 24px gutter, 12-column.
- Long-form article: 720px reading column, centered.
- Docs: Vercel's 256px sidebar + 720px article + 240px on-this-page rail.
- 4px base. 4 / 8 / 12 / 16 / 24 / 32 / 48 / 64 / 96.

Magazine move: every long-form page opens with a full-width title block — section marker, serif h1, dek paragraph, byline rule — then drops back into Vercel's docs grid.

## 6. Depth & Elevation

Flat. Border-based depth on light, alpha-border on dark. Shadows only on popovers (`0 2px 8px rgba(0,0,0,0.04)` light, `0 12px 32px rgba(0,0,0,0.6)` dark).

Both parents agree — print-flat editorial meets developer-tool minimalism. No conflict.

## 7. Do's and Don'ts

**Do**
- Use Tiempos at 48px+ only.
- Reserve orange for links, section markers, and pull-quote rules.
- Open every long-form page with a full-width title block.
- Keep all body and UI in Geist for density.

**Don't**
- Use orange as a button fill.
- Add a second accent color.
- Drop serif into UI controls or table cells.
- Add drop shadows on cards.

## 8. Responsive Behavior

- Serif h1 scales 88 → 56 → 40.
- Reading column stays 720px until viewport < 768px, then padding-only.
- Docs sidebar collapses to drawer at 1024px; on-this-page rail hides at 1280px.
- Section markers stay 12px at all breakpoints — hierarchy comes from the serif, not the marker.

## 9. Agent Prompt Guide

Bias: single grayscale ramp + Geist UI everywhere, Tiempos serif at 48px+ for editorial heads, `#ff5d1f` orange used only for links / section markers / pull-quote rules, full-width article title blocks, Vercel docs grid below the fold.

Reject: orange button fills, second accent colors, serif in body or UI, drop shadows, colored hover borders on cards, abandoning the docs grid for full-bleed art on technical pages.

## Creative Tensions (documented for team)

- **Editorial heat vs technical cool.** Pitchfork orange wants to dominate; Vercel restraint wants to bury it. Resolution: orange appears at most twice per viewport, and never on a CTA.
- **Serif legibility floor.** Below 48px the serif reads decorative against Geist body. Enforce a hard size floor in tokens — no exceptions, even for h2.

## Parent-brand DNA

Tokens traced:
- From Vercel: 26 (grayscale ramp light + dark, Geist Sans + Mono, button geometry, card pattern, input pattern, docs grid, 4px base scale, flat depth, focus ring geometry, sidebar shell)
- From Pitchfork: 17 (orange accent, Tiempos display, pull-quote rule, section markers, full-width title block, dek paragraph pattern, byline rule, italic pull-quote treatment)

Net DNA: Vercel 60% · Pitchfork 40%.
