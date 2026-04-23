# Ferrari — Chiaroscuro Rosso Corsa

Reference DESIGN.md for performance brands that need to feel theatrical. High-contrast black-and-white frames cut by Rosso Corsa red, sharp 0-radius components, FerrariSans across the entire page, photography that treats the car as sculpture.

## 1. Visual Theme & Atmosphere

Cinematic chiaroscuro. The page alternates between a deep ink stage and a paper-white gallery, with Rosso Corsa appearing once per section as a single decisive note — a CTA, a rule, a numeral. Photography is high-contrast: car against black sky, paddock light, Maranello tarmac. Every component is a sharp rectangle. Italian editorial discipline meets Formula 1 timing.

Mood: theatrical, decisive, hand-built, fast.

## 2. Color Palette & Roles

```
--bg-light:        #ffffff
--bg-dark:         #000000   /* full-bleed dark slabs, hero */
--bg-alt:          #f4f4f4   /* spec rail, paddock light */
--text-on-light:   #000000
--text-on-dark:    #ffffff
--text-muted:      #6a6a6a
--accent:          #eb2323   /* Rosso Corsa, primary CTA + rule */
--accent-hover:    #c81a1a
--accent-bright:   #ff0000   /* link, focus, livery moments */
--support-yellow:  #f6e500   /* Modena yellow, race-livery accent only */
--border:          #1a1a1a
--rule:            #eb2323
```

Rule: red appears once per visual frame. Never two reds touching. Yellow is reserved for racing-content slabs and never sits in the same hero as a CTA.

## 3. Typography Rules

- **Display + headings:** `FerrariSans`, fallback `Helvetica`, `Arial`, `sans-serif`. Weight 700 for nameplates, weight 500 for editorial heads. Tracked −1% above 48px.
- **Body + UI:** FerrariSans regular, 13–16px body, 1.5 line-height.
- **Numerals (lap times, displacement, top speed):** tabular, weight 700, oversized — 64–140px.
- **Labels:** uppercase, tracked 10%, 11–12px.

Scale: 11 / 13 / 16 / 20 / 26 / 36 / 56 / 88 / 140.

Single typeface. The contrast is black/white/red — not type families.

## 4. Component Stylings

**Buttons**
- Primary: `--accent` fill, white text, radius 0, padding 14/28, weight 700, uppercase, tracked 6%.
- Secondary on light: transparent, 1px ink border, ink text, sharp rectangle.
- Ghost on dark: transparent, 1px white border, white text.
- Hover: fill shifts to `--accent-hover` instantly. No transition softening.

**Cards / model tiles**
- No card chrome on hero. Full-bleed photo on `--bg-dark` with overlaid label bottom-left.
- Spec cards on light: white surface, 1px `--border` hairline above and below only — no left/right border. Radius 0.

**Inputs**
- Sharp rectangle, 1px ink border, 12/16 padding, radius 0. Focus: 2px `--accent` outline, no offset.

**Nav**
- Fixed top, transparent over hero, snaps to ink fill on scroll. White wordmark, uppercase nav links, red active underline 2px.

**Hero**
- Full-bleed dark slab, vehicle photo right-aligned 60% width, headline left in white at 88–140px, single `--accent` CTA below.

## 5. Layout Principles

- 1320px max content, full-bleed photo plates, 24px gutter, 12 column.
- 8px base. 8 / 16 / 24 / 32 / 48 / 80 / 120 / 160.
- Alternate dark hero → white spec → dark dyno-numerals → white configurator.
- Asymmetric splits (60/40 photo + numeral block) over symmetric grids.

## 6. Depth & Elevation

Flat, theatrical. Depth from contrast, not shadow. Allowed: 1px hairline above/below spec rows. Forbidden: drop shadows on cards, glow effects, beveled edges, layered translucency.

## 7. Do's and Don'ts

**Do**
- Use one Rosso Corsa moment per visual frame: CTA, rule, or oversized numeral.
- Oversize lap times and displacement numerals to 88–140px.
- Alternate dark and light slabs aggressively — chiaroscuro is the brand.
- Keep every corner at radius 0.

**Don't**
- Pair red and yellow in the same hero. Yellow is racing-only.
- Round any corner. No pill buttons, ever.
- Add drop shadows, glows, or backdrop blur.
- Mix in a second typeface — FerrariSans does everything.
- Use lifestyle stock photography. The car is the subject, always.

## 8. Responsive Behavior

- Hero headline scales 140 → 48 on mobile, retains weight 500.
- Vehicle photo stacks above headline below 768px; dark slab retains full bleed.
- Nav collapses to ink hamburger; uppercase links stay tracked.
- Oversized numerals scale 140 → 64 but never thin out — weight 700 holds.

## 9. Agent Prompt Guide

Bias: alternating black/white full-bleed slabs, FerrariSans single-family typography, oversized lap-time numerals (88–140px), Rosso Corsa `#eb2323` used once per frame as CTA or rule, sharp 0-radius components, uppercase tracked nav.

Reject: rounded corners, drop shadows, multi-typeface mixing, red and yellow in the same hero, pastel palettes, lifestyle stock photography, gradient buttons, glassmorphism, sidebar-heavy layouts.
