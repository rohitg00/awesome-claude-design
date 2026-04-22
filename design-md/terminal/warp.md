# Warp — Modern Terminal-Core

Reference DESIGN.md for terminal-aesthetic with chromatic warmth. Mono-first, but neon teal and coral break the ascetic.

## 1. Visual Theme & Atmosphere

Terminal-core, but no longer ascetic. Deep navy bg, two saturated accents (teal action, coral warning), monospace UI. Reads like a CLI that learned to design.

Mood: technical, kinetic, opinionated.

## 2. Color Palette & Roles

```
--bg:              #0b0d14
--bg-alt:          #11141d
--surface:         #161a25
--surface-2:       #1e2331
--text:            #f1f1f4
--text-muted:      #9aa1b3
--text-dim:        #5f6580
--border:          #232838
--border-strong:   #2e3447
--accent:          #16d5e6   /* teal — primary action */
--accent-hover:    #2ee2f0
--accent-warm:     #ff7a59   /* coral — warning, secondary highlight */
--success:         #5ee78a
--danger:          #ff4d6d
```

Rule: teal for action, coral for state change or warning. Never both on the same primitive.

## 3. Typography Rules

- **UI:** `Roobert`, fallback `Inter`, fallback system. Weight 400/500/600.
- **Code + numerals + kbd:** `JetBrains Mono`, fallback `SF Mono`. Weight 400/500.
- Mixed UI is the look — labels in Roobert, values in JetBrains Mono.

Scale: 11 / 12 / 13 / 15 / 17 / 20 / 26 / 34 / 44 / 56.

Mono-tabular numerals everywhere counts appear.

## 4. Component Stylings

**Buttons**
- Primary: `--accent` fill, `#0b0d14` text, radius 8, padding 8/14, weight 500. Subtle 1px highlight on top edge.
- Secondary: `--surface-2` fill, `--text` color, `--border-strong` outline.
- Destructive: `--danger` fill, `#0b0d14` text.

**Cards / blocks**
- `--surface` fill, 1px `--border`, radius 10. Inner content uses 16px padding.
- Code blocks nest with `--bg` fill and 1px `--border`.

**Inputs**
- `--bg-alt` fill, 1px `--border-strong`, radius 8, padding 8/12.
- Focus: 2px `--accent` ring, no offset.

**Keyboard hints**
- Mono character on `--surface-2`, 1px `--border-strong`, radius 4, 11px.

**Command palette**
- Centered modal, `--surface-2`, 12px radius, 24px padding. Result rows on `--bg-alt` hover.

## 5. Layout Principles

- 1280px max marketing, full-width app shell with sidebar.
- 4px base. 4/8/12/16/24/32/48 scale.
- Density first — Warp users tolerate small targets; this is a pro tool.

## 6. Depth & Elevation

Layered surfaces, not shadows. `bg → surface → surface-2` is the entire elevation language. Modals add `0 24px 48px rgba(0,0,0,0.5)`.

## 7. Do's and Don'ts

**Do**
- Mix Roobert and JetBrains Mono in the same row.
- Use teal CTA on coral hero illustration — the brand's signature collision.
- Tabular numerals on every metric.

**Don't**
- Use teal for type color (only background or accent rule).
- Soften corners past 10px.
- Switch to a light theme (Warp ships dark only — honor it).
- Add a third chromatic accent.

## 8. Responsive Behavior

- Sidebar collapses to icon rail at 1024px, full overlay at 768px.
- Command palette goes full-screen below 640px.
- Type scales by one step per breakpoint.

## 9. Agent Prompt Guide

Bias: deep navy bg, teal/coral dual-accent, Roobert UI + JetBrains Mono code, layered surface elevation, tabular numerals, 8/10 radius.

Reject: light themes, gradient buttons, drop shadows on cards, three+ accent colors, sans-only metric numerals.
