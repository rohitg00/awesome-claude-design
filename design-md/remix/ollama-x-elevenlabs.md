# Ollama × ElevenLabs — CLI Tool With A Cinematic Hero

Remix. Ollama's pure terminal monochrome + ElevenLabs' cinematic dark gradients and electric-blue motion. For CLI / OSS tool landing pages that want the hero to feel like a product film, then settle into terminal density below the fold.

## Parent DNA: Ollama 50% · ElevenLabs 50%

## 1. Visual Theme & Atmosphere

Two surfaces, one product. Above the fold: cinematic — full-bleed near-black gradient, oversized headline, subtle wave-form motion, electric blue accent. Below the fold: terminal — pure black surfaces, monospace everywhere, 1px borders, code blocks with breathing room, no decoration.

The hero plays like a 4-second film bumper before the page resolves into a documentation surface. The transition is a single horizontal rule and a font-weight shift — no bridge gradient.

Mood: cinematic intro, technical execution.

## 2. Color Palette & Roles

```
/* terminal base from Ollama */
--bg:              #000000
--bg-alt:          #080808
--surface:         #14141a
--text:            #ffffff
--text-muted:      #a0a0a8
--text-dim:        #6b6b75
--border:          #2a2a32
--border-strong:   #3d3d48

/* cinematic hero from ElevenLabs */
--hero-bg:         #0a0a14
--hero-gradient:   radial-gradient(ellipse at 50% 30%, #1a2440 0%, #0a0a14 70%)
--accent:          #2c6cff
--accent-glow:     #4d8aff
--accent-soft:     rgba(44,108,255,0.16)

/* light mode (docs only — terminal stays dark) */
--bg-light:        #ffffff
--text-light:      #000000
```

Arbitration: Ollama's pure `#000` wins all body surfaces, code blocks, and docs. ElevenLabs' radial gradient is allowed only on the hero panel and on featured product cards. Electric blue is the sole accent across both modes.

## 3. Typography Rules

- **Hero h1:** Inter Display (ElevenLabs), weight 600, 88px+, tight tracking (-0.02em).
- **Hero subhead:** Inter, weight 400, 20px, `--text-muted` color.
- **Body h1–h6:** JetBrains Mono (Ollama-adjacent), weight 500/600. Headings stay mono — terminal discipline.
- **Body:** JetBrains Mono, weight 400, 14/22.
- **UI labels + code:** JetBrains Mono, all weights.

Scale: Ollama's terminal ramp + ElevenLabs' hero extension. 11 / 13 / 14 / 16 / 20 / 28 / 40 / 56 / 88 / 128.

Inter fires only on the hero. Below the fold, mono everywhere.

## 4. Component Stylings

**Hero panel**
- `--hero-gradient` background, full-bleed, min-height 80vh.
- Centered headline at 88px+, subhead at 20px, single CTA.
- Optional looping wave-form / particle motion at 4–6% opacity, never above 8%.

**Button (primary, hero)**
- Fill `--accent`, text `--text`, weight 500, radius 4. Padding 12/24.
- Subtle `--accent-glow` outer shadow at 16px / 0 / `--accent-soft`.

**Button (primary, body)**
- Same `--accent` fill, no glow, sharper radius (2). Padding 8/16. Mono label.

**Button (secondary)**
- Transparent fill, 1px `--border`, `--text` color. Mono label.

**Code block**
- `--bg-alt` fill, 1px `--border`, radius 4, padding 16/20. Mono 14px.
- Copy-button top-right, `--text-dim` until hover then `--text`.

**Card / feature tile**
- `--bg-alt` fill, 1px `--border`, radius 4. Mono heading 16px, body 13px. Optional 1px `--accent` top rule on featured cards.

**Input**
- Mono. 1px `--border`, radius 2, padding 8/12. Focus: 1px `--accent` border, no ring.

## 5. Layout Principles

- Hero: full-bleed, no max-width, vertical center.
- Body: 1080px max, 24px gutter, 12-column.
- Docs: 240px sidebar + 720px content + 200px on-this-page rail.
- 4px base. 4 / 8 / 12 / 16 / 24 / 32 / 48 / 64.

Ollama's tight spacing holds below the fold. The hero is the only place vertical rhythm goes generous (96px+ section padding).

## 6. Depth & Elevation

Two depth modes.

- Hero: gradient depth + soft glow on accent only. No card shadows.
- Body: flat. Border-only depth. Code blocks and cards never elevate.

ElevenLabs contributes the glow; Ollama contributes the flatness. They occupy different surfaces — never composed on the same element.

## 7. Do's and Don'ts

**Do**
- Confine the radial gradient to hero / feature-card surfaces.
- Keep all body type in mono — including h1–h6.
- Use the wave-form motion at < 8% opacity, looping, never on scroll-triggered.
- Single accent: electric blue. Period.

**Don't**
- Bridge the hero gradient into body surfaces with intermediate gradients.
- Drop Inter into body or docs.
- Add a second neon (cyan, magenta, lime) — kills the discipline.
- Add box shadows on body cards.

## 8. Responsive Behavior

- Hero h1 scales 128 → 88 → 56 → 40.
- Hero min-height drops to 60vh on mobile.
- Sidebar collapses to drawer at 1024px; on-this-page rail hides at 1280px.
- Wave-form motion disables below 768px (perf + visual noise).
- Light-mode docs available on /docs/* routes only — hero is always dark.

## 9. Agent Prompt Guide

Bias: dark-by-default, mono-everywhere body, Inter-only-on-hero, single electric blue accent, full-bleed gradient hero, 4px tight spacing in body, 1px borders, looping wave motion at low opacity, copy-button on every code block.

Reject: Inter in body or UI, second accent colors, gradients in body surfaces, drop shadows on cards, scroll-triggered animation, mid-page hero re-entries, light-mode hero, sans-serif headings below the fold.

## Creative Tensions (documented for team)

- **Tone whiplash.** Hero feels cinematic, body feels terminal. The risk is incoherence. Resolution: shared accent + shared mono code blocks + zero bridge gradient. The shift is intentional and instant.
- **Motion fatigue.** ElevenLabs-style wave motion can feel like noise on a tool page. Cap at 4–6% opacity, no scroll triggers, loop subtly.
- **Heading discipline.** Resisting Inter for in-body h1 takes restraint — designers will want to "warm it up." Don't. The mono heading is the signature.

## Parent-brand DNA

Tokens traced:
- From Ollama: 22 (pure black surface, mono everywhere body, 1px border depth, code-block pattern, tight 4px scale, copy-button affordance, sidebar shell, mono headings, terminal docs grid)
- From ElevenLabs: 22 (radial gradient hero, electric blue accent, accent glow, Inter Display hero h1, wave-form motion, full-bleed hero panel, generous hero vertical rhythm, soft accent shadow, hero CTA glow)

Net DNA: Ollama 50% · ElevenLabs 50%.
