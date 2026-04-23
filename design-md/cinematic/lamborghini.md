# Lamborghini — Black Cathedral Gold

Reference DESIGN.md for hyper-luxury that needs to feel forged. True-black canvas, oversized LamboType nameplates at 120px+, hexagonal angle motifs, single warm-gold accent for primary actions, photography lit like a vault.

## 1. Visual Theme & Atmosphere

Black cathedral. The page is dark architecture — true `#000000` canvas, vehicles lit from below like sculpture, type carved into the screen at 120px. Geometry is angular: hex motifs in dividers, sharp 0-radius components, no soft edges anywhere. Gold appears as a single decisive accent on CTAs and active states. Reads like a Sant'Agata showroom at night.

Mood: forged, dramatic, exclusive, mechanical.

## 2. Color Palette & Roles

```
--bg:              #000000   /* true black, default canvas */
--bg-alt:          #0a0a0a   /* spec slab, secondary surface */
--surface:         #141414   /* card, configurator panel */
--text:            #ffffff
--text-muted:      #b8b8b8
--text-dim:        #6a6a6a
--accent:          #ffc000   /* warm gold, primary CTA */
--accent-hover:    #ffce3e   /* lifted gold on hover */
--accent-deep:     #917300   /* engraved gold, rules + active state */
--border:          #1f1f1f
--rule:            #2a2a2a
--hex-stroke:      #2a2a2a   /* hex grid motif */
```

One gold, three depths of black. No second accent. Color restraint is the luxury signal.

## 3. Typography Rules

- **Display + nameplates:** `LamboType`, fallback `Roboto`, `Helvetica Neue`, `Arial`. Weight 700, slight italic on model names. Tight tracking −2%. Used at 64–168px.
- **Body + UI:** `Roboto`, weight 400, 16–18px body, 1.55 line-height.
- **Labels + spec rows:** uppercase, tracked 12%, 11–12px, `--text-muted`.
- **Numerals (top speed, 0-100, output):** tabular, weight 700, paired with small unit labels.

Scale: 11 / 14 / 16 / 20 / 28 / 40 / 64 / 96 / 120 / 168.

Headlines go enormous — 120px is the floor for nameplates, not the ceiling.

## 4. Component Stylings

**Buttons**
- Primary: `--accent` fill, black text, radius 0, padding 14/28, weight 700, uppercase, tracked 8%.
- Secondary: transparent, 1px white border, white text, radius 0.
- Ghost: transparent, white text, no border, underline on hover.
- Hover: primary lifts to `--accent-hover`; secondary fills white-on-black inversion. No scale.

**Cards / model tiles**
- `--surface` fill, 1px `--border`, radius 0. Photo top, model name centered in LamboType at 40px, spec strip below.
- Hover: border shifts to `--accent-deep`, no shadow.

**Inputs**
- `--bg-alt` fill, 1px `--border`, radius 0, 14/16 padding. Focus: 2px `--accent` ring, no offset.

**Nav**
- Fixed top, transparent over hero, fills to `--bg` on scroll. White wordmark, uppercase tracked links, gold active underline 2px.

**Hex motif**
- Used sparingly: section dividers as a single 1px hex outline at the seam, never as repeating pattern wallpaper.

**Hero**
- Full-bleed black slab, vehicle photo center-stage, nameplate overlaid at 120–168px in white, single gold CTA bottom-center.

## 5. Layout Principles

- 1440px max, 24px gutter, 12 column.
- 8px base. 8 / 16 / 24 / 32 / 48 / 80 / 120 / 160.
- Alternate full-bleed black hero → `--bg-alt` spec slab → black configurator.
- Centered compositions over asymmetric — the car is on a plinth.
- Section breaks at 120–160px on desktop.

## 6. Depth & Elevation

Architectural, never soft. Depth from light direction in photography and tonal step between `#000` / `#0a0a0a` / `#141414`. Allowed: 1px hex divider, 1px border on cards. Forbidden: drop shadows, glows, backdrop blur, neumorphism, gradient fills.

## 7. Do's and Don'ts

**Do**
- Hold true `#000000` as the canvas — not `#0a0a` and not `#111`.
- Push nameplates to 120–168px; let them dominate the fold.
- Keep gold as the only chromatic note. One gold CTA per section.
- Use sharp 0-radius corners on every component.
- Keep the hex motif as a single outline at section seams, not a repeating pattern.

**Don't**
- Switch to off-black or charcoal. The true black is the differentiator.
- Add a second accent (red, blue, white-gold variants).
- Round corners or pill buttons.
- Apply drop shadows, glows, or beveled chrome.
- Use repeating hex wallpaper — that reads as gaming, not luxury.
- Mix in a serif typeface for "elegance".

## 8. Responsive Behavior

- Nameplate scales 168 → 56 on mobile, retains weight 700.
- Vehicle photo stacks above nameplate below 768px; black slab retains full bleed.
- Nav collapses to gold-on-black hamburger; uppercase tracked links stay.
- Spec strips reflow to single column; gold CTA stays full-width below 480px.

## 9. Agent Prompt Guide

Bias: true-black `#000000` canvas, oversized LamboType nameplates (120–168px), single warm-gold accent (`#ffc000`) on CTAs, sharp 0-radius components, hex motifs as 1px section seams, vehicle photographed as plinth-lit sculpture, uppercase tracked nav, three-tone black depth (`#000` / `#0a0a` / `#141414`).

Reject: charcoal or off-black backgrounds, secondary accent colors, rounded corners, drop shadows, glow rings, backdrop blur, repeating hex wallpaper, serif type for elegance, lifestyle photography, pill buttons, gradient backgrounds.
