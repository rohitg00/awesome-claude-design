# BMW — Editorial Performance Blue

Reference DESIGN.md for luxury automotive editorial that needs to feel engineered. White slabs, full-bleed performance photography, BMW corporate blue rising into a deeper blue at active states, restrained Helvetica-grade typography.

## 1. Visual Theme & Atmosphere

Editorial automotive. The page is a magazine: oversized photo plates of the car, clean white margins, narrow blue keyline rules. Headlines are short and committed. Blue is the only chromatic note — every other surface is paper-white or near-black. Reads like a Munich brochure that learned to scroll.

Mood: precise, premium, engineered, quietly confident.

## 2. Color Palette & Roles

```
--bg:              #ffffff
--bg-alt:          #f6f6f6   /* spec sheet, secondary slab */
--surface:         #ffffff
--ink:             #262626   /* body text, headlines on light */
--ink-muted:       #6b6b6b
--ink-dim:         #a8a8a8
--bg-inverse:      #111111   /* M Performance dark slab */
--text-on-dark:    #ffffff
--accent:          #1c69d4   /* BMW corporate blue, primary CTA */
--accent-hover:    #0653b6   /* deeper marine on hover, focus, link */
--m-gradient:      linear-gradient(90deg, #2e9bd6 0%, #1c69d4 50%, #0653b6 100%)
--border:          #e5e5e5
--rule:            #1c69d4
```

One blue, one neutral pair. The M-style gradient is reserved for performance moments — never on body or buttons.

## 3. Typography Rules

- **Display + headings:** `BMW Type Next Web`, fallback `Helvetica Neue`, `Helvetica`, `Arial`, `sans-serif`. Weight 400 for editorial, 700 for vehicle nameplates. Tight tracking at 48px+.
- **Body + UI:** same stack, weight 400, 16–18px, 1.5 line-height.
- **Labels + spec rows:** uppercase, tracked 8%, 12–13px, ink-muted.

Scale: 12 / 14 / 16 / 20 / 28 / 36 / 48 / 64 / 96. Restraint is the point — brochures don't shout.

## 4. Component Stylings

**Buttons**
- Primary: `--accent` fill, white text, radius 3px, padding 12/24, weight 500.
- Secondary: transparent, 1px ink border, ink text, 3px radius.
- Hover: fill shifts to `--accent-hover`. No scale, no glow.

**Cards / vehicle tiles**
- White surface, 1px `--border`, radius 3px. Photo top, two-line title, one-line spec, blue inline link.
- Hover: border shifts to `--accent`. Shadow stays off.

**Inputs**
- White fill, 1px border, 3px radius. Focus: 2px `--accent` ring, no offset.

**Nav**
- Fixed top, white fill, 1px bottom border. Logo left, model groups center, account/build right. Active link gets a 2px `--accent` underline.

**Hero photo plate**
- Full-bleed vehicle photograph, 70–90vh. Headline overlaid bottom-left in white, 64–96px. CTA below in primary blue.

## 5. Layout Principles

- 1440px max, 24px gutter, 12 column.
- 8px base. 8 / 16 / 24 / 32 / 48 / 80 / 120.
- Alternate full-bleed hero, white spec slab, `--bg-alt` comparison slab.
- Section breaks at 96–120px on desktop. Whitespace flanks the photograph; never crop the car.

## 6. Depth & Elevation

Almost flat. Depth comes from photographic contrast, not chrome. Allowed: 1px `--border` on cards, 2px `--accent` keyline at section breaks. Shadows reserved for floating spec sheets only — `0 8px 24px rgba(0, 0, 0, 0.08)`. No glows, no neumorphism.

## 7. Do's and Don'ts

**Do**
- Lead with full-bleed vehicle photography at the fold.
- Hold to one blue. Use the M-gradient once, on a single performance moment.
- Pair short editorial headlines with tracked uppercase labels for specs.
- Keep buttons binary: blue primary or ghost. Sharp 3px corners only.

**Don't**
- Apply the M-gradient to buttons, links, or body type.
- Add a second accent color (red, gold, green) — that's a competitor brand.
- Round corners past 4px or pill anything — automotive is engineered, not playful.
- Drop the photograph for stock illustration or hero CGI.
- Use heavy shadows or backdrop blur on nav.

## 8. Responsive Behavior

- Hero headline scales 96 → 36 on mobile, retains weight 400.
- Vehicle photo retains full bleed; CTA stacks below headline.
- Nav collapses to white hamburger below 1024px; model groups fold into a single sheet.
- 12-column grid reflows to single column below 768px; 64px section rhythm.

## 9. Agent Prompt Guide

Bias: paper-white canvas, full-bleed automotive photography, BMW Type Next Web headlines, single corporate blue (`#1c69d4`) on CTAs, sharp 3px radii, tracked uppercase spec labels, restrained editorial rhythm, M-gradient used once per page maximum.

Reject: dark-mode default, multi-color accents, pill buttons, drop shadows on hero plates, gradient-filled body type, stock illustration replacing the vehicle photo, glassmorphism, oversized rounded corners.
