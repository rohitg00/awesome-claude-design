# Tavus — Cinematic Conversational AI

Reference DESIGN.md for video-AI products that need to feel premium and human at once. Cream off-white canvas with deep ink contrast, one warm pink accent, oversized display serif intercut with a compact display grotesque.

## 1. Visual Theme & Atmosphere

Cinematic but not midnight-black. The brand sits on warm off-white paper, then drops into full-bleed video portraits that do the heavy lifting. Display type is large and editorial; pink is the heartbeat color that signals "the AI is alive". Every section reads like a film title card paired with a portrait still.

Mood: warm, premium, alive, slightly uncanny.

## 2. Color Palette & Roles

```
--bg-primary:      #f7f4ef   /* warm off-white canvas */
--bg-inverse:      #140206   /* near-black for cinematic sections */
--bg-surface:      #ffffff
--text-primary:    #140206
--text-on-dark:    #f7f4ef
--text-muted:      #6a5f5e
--accent:          #ff6183   /* warm pink, brand heartbeat */
--accent-hover:    #e84d6f
--accent-soft:     #ffd6df   /* tinted backgrounds, badges */
--support-green:   #0cb531   /* secondary action, positive state */
--border:          #e7e2da
--border-on-dark:  #2a1a1f
```

Rule: pink is always paired with either ink or off-white — never with green on the same surface. Green is reserved for "explore" / API-positive moments.

## 3. Typography Rules

- **Display:** `Perfectly Nineties`, fallback `Tiempos Headline`, `Georgia`. Weight 400. Used at 80–140px. This is the film-poster type.
- **Heading sans:** `FK Raster Grotesk Compact`, fallback `Söhne Breit`, `Inter Display`. Weight 500. Tight tracking. Used at 24–48px.
- **Body + UI:** `Suisse Intl`, fallback `Inter`. Weight 400/500. 16–22px body.
- **Mono:** `JetBrains Mono` for API examples and timestamps.

Scale: 14 / 16 / 18 / 22 / 34 / 48 / 64 / 88 / 140.

Mix the serif and the compact grotesque on the same page — that contrast is the brand.

## 4. Component Stylings

**Buttons**
- Primary: pink fill, ink text, radius 0 (sharp rectangle), 1px ink border, padding 12/24, weight 500. Sharp corners are deliberate.
- Secondary: green fill, ink text, sharp rectangle, 1px ink border.
- Ghost: ink text on cream, underline on hover, no fill.

**Video portraits**
- Full-bleed or framed in 1px ink border on cream, radius 0.
- Autoplay muted on desktop, click-to-play on mobile.
- Caption overlay: 13px Suisse, ink-on-cream, bottom-left, no scrim.

**Cards**
- Cream on white or white on cream — tonal step only. 1px `--border`, radius 0. Padding 24.

**Inputs**
- Sharp rectangle, 1px ink border, 12/16 padding. Focus: 2px pink ring, no offset.

**Nav**
- Fixed top, transparent over cream, shifts to ink-on-cream when scrolled. No backdrop blur.

## 5. Layout Principles

- 1320px max, 32px gutter.
- 8px base. 8 / 16 / 24 / 32 / 48 / 80 / 120.
- Sections alternate cream and full-bleed video. Whitespace around display type is non-negotiable: 120px above, 80px below.
- Asymmetric column splits (60/40 portrait + caption) over symmetric grids.

## 6. Depth & Elevation

Flat. Depth is film-grain, not shadow. Allowed: subtle 1px ink border on portraits, 1px hairline section dividers. Forbidden: drop shadows on cards, glow rings, layered gradients.

## 7. Do's and Don'ts

**Do**
- Mix the editorial serif (Perfectly Nineties) with the compact grotesque (FK Raster) on the same page.
- Frame video portraits in 1px ink and let them dominate the fold.
- Use sharp 0-radius corners — softness comes from type and color, not geometry.

**Don't**
- Switch to pure black backgrounds. The off-white cream is the brand differentiator from generic dark-mode AI.
- Round corners or apply pill buttons.
- Use pink and green in the same component — alternate by section.
- Add chat-bubble UI tropes around the portrait. The portrait is the interface.

## 8. Responsive Behavior

- Display serif scales 140 → 56 on mobile, retains weight 400.
- Video portraits become full-width single column below 768px.
- Nav collapses to hamburger below 768px; cream-on-cream menu, no overlay scrim.

## 9. Agent Prompt Guide

Bias: cream off-white canvas, ink contrast, oversized editorial serif paired with compact grotesque headings, sharp 0-radius components, single warm-pink accent, 1px-bordered video portraits dominating the fold.

Reject: pure-black cinematic dark mode, pill buttons, drop shadows on portraits, chat-bubble UI around the AI, multi-color gradients, glassmorphism, hero illustrations replacing the video.
