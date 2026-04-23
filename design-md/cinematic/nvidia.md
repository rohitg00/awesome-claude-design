# NVIDIA — Cinematic Compute

Reference DESIGN.md for GPU-vendor cinematic: chrome-black canvas, signature green action, video-led hero, hard-edged grotesque headlines.

## 1. Visual Theme & Atmosphere

Cinematic compute. The page reads like a hardware launch reel — black canvas, full-bleed video of die shots and rendered scenes, green CTA punching through. Type stays sharp, narrow, almost industrial. There is exactly one accent and it is the green; everything else is grayscale.

Mood: high-energy, precision-engineered, motion-forward.

## 2. Color Palette & Roles

```
--bg:              #000000   /* canvas */
--bg-alt:          #0d0d0d
--surface:         #1a1a1a
--surface-2:       #2a2a2a
--text:            #ffffff
--text-muted:      #b8b8b8
--text-dim:        #767676
--border:          #333333
--border-strong:   #4d4d4d

--accent:          #76b900   /* signature green — primary CTA + brand */
--accent-hover:    #8fd400
--accent-deep:     #5a8d00   /* hover-pressed, dark variants */
--accent-soft:     #c9e892   /* tinted callouts only */

--secondary:       #10b1fb   /* developer / data accent, sparingly */
--success:         #76b900
--warning:         #ffb800
--danger:          #d13438
```

Rule: green and only green for primary action and brand mark. Cyan `--secondary` is reserved for developer surfaces (CUDA, RAPIDS, NeMo). Never gradient between the two; they are not partners.

## 3. Typography Rules

- **Display + headlines:** `NVIDIA Sans` (NALA), fallback `Helvetica Neue`, `Arial`, system. Weight 500–700, tight tracking (−1% at large sizes).
- **Body:** NVIDIA Sans regular, weight 400, 16–18px, line-height 1.5.
- **UI labels:** NVIDIA Sans weight 500, 12–14px, uppercase only for category eyebrows (tracked +6%).
- **Numerals:** tabular figures on spec tables, benchmark charts, pricing.
- **Mono:** `JetBrains Mono`, fallback `SF Mono`. Used for code samples, command snippets, telemetry.

Scale: 12 / 14 / 16 / 18 / 24 / 32 / 48 / 72 / 96 / 128.

Display headlines go big. 96px and up for product launches.

## 4. Component Stylings

**Buttons**
- Primary: `--accent` fill, black text, radius 4px, padding 12/24, weight 600. Hover: `--accent-hover`. No lift, no scale.
- Secondary: transparent fill, 1px white border, white text. Hover: 1px `--accent` border.
- Tertiary / link: white text, green underline on hover.
- Destructive: `--danger` fill, white text, only on confirm modals.

**Cards / product tiles**
- `--surface` fill, 1px `--border`, radius 4px. Padding 24.
- Hero product cards run full-bleed images with text overlay; gradient scrim `linear-gradient(180deg, transparent 0%, rgba(0,0,0,0.8) 100%)` for legibility.
- Hover: 1px `--accent` border, 200ms ease. No scale, no glow.

**Inputs**
- `--bg-alt` fill, 1px `--border-strong`, radius 4px, padding 10/14. Focus: 2px `--accent` ring with 1px offset.

**Nav**
- Fixed top, `--bg` fill with 90% opacity and 8px backdrop blur. White links, green underline on active. Mega-menu opens flush, full-width, dark.

**Video hero**
- Autoplay muted, 100vw × 80vh minimum. Loop. Subtle bottom scrim for headline legibility. Reduced-motion users get a static still frame.

## 5. Layout Principles

- Full-bleed hero (100vw, 80–100vh).
- 1440px max for content sections, 32px gutter, 12-column.
- 8px base. 8 / 16 / 24 / 32 / 48 / 64 / 96 / 128.
- Generous vertical whitespace between sections (96–128px).
- Spec tables break grid and run dense.

## 6. Depth & Elevation

Flat surfaces with hard borders. Depth comes from:
- Surface tonal shift (`--bg → --surface → --surface-2`)
- 1px `--border` and `--border-strong`
- Video and image hierarchy

Modals get `0 24px 64px rgba(0, 0, 0, 0.72)` over a 70% black scrim. No soft glows on cards. Reserve glow effects for chart highlights only.

## 7. Do's and Don'ts

**Do**
- Open with full-bleed video. Die shots, rendered scenes, lab footage, robotaxi POV.
- Oversize the launch headline. 96px+.
- Lock the green to action and brand; let chrome stay grayscale.
- Use tabular numerals for benchmark deltas (1.7×, 2.5×, +43%).
- Keep corners at 4px. Hard edges read as engineered.

**Don't**
- Mix green and cyan in the same component.
- Use light backgrounds. NVIDIA marketing is dark by default.
- Soften corners past 8px.
- Add purple gradients, glassmorphism, or pastel accents.
- Replace video hero with stock photography.

## 8. Responsive Behavior

- Hero video remains full-bleed; headline scales 128 → 40 on mobile.
- Mega-menu collapses to drawer at 1024px, full-screen overlay below 768px.
- Spec tables become horizontally scrollable below 640px (preserve density, no stacking).
- Autoplay disabled on mobile per bandwidth respect; static poster frame substitutes.
- Body type holds 16px on mobile.

## 9. Agent Prompt Guide

Bias: black `#000000` canvas, signature green `#76b900` reserved for primary action and brand mark only, NVIDIA Sans / Helvetica Neue tight grotesque, oversized display headlines (96px+), full-bleed video hero, 4px radii, tabular numerals on benchmark tables, mega-menu nav with backdrop blur.

Reject: light-mode marketing pages, multi-accent palettes, soft pastel gradients, glassmorphism, rounded-pill buttons, hero stock photography in place of video, scaled hover lifts, decorative illustration in chrome.
