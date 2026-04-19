# Arc Browser — Glass / Soft-Futurism

Reference DESIGN.md for frosted translucency, pastel gradients, soft geometry.

## 1. Visual Theme & Atmosphere

Glass and soft-futurism. Layered translucency, backdrop blur, pastel radial gradients. Feels like holding a piece of technology from 2035.

Mood: premium consumer, optimistic, tactile.

## 2. Color Palette & Roles

```
--bg:              #fafaff
--bg-gradient:     radial-gradient(at 20% 0%, #ffe0f0 0%, transparent 50%),
                   radial-gradient(at 80% 30%, #d4e4ff 0%, transparent 50%),
                   radial-gradient(at 50% 100%, #e0d4ff 0%, transparent 50%);
--surface:         rgba(255, 255, 255, 0.6)   /* frosted */
--surface-strong:  rgba(255, 255, 255, 0.85)
--text:            #0f0f14
--text-muted:      #5a5a68
--border:          rgba(255, 255, 255, 0.5)
--border-alt:      rgba(15, 15, 20, 0.08)
--accent:          #8b5cf6
--accent-soft:     #c4b5fd
```

## 3. Typography Rules

- **Headlines:** custom grotesque with slight warmth. `PP Neue Montreal`, fallback `Inter`. Weight 500.
- **Body:** `Inter`, weight 400, 16px.
- **UI:** Inter medium.

Scale: 13 / 15 / 17 / 20 / 26 / 36 / 52 / 72.

## 4. Component Stylings

**Buttons**
- Primary: `--accent` fill, white text, radius 12px, subtle inner highlight.
- Secondary: `--surface` (frosted), 1px `--border`, backdrop-filter `blur(12px)`.

**Cards**
- `--surface` fill, 1px `--border`, radius 16–20px.
- Backdrop-filter `blur(20px) saturate(160%)`.
- Inner highlight: `inset 0 1px 0 rgba(255,255,255,0.6)`.

**Inputs**
- `--surface` fill, 1px `--border-alt`, radius 12px.
- Focus: 2px `--accent` ring with 2px offset.

**Navigation**
- Floating pill at top. `--surface-strong`, backdrop-blur, shadow `0 4px 16px rgba(15,15,20,0.08)`.

## 5. Layout Principles

- 1200px max, 32px gutter.
- Background gradient is fixed-position on the body, content scrolls over it.
- Corner radii are generous (12–24px).

## 6. Depth & Elevation

Depth is the whole game. Use:
- Backdrop blur for surfaces.
- Soft shadows `0 8px 32px rgba(15,15,20,0.08)`.
- Inner highlights for glass quality.

## 7. Do's and Don'ts

**Do**
- Use `backdrop-filter: blur()` on every surface.
- Layer translucent surfaces over colorful gradients.
- Keep shadows soft and warm.

**Don't**
- Use hard-edged solid surfaces — they break the aesthetic.
- Use neon saturation — glass is about subtle color.
- Forget fallbacks for browsers without backdrop-filter.

## 8. Responsive Behavior

- Gradients simplify to two radial points below 768px (performance).
- Blur intensity reduced to 8px on mobile.
- Floating pill nav collapses to bottom bar.

## 9. Agent Prompt Guide

Bias: pastel radial gradients on the body, frosted white surfaces with backdrop-blur, soft purple accent, 16–20px radii, inner highlights for glass quality.

Reject: opaque surfaces without translucency, dark-mode-first designs, hard geometric elements, saturated neon.
