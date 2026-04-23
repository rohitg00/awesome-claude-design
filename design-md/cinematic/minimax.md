# MiniMax — Cinematic Lab

Reference DESIGN.md for AI-lab cinematic: pure black canvas, neon-lime accent on charcoal chrome, geometric DM Sans / Outfit type, pill-shaped CTAs.

## 1. Visual Theme & Atmosphere

Cinematic lab. The page reads like a research-trailer reel — black canvas, oversized geometric type, demos that loop without a play button, and one neon-lime moment per screen that signals "this is the action." Chrome shrinks; the model demos are the subject. Marketing surfaces stay dark by default; the rare light section is a deliberate inversion that frames a paper or product spec.

Mood: laboratory-grade, kinetic, deliberately understated until the lime CTA fires.

## 2. Color Palette & Roles

```
--bg:              #000000   /* canvas */
--bg-alt:          #0a0a0a
--surface:         #181e25   /* charcoal — observed brand chrome */
--surface-2:       #232a33
--text:            #ffffff
--text-muted:      #c5c9cf
--text-dim:        #7a808a
--border:          #2a3038
--border-strong:   #3a4049

--accent:          #c8ff00   /* neon lime — primary action + brand */
--accent-hover:    #d8ff3a
--accent-deep:     #9bcc00   /* hover-pressed, ink-on-light variant */
--accent-soft:     #e9ff86   /* tinted callouts */

/* inverse — used for spec / paper sections only */
--bg-inverse:      #ffffff
--text-inverse:    #181e25
--border-inverse:  #e1e3e6

--success:         #6ee7b7
--warning:         #ffd166
--danger:          #ff5d5d
```

Rule: lime `--accent` carries one moment per viewport and never tints body text. Charcoal `--surface` is the resting chrome state; pure black is for full-bleed media. Inverse light sections are the exception, not the rhythm.

## 3. Typography Rules

- **Display + headlines:** `Outfit`, fallback `Helvetica Neue`, `Helvetica`, `Arial`, system. Weight 500–700, tight tracking (−1% at large sizes). Outfit's geometric construction reads as "model architecture diagram."
- **Body + UI:** `DM Sans`, fallback `Helvetica Neue`, `Helvetica`, `Arial`, system. Weight 400/500. Line-height 1.5–1.6.
- **UI labels:** DM Sans weight 500, 13–14px, uppercase only for category eyebrows (tracked +4%).
- **Numerals:** tabular figures on benchmark tables, parameter counts, latency stats.
- **Mono:** `JetBrains Mono`, fallback `SF Mono`. Used for code samples, API snippets, citation hashes.

Scale: 12 / 14 / 16 / 20 / 28 / 40 / 56 / 80 / 112.

Headlines balance (`text-wrap: balance`); body reflows (`text-wrap: pretty`). Display goes to 80–112px on launches.

## 4. Component Stylings

**Buttons**
- Primary: lime fill `--accent`, charcoal text `--surface`, radius 60px (pill), padding 12/24, weight 500. Hover: `--accent-hover`. No lift, no scale.
- Secondary: white fill, charcoal text, radius 12px, weight 500. Used inside dark sections to invert hierarchy.
- Tertiary / link: white text, lime underline on hover.
- Destructive: `--danger` fill, white text, only on confirm modals.

**Cards / model tiles**
- `--surface` fill, 1px `--border`, radius 12px. Padding 24.
- Hero model cards run looping demo videos with text overlay; bottom gradient scrim for legibility.
- Hover: 1px `--accent` border, 200ms ease. No scale.

**Inputs**
- `--bg-alt` fill, 1px `--border-strong`, radius 12px, padding 12/14. Focus: 2px `--accent` ring with 1px offset.

**Nav**
- Fixed top, `--bg` fill with 80% opacity and 12px backdrop blur. White links, lime underline on active.

**Demo player**
- Autoplay muted, looped, 16:9 minimum. No controls visible until hover. Reduced-motion users get a static still frame and a play affordance.

## 5. Layout Principles

- Full-bleed hero (100vw, 80–100vh) anchored on a model demo loop.
- 1280px max for content sections, 32px gutter, 12-column.
- 8px base. 8 / 16 / 24 / 32 / 48 / 64 / 96 / 128.
- Generous vertical whitespace between sections (96–128px).
- Spec / benchmark tables break the editorial rhythm and run dense.

## 6. Depth & Elevation

Flat surfaces with hard borders. Depth comes from:
- Surface tonal shift (`--bg → --surface → --surface-2`)
- 1px `--border` and `--border-strong`
- Demo media hierarchy

Modals get `0 24px 64px rgba(0, 0, 0, 0.72)` over a 70% black scrim. No drop shadows on cards or buttons. Reserve subtle glow effects for hovered demo tiles only.

## 7. Do's and Don'ts

**Do**
- Open with a full-bleed model demo loop. No stock photography.
- Reserve lime for the single CTA moment per viewport.
- Oversize the launch headline. 80–112px on hero.
- Use tabular numerals for benchmark deltas (1.7×, 2.5×, +43%).
- Pair pill primary CTAs with rectangular `12px` secondary buttons — the geometric collision is the brand.

**Don't**
- Use lime inside body text or as a paragraph tint.
- Use multiple accents per viewport.
- Soften corners past 16px on cards.
- Switch to a light theme as the marketing default.
- Add purple-to-pink gradients, glassmorphism, or rainbow accents.

## 8. Responsive Behavior

- Hero demo remains full-bleed; headline scales 112 → 36 on mobile.
- Nav collapses to drawer at 1024px, full-screen overlay below 768px.
- Spec tables become horizontally scrollable below 640px (preserve density, no stacking).
- Autoplay disabled on mobile per bandwidth respect; static poster substitutes.
- Body type holds 16px on mobile.

## 9. Agent Prompt Guide

Bias: pure black `#000000` canvas with charcoal `#181e25` chrome, single neon-lime `#c8ff00` moment per viewport reserved for primary CTA, Outfit display headlines paired with DM Sans body, oversized launch type (80–112px), pill primary CTAs at 60px radius alongside 12px-radius secondaries, looping demo media as the hero artifact, tabular numerals on benchmark tables.

Reject: light-mode marketing pages, multi-color palettes, soft pastel gradients, glassmorphism, scale-on-hover lifts, hero stock photography in place of demo loops, decorative illustration in chrome, lime tints on body type.
