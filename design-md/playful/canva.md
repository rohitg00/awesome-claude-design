# Canva — Design Platform Playful

Reference DESIGN.md for design tools that need to feel friendly and full-spectrum without sliding into kitsch. Canva-purple action, periwinkle and sky support tones, generous radii, gradient surfaces used as backdrops not buttons.

## 1. Visual Theme & Atmosphere

Approachable creativity. The palette is broader than a SaaS would dare — purple, periwinkle, sky, mint, coral all coexist — but every page anchors on one Canva-purple CTA. Surfaces breathe. Buttons are large, friendly, reachable. Microcopy assumes a first-time user without talking down.

Mood: welcoming, expressive, capable, optimistic.

## 2. Color Palette & Roles

```
--bg:              #ffffff
--bg-alt:          #f5f5f7
--surface:         #ffffff
--text-primary:    #0f1015
--text-secondary:  #575a5f
--text-muted:      #8a8d93
--border:          #e0e1e6
--border-strong:   #c9cad1

/* brand spectrum — all first-class, rotate by section */
--brand-purple:    #8b3dff   /* primary action, the Canva color */
--brand-purple-hover: #7929e6
--brand-periwinkle: #9e9eff  /* gradient pair, hover surfaces */
--brand-sky:       #00c4cc   /* secondary action, education */
--brand-mint:      #7ed6a3
--brand-coral:     #ff7a59
--brand-yellow:    #ffd66b

/* gradients */
--gradient-hero:   linear-gradient(135deg, #8b3dff 0%, #00c4cc 100%)
--gradient-soft:   linear-gradient(180deg, #cce1ff 0%, #ffffff 100%)
```

Rule: one brand-purple primary CTA per viewport. Other brand hues appear as gradient backdrops, illustration fills, or category chips — never as a competing primary button.

## 3. Typography Rules

- **All UI + headings + body:** `Canva Sans`, fallback `Noto Sans`, system-ui. Weight 400/500/700.
- **Display headlines:** Canva Sans weight 700, tracking −1%.
- **Mono:** `Roboto Mono` for code samples in dev docs only. Not used in product chrome.

Scale: 12 / 14 / 15 / 18 / 22 / 28 / 36 / 48 / 64.

Single typeface across the system. Hierarchy from weight + size, not family.

## 4. Component Stylings

**Buttons**
- Primary: `--brand-purple` fill, white text, radius 8px, padding 12/20, weight 700.
- Secondary: white fill, 1px `--border-strong`, ink text, radius 8px.
- Tertiary: text-only, purple, underline on hover.
- Hover: 8% darker fill, no scale, no shadow.

**Cards**
- White fill, 1px `--border`, radius 12px, padding 20.
- Hover: `0 4px 16px rgba(15, 16, 21, 0.08)` shadow, no transform.
- Template thumbnails: 1px border on hover only, otherwise borderless.

**Inputs**
- 1px `--border-strong`, radius 8px, padding 10/14. Focus: 2px purple ring, 1px offset.
- Search bars: full pill (radius 999), `--bg-alt` fill on focus.

**Illustrations**
- Flat vector, rounded geometric forms, 3–4 brand hues per illustration max.
- Avoid photorealism in marketing; product UI uses real template thumbnails.

**Gradients**
- Allowed only on hero backdrops and large promotional cards.
- Never on buttons. Never on body text.

## 5. Layout Principles

- 1440px max marketing, 100vw app shell.
- 4px base. 4 / 8 / 12 / 16 / 20 / 24 / 32 / 48 / 80.
- Sections alternate white and `--bg-alt` for rhythm. Soft gradient backdrops appear once per page max.
- Template grids: 4-up desktop, 2-up tablet, 1-up mobile.

## 6. Depth & Elevation

Soft shadows on hover, never on default state. Modals: `0 12px 32px rgba(15, 16, 21, 0.16)`. Floating action buttons in the editor: `0 4px 12px rgba(139, 61, 255, 0.24)`. No neumorphism, no inner shadows.

## 7. Do's and Don'ts

**Do**
- Anchor every viewport on one Canva-purple CTA, no exceptions.
- Use the gradient backdrop sparingly — once per page for emphasis.
- Write microcopy that explains the next click in plain words.
- Show real template thumbnails in product surfaces, not placeholder shapes.

**Don't**
- Apply gradients to buttons or body text.
- Use sharp 0–4px radii — friendly geometry is part of the brand.
- Drop the brand spectrum to a single hue for "professionalism" — the spectrum is the identity.
- Stack two saturated brand-hue CTAs on the same fold.
- Replace illustrations with stock photography in marketing.

## 8. Responsive Behavior

- Editor sidebar collapses to bottom-sheet below 1024px.
- Template grid reflows 4 → 2 → 1 at 1280 / 768 / 480.
- Headlines scale 64 → 32 on mobile.
- CTA full-width below 480px.

## 9. Agent Prompt Guide

Bias: white canvas, single-typeface (Canva Sans) hierarchy, one Canva-purple primary per viewport, full brand spectrum reserved for illustrations and gradient backdrops, 8–12px radii, soft hover shadows, friendly microcopy, real template thumbnails.

Reject: dark-mode default, monochrome single-hue palettes, sharp 0px radii, gradient-filled buttons, photorealistic stock imagery, dense data-table layouts, hero copy that assumes designer literacy.
