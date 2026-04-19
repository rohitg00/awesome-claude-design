# Figma — Playful Color

Reference DESIGN.md for multi-color, rounded, illustration-friendly SaaS.

## 1. Visual Theme & Atmosphere

Playful color. The brand palette itself is the identity. Multiple hues coexist. Rounded corners, illustrated accents, friendly microcopy. Approachable for consumer and prosumer alike.

Mood: welcoming, expressive, generous.

## 2. Color Palette & Roles

```
--bg:              #ffffff
--bg-alt:          #fafafa
--text:            #0f0f14
--text-muted:      #6e6e78
--border:          #e5e5ea

/* brand prism — all first-class */
--brand-green:     #0acf83
--brand-orange:    #f24e1e
--brand-purple:    #a259ff
--brand-red:       #ff7262
--brand-blue:      #1abcfe

--accent-default:  var(--brand-purple)
```

Rule: any of the five brand hues is valid as an accent. Use one per page section, rotate across the site.

## 3. Typography Rules

- **Headlines:** `Whyte Inktrap`, fallback `PP Editorial New`, weight 500, tight tracking.
- **Body:** `Inter`, weight 400, 16px.
- **UI:** Inter, weight 500.
- **Mono:** `Söhne Mono`.

Scale: 13 / 15 / 17 / 20 / 24 / 32 / 44 / 64 / 88.

## 4. Component Stylings

**Buttons**
- Primary: brand-hue fill, white text, radius 8px, padding 10/18, weight 500.
- Hover: 10% darker fill, no scale.
- Secondary: 1.5px brand-hue border, brand-hue text.

**Cards**
- White fill, 1px `--border`, radius 12px, padding 24.
- Hover: `0 8px 24px rgba(15, 15, 20, 0.08)` shadow.

**Illustrations**
- Flat vector, 2–3 brand hues per illustration.
- Simple geometric shapes (circle, rounded square, blob).
- Avoid photorealism; avoid gradients that aren't brand hues.

**Inputs**
- 1.5px `--border`, radius 8px, padding 10/14. Focus: 2px brand-hue ring.

## 5. Layout Principles

- 1280px max, 32px gutter on desktop.
- 8px base unit.
- Sections alternate tinted backgrounds (10% opacity of brand hues).

## 6. Depth & Elevation

Soft shadows allowed on cards. Radius is generous (12–24px on cards, 999 on pills). No neumorphism.

## 7. Do's and Don'ts

**Do**
- Rotate accent hue across sections.
- Use illustrations that reinforce the brand.
- Write microcopy that sounds like a helpful friend.

**Don't**
- Use only one brand hue across the entire page.
- Sharp 0–4px radii (too cold).
- Dark mode as the default.

## 8. Responsive Behavior

- Sections stack gracefully below 768px.
- Illustrations center and scale to 50% width.
- Headlines scale 88 → 32 on mobile.

## 9. Agent Prompt Guide

Bias: five-color brand prism rotated across sections, 8–16px radii, soft shadows, illustrations in flat vector, friendly copy.

Reject: single monochrome palette, 0px radius, photorealistic imagery, dark-by-default layouts.
