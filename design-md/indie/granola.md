# Granola — Cult / Indie

Reference DESIGN.md for warm-glass AI notetaker aesthetic. Not in VoltAgent's catalog. Worth cloning.

## 1. Visual Theme & Atmosphere

Warm glass. Editorial serif meets soft frosted surfaces over cream backgrounds. Feels like a premium paper notebook that happens to be software.

Mood: calm, considered, indie-premium.

## 2. Color Palette & Roles

```
--bg:              #faf8f2   /* warm cream */
--bg-gradient:     radial-gradient(at 30% 0%, #fff4e0 0%, transparent 50%),
                   radial-gradient(at 80% 20%, #f4e4d4 0%, transparent 60%);
--surface:         rgba(255, 251, 244, 0.7)   /* frosted warm white */
--text:            #1a1814
--text-muted:      #6a5f52
--border:          rgba(26, 24, 20, 0.08)
--accent:          #b45837   /* muted terracotta */
--accent-soft:     #e4b894
```

## 3. Typography Rules

- **Headlines:** editorial serif — `PP Editorial New`, fallback `Tiempos Headline`. Weight 400–500.
- **Body:** `Söhne`, fallback `Inter`. Weight 400, 16–17px.
- **UI:** Söhne medium, 14px.

Scale: 13 / 15 / 17 / 20 / 26 / 36 / 52.

Light weights dominate. Avoid anything above 600.

## 4. Component Stylings

**Buttons**
- Primary: `--accent` fill, cream text, radius 10, padding 10/18, weight 500.
- Secondary: `--surface` frosted, 1px `--border`, backdrop-blur 12px.

**Cards / notes**
- `--surface` frosted fill, 1px `--border`, radius 14.
- Backdrop-filter `blur(16px) saturate(150%)`.
- Inner highlight `inset 0 1px 0 rgba(255, 255, 255, 0.6)`.

**Inputs**
- Nearly invisible — `--surface` fill, no visible border until focus.
- Focus: 2px `--accent` ring, 2px offset.

## 5. Layout Principles

- Max 680px for reading, 1000px for app shell.
- Gradient fixed on body, content scrolls over it.
- Vertical rhythm: generous, 40–64px section breaks.

## 6. Depth & Elevation

Glass depth. Backdrop blur on every surface. Soft warm shadows `0 8px 32px rgba(180, 88, 55, 0.08)`.

## 7. Do's and Don'ts

**Do**
- Let the warm gradient show through every surface.
- Use serif for any editorial moment (empty states, onboarding).
- Keep weights light; avoid bold.

**Don't**
- Use cold blues or grays — everything bends warm.
- Use Inter for display type.
- Add heavy shadows or hard borders.

## 8. Responsive Behavior

- Gradient simplifies on mobile.
- Blur intensity halved (8px) for performance.
- Single column, generous padding.

## 9. Agent Prompt Guide

Bias: cream base, warm radial gradients, frosted white surfaces, editorial serif for display, light weights, muted terracotta accent.

Reject: cold neutral palettes, sans-serif-only hierarchies, dark-mode primary, high-contrast saturated accents.
