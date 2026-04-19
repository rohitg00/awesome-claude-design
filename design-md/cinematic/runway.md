# RunwayML — Cinematic Dark

Reference DESIGN.md for film-grade dark UI, oversized type, motion-forward hero sections.

## 1. Visual Theme & Atmosphere

Cinematic dark. The page is a movie poster. Type is large, motion is present, media is the subject. Creator tools live here.

Mood: atmospheric, premium, kinetic.

## 2. Color Palette & Roles

```
--bg:              #000000
--bg-alt:          #0a0a0a
--surface:         #141414
--text:            #f5f5f5
--text-muted:      #a8a8a8
--text-dim:        #6a6a6a
--border:          #2a2a2a
--accent:          #ff2d8e   /* saturated magenta */
--accent-alt:      #00e5ff   /* electric cyan */
--gradient-1:      linear-gradient(135deg, #ff2d8e 0%, #a855f7 50%, #00e5ff 100%)
--gradient-warm:   linear-gradient(135deg, #ff6b35 0%, #f72585 100%)
```

Gradients are allowed here — and expected.

## 3. Typography Rules

- **Display:** custom grotesque. `PP Editorial New`, `Söhne Breit`, fallback `Inter Display`. Weight 400, tight tracking.
- **Body:** `Inter`, weight 400, 16–18px.
- **Mono:** `JetBrains Mono` for captions, timestamps, technical metadata.

Scale: 14 / 16 / 18 / 24 / 40 / 64 / 96 / 140. Go big.

Oversized display type is a feature, not excess.

## 4. Component Stylings

**Buttons**
- Primary: `--accent` fill, white text, radius 999 (pill), 12/24 padding.
- Secondary: transparent, 1px white border, white text.
- Hover: subtle scale(1.02) + 200ms ease-out. This is the one place lift is OK.

**Cards / media tiles**
- `--surface` bg, radius 12–16px, 1px `--border`.
- On hover: border becomes `--accent`, 300ms transition.
- Video previews autoplay muted on hover.

**Inputs**
- `--bg-alt` fill, radius 10px, 14px padding.
- Focus: 2px `--accent` ring with glow `0 0 16px rgba(255, 45, 142, 0.4)`.

**Nav**
- Fixed top. Transparent with backdrop-filter `blur(12px)` over scrolled content.

## 5. Layout Principles

- Full-bleed hero (100vw × 100vh common).
- 12-column grid, 32px gutter on desktop.
- Generous vertical whitespace between sections (120–160px).
- Media-first above the fold.

## 6. Depth & Elevation

Atmospheric. Soft glows around active elements. Backdrop blur for nav and modals. Drop shadows allowed but keep them deep and soft (`0 24px 64px rgba(0,0,0,0.6)`).

## 7. Do's and Don'ts

**Do**
- Use gradients on text, buttons, and hero backgrounds.
- Show motion: autoplay silent video, subtle parallax, morphing shapes.
- Oversize the hero headline to absurdity.

**Don't**
- Use light backgrounds. Ever. This is a dark system.
- Clutter with copy. Let media breathe.
- Add traditional sidebars or dense chrome.

## 8. Responsive Behavior

- Hero headlines scale 140 → 48 on mobile.
- Media grids collapse to single column below 768px.
- Autoplay disabled on mobile (bandwidth respect).

## 9. Agent Prompt Guide

Bias: pure black canvas, magenta/cyan gradients, oversized display type, pill buttons, media hero, blur-backed nav, generous whitespace between full-bleed sections.

Reject: light mode variants, dense info layouts, 16px headlines, conventional SaaS card grids.
