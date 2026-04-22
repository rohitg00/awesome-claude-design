# Cohere — Enterprise AI Gradient

Reference DESIGN.md for enterprise-AI brands that need to feel premium, dark, and quietly futuristic. Ink canvas, Unica grotesque type, saturated coral-to-violet brand gradient deployed as backdrop and accent rule, full-pill buttons, generous oversized display.

## 1. Visual Theme & Atmosphere

Dark cinematic, but corporate-quiet. The page is near-black ink with carefully placed gradient surfaces — coral fading to violet to indigo — that echo the Cohere brand mark. Display type goes large. Body type is restrained. Pill buttons are the only soft geometry. Reads like a research lab that ships to the Fortune 100.

Mood: premium, scientific, quietly confident, enterprise-grade.

## 2. Color Palette & Roles

```
--bg-primary:      #17171c   /* near-black ink, default canvas */
--bg-elevated:     #1f1f26   /* card, modal */
--bg-light:        #ffffff   /* light sections, docs */
--text-on-dark:    #ffffff
--text-on-dark-muted: #b8b3ad
--text-on-dark-dim:  #75758a
--text-on-light:   #17171c
--text-on-light-muted: #5a5a66
--border-on-dark:  #2a2a33
--border-on-light: #e5e2dc

/* brand gradient — coral → violet → indigo */
--brand-coral:     #ff7759
--brand-pink:      #ff6b9d
--brand-violet:    #9b60aa
--brand-indigo:    #5a5fff
--brand-sand:      #d7cfc1   /* link, soft accent on dark */

--gradient-brand:  linear-gradient(135deg, #ff7759 0%, #ff6b9d 35%, #9b60aa 70%, #5a5fff 100%)
--gradient-soft:   linear-gradient(180deg, rgba(155, 96, 170, 0.12) 0%, transparent 100%)
```

Rule: the four-stop brand gradient is the identity. Use it on hero backdrop, oversized text fills, and brand mark — not on buttons. Buttons stay ink or white.

## 3. Typography Rules

- **Display + headings:** `Unica77 Cohere Web` (CohereText), fallback `Space Grotesk`, `Inter`. Weight 400/500. Tight tracking at large sizes (−1.5%).
- **Body + UI:** Unica77 weight 400, fallback Inter, system-ui. 14–18px body.
- **Mono:** `JetBrains Mono`, fallback `SF Mono`. Used for code samples and model-name labels.

Scale: 12 / 14 / 16 / 20 / 24 / 32 / 48 / 64 / 96.

Hero display goes to 96px. Resist scaling down for "balance" — the oversize is the point.

## 4. Component Stylings

**Buttons**
- Primary: ink `#17171c` fill, white text, full pill (radius 9999), padding 12/24, weight 500.
- Secondary: white fill, ink text, full pill, 1px ink border.
- Ghost on dark: transparent, white text, 1px white border, full pill.
- Hover: 8% lighten/darken, no scale. No glow.

**Cards**
- Dark surface: `--bg-elevated`, 1px `--border-on-dark`, radius 7px.
- Light surface: white, 1px `--border-on-light`, radius 7px.
- Hover: border shifts to `--brand-sand` on dark, `--brand-violet` on light. No shadow.

**Inputs**
- Transparent fill, 1px border, radius 7px, padding 10/14. Focus: 2px `--brand-violet` ring, 2px offset.

**Hero gradient surface**
- Full-bleed `--gradient-brand` panel, 60–80vh tall.
- Display headline overlaid in white at 96px, weight 400, tight tracking.
- Pill CTA bottom-left, ink fill on the gradient.

**Nav**
- Fixed top, transparent over hero, shifts to ink fill with 1px `--border-on-dark` on scroll. No backdrop blur.

## 5. Layout Principles

- 1440px max, 32px gutter, 12 column.
- 8px base. 8 / 16 / 24 / 32 / 48 / 80 / 120 / 160.
- Section breaks at 120–160px on desktop.
- Alternate full-bleed gradient hero, ink content slab, light docs slab. Three modes per page max.

## 6. Depth & Elevation

Atmospheric, never literal. Depth from gradient saturation, type weight, surface tone shifts. Shadows allowed only on modals: `0 24px 64px rgba(0, 0, 0, 0.48)`. Forbidden: glow rings, neon outlines, neumorphic tiles.

## 7. Do's and Don'ts

**Do**
- Deploy the four-stop brand gradient on hero backdrop and as a large text fill, once per page max.
- Keep buttons binary: ink pill or white pill. Gradients live around buttons, not on them.
- Set display headlines at 96px and trust the whitespace.
- Pair Unica77 grotesque consistently — no secondary display family.

**Don't**
- Apply the brand gradient to buttons, links, or body text.
- Switch to pure black (`#000`) — the warm-ink `#17171c` is the brand.
- Add glow effects, neon outlines, or accent rings to interactive elements.
- Round corners past 8px on cards or inputs. Pills are reserved for buttons only.
- Mix in a third typeface for "playfulness".

## 8. Responsive Behavior

- Hero display scales 96 → 40 on mobile.
- Brand gradient backdrop retains full bleed; CTA stacks below headline.
- Nav collapses to ink hamburger on `--bg-primary` below 768px.
- 12-column grid reflows to single column below 768px; 80px section breaks.

## 9. Agent Prompt Guide

Bias: warm-ink `#17171c` canvas, oversized Unica77 display, four-stop coral→violet→indigo brand gradient on hero, ink-or-white pill buttons (never gradient buttons), 7px radii on cards, generous 120px section rhythm, alternating dark/gradient/light slabs.

Reject: pure-black `#000` canvas, gradient-filled buttons or text links, glow effects, neumorphism, multi-typeface mixing, dense card-grid layouts, dropping the brand gradient for "minimalism", chat-bubble UI in product surfaces.
