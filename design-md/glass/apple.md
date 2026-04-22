# Apple — Glass / Soft-Futurism Reference

Reference DESIGN.md for premium consumer software with translucent surfaces. SF Pro everywhere, system tints sparingly, vibrancy materials over solid fills.

## 1. Visual Theme & Atmosphere

Soft futurism. Frosted vibrancy materials, layered translucency, SF Pro at every size, system tints used as accent rather than fill. Hardware-adjacent — every surface implies physical depth.

Mood: calm, premium, trustworthy.

## 2. Color Palette & Roles

```
/* light */
--bg:                  #ffffff
--bg-elevated:         #ffffff
--surface-grouped:     #f2f2f7
--separator:           rgba(60,60,67,0.18)
--text:                #1d1d1f
--text-secondary:      rgba(60,60,67,0.78)
--text-tertiary:       rgba(60,60,67,0.55)

/* dark */
--bg-dark:             #000000
--bg-elevated-dark:    #1c1c1e
--surface-grouped-dark:#2c2c2e
--separator-dark:      rgba(84,84,88,0.65)

/* system tints (use sparingly, one per surface) */
--system-blue:         #007aff
--system-green:        #34c759
--system-red:          #ff3b30
--system-orange:       #ff9500
--system-purple:       #af52de
--system-pink:         #ff2d55
--system-yellow:       #ffcc00

/* vibrancy materials (alpha over backdrop blur) */
--material-thin:       rgba(255,255,255,0.6)
--material-regular:    rgba(255,255,255,0.78)
--material-thick:      rgba(255,255,255,0.92)
```

Rule: pick one system tint per surface and use it for the primary action only. Materials replace solid fills on overlays, navigation bars, sidebars.

## 3. Typography Rules

- **All UI + body:** `SF Pro Text` (≤19px), `SF Pro Display` (≥20px). Fallback `system-ui`.
- **Mono / code:** `SF Mono`, fallback `Menlo`.
- Use Apple's optical sizing — never disable `font-optical-sizing`.

Scale: 11 / 12 / 13 / 15 / 17 / 22 / 28 / 34 / 44 / 56 (matches Apple HIG).

Body 17px on touch, 13px on dense desktop.

## 4. Component Stylings

**Buttons**
- Primary: `--system-blue` fill, white text, radius 12, padding 10/20, weight 600.
- Bordered: clear fill, 1px `--system-blue`, blue text.
- Plain: text-only blue, no border.

**Cards / sections**
- `--bg-elevated` fill (light) or `--bg-elevated-dark` (dark), radius 14, no border.
- Grouped lists: `--surface-grouped`, separator hairline between rows.

**Sheets / modals**
- `--material-regular` over backdrop blur 30px. Rounded top corners 16px. Detents at 50% / 100%.

**Inputs**
- `--surface-grouped` fill, no border, radius 10, padding 11/14.
- Focus: 4px outer halo using current system tint at 18% alpha.

**Navigation**
- Nav bars use `--material-thin` over content. Title type weight 600. Large-title pattern: 34px → 17px on scroll.

## 5. Layout Principles

- Touch targets ≥44pt. Desktop dense ≥28pt.
- 8pt base unit. 4 / 8 / 12 / 16 / 20 / 24 / 32 / 44 / 56 / 80 scale.
- Safe-area inset everywhere on mobile. Edge-to-edge content; chrome floats above.

## 6. Depth & Elevation

Material layering replaces shadows on iOS. macOS uses subtle `0 1px 0 rgba(0,0,0,0.04)` divider plus material backdrop. Never drop-shadow over a material — defeats the blur.

## 7. Do's and Don'ts

**Do**
- Use one system tint per screen for primary action.
- Apply `backdrop-filter: blur(30px) saturate(180%)` on translucent surfaces.
- Honor SF Pro optical sizing thresholds (Text ≤19px, Display ≥20px).

**Don't**
- Mix system tints on the same surface.
- Replace SF Pro with Inter — kills the platform feel instantly.
- Drop-shadow buttons, cards, or inputs.
- Use hard 1px borders on cards; use radius + material instead.

## 8. Responsive Behavior

- iOS: sheet detents adapt to content height. Large-title shrinks on scroll.
- macOS: sidebar uses `NSSplitViewController` ratios — 240/flex.
- iPadOS: column layouts collapse on size class transitions.
- Web/PWA: prefer `env(safe-area-inset-*)` and `@media (prefers-color-scheme)`.

## 9. Agent Prompt Guide

Bias: SF Pro everywhere with optical-size respect, system tints as accent (one per surface), vibrancy materials over solid fills, 12/14 radius, no card borders.

Reject: Inter substitution, multi-tint surfaces, shadowed cards, Material Design ripples, hard 1px borders on cards.
