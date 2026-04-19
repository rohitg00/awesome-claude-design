# Claude (Anthropic) — Warm Editorial

Reference DESIGN.md for a terracotta-on-cream editorial aesthetic. Drop into Claude Design → scaffolds the full system.

## 1. Visual Theme & Atmosphere

Warm editorial. Human, considered, slightly literary. Not tech-startup sterile, not luxury-brand cold. Feels like a well-designed magazine spread with a craft espresso on the side. Generous whitespace, slow rhythm, long-form reading is first-class.

Mood words: calm, earnest, tactile, deliberate, patient.

## 2. Color Palette & Roles

```
--bg-primary:      #f4f3ee   /* cream, page */
--bg-secondary:    #eeede6   /* subtle surface lift */
--bg-inverse:      #191817   /* near-black, inverse sections */
--text-primary:    #191817   /* ink */
--text-secondary:  #5a554e   /* warm gray */
--text-muted:      #8a847a
--accent:          #c96442   /* terracotta */
--accent-hover:    #b55738
--accent-soft:     #e89268   /* callouts, illustrations */
--border:          #d8d3c8
--success:         #6b7a3d
--warning:         #c98a42
--danger:          #a53e2a
```

Rules: one accent per viewport. Terracotta never competes with itself. Never tint body text with accent.

## 3. Typography Rules

- **Display / headlines:** serif. `Tiempos Headline`, `Iowan Old Style`, fallback `Georgia`. Weight 500. Letter-spacing −1.5% at large sizes.
- **Body:** humanist sans. `Styrene A`, fallback `Inter`. Weight 400. Line-height 1.6. Measure 65–72 characters.
- **UI / labels:** same humanist sans, weight 500, letter-spacing +2%, uppercase only for eyebrow labels.
- **Code / mono:** `GT America Mono`, fallback `JetBrains Mono`, `SF Mono`.

Type scale (modular 1.25): 13 / 15 / 17 / 21 / 26 / 32 / 40 / 50 / 62.

Headlines balance (`text-wrap: balance`), body reflow (`text-wrap: pretty`).

## 4. Component Stylings

**Buttons**
- Primary: terracotta fill, cream text, radius 6px, padding 10/18, weight 500. Hover: darker terracotta, no lift.
- Secondary: 1px `--border`, ink text, transparent fill. Hover: `--bg-secondary`.
- Ghost: ink text, underline on hover.

**Cards**
- Background `--bg-secondary`, no border, no shadow. Radius 8px. Padding 24.
- Hover: subtle `--border` appears. No transform, no scale.

**Inputs**
- 1px `--border`, radius 6px, padding 10/14. Focus: 2px `--accent` outline with 2px offset. No box-shadow glows.

**Navigation**
- Horizontal, underline-on-hover, accent underline on active. No pill backgrounds.

**Tables**
- Zebra rows on `--bg-secondary`. Header in mono, uppercase, tracked wide.

## 5. Layout Principles

- Max content width 680px for long-form, 1180px for app shells.
- 12-column grid, 24px gutters.
- Vertical rhythm: baseline 8px, heading top-margin 2× line-height, section break = 96px.
- Asymmetry is allowed and encouraged for editorial pages (pull-quotes float, sidenotes in margin).

## 6. Depth & Elevation

Flat by default. No drop shadows. Depth comes from:
- Surface color shifts (`--bg-secondary` over `--bg-primary`)
- 1px `--border` lines
- Type weight contrast

Exception: modals use a single `0 8px 24px rgba(25, 24, 23, 0.08)` shadow.

## 7. Do's and Don'ts

**Do**
- Let whitespace do the heavy lifting.
- Use serif for long-form headlines, sans for UI.
- Lean on typographic hierarchy before color.
- Write microcopy in full sentences with periods.

**Don't**
- Use purple gradients. Ever.
- Apply Inter to every surface by default.
- Animate hover states with scale or lift.
- Mix more than two fonts per page.
- Use emojis in UI chrome.

## 8. Responsive Behavior

- Single-column mobile, no hamburger-only nav — show 2–3 primary links.
- Serif headline size scales 62 → 36 on mobile.
- Tables become stacked cards below 640px.
- Long-form retains 18px body on mobile (not 16).

## 9. Agent Prompt Guide

Bias toward:
- Serif headlines, humanist sans body.
- One terracotta moment per viewport.
- Flat surfaces, typographic depth.
- Long lines broken by pull-quotes and sidenotes.

Reject:
- Purple-to-pink gradients, glassmorphism, neon glows.
- Card-heavy layouts where every element is a rounded box.
- Generic hero + 3-column features + CTA template.

When generating, ask: "Would this look at home on the Anthropic blog or in a New Yorker feature?" If not, start over.
