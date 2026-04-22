# Vercel — Editorial Grayscale

Reference DESIGN.md for grayscale-only editorial. No accent. Geometry and type carry the entire identity.

## 1. Visual Theme & Atmosphere

Editorial minimalism stripped further than Linear. Pure greyscale ramp, geometric grotesque, hairline rules. The product brand says "we don't need a color to look expensive."

Mood: severe, fast, infrastructural.

## 2. Color Palette & Roles

```
--bg:              #ffffff
--bg-alt:          #fafafa
--surface:         #f4f4f4
--bg-dark:         #000000
--surface-dark:    #0a0a0a
--surface-dark-2:  #111111
--text:            #000000
--text-muted:      #666666
--text-dim:        #8f8f8f
--border:          #ebebeb
--border-strong:   #d4d4d4
--accent:          #000000   /* yes, black is the accent */
--accent-inverse:  #ffffff   /* on dark surfaces */
```

Rule: no chromatic accent anywhere. State color (success/error) only on alerts and form validation. CTAs are filled black on white, filled white on black.

## 3. Typography Rules

- **Headlines + body + UI:** `Geist Sans`, fallback `system-ui`. Weight 400/500/600.
- **Mono:** `Geist Mono`, fallback `SF Mono`.
- Display sizes use weight 600 with tight tracking (−2%).

Scale: 12 / 13 / 14 / 16 / 18 / 24 / 32 / 48 / 64 / 96.

No serif. No italics. No second font family.

## 4. Component Stylings

**Buttons**
- Primary: `--accent` fill (black), white text, radius 6, padding 8/16, weight 500.
- Secondary: white fill, 1px `--border-strong`, black text.
- Ghost: black text, hover underline only.

**Cards**
- 1px `--border` only. Radius 12. No background fill on light mode, `--surface-dark` on dark.
- Hover: border to `--border-strong`. Never lift.

**Inputs**
- 1px `--border-strong`, radius 6, padding 8/12.
- Focus: 2px black ring on light, 2px white ring on dark.

**Tables**
- Hairline rules only. Header bottom-border 1px `--text`. Row separators 1px `--border`.

## 5. Layout Principles

- 1200px max for marketing, 1440px for app shells, 24px gutter.
- 4px base unit. 4/8/12/16/24/32/48/64/96 spacing scale.
- Generous vertical rhythm at marketing surfaces (96px section breaks). Tight in dashboards.

## 6. Depth & Elevation

Flat. Border depth only. Pop-overs use `0 1px 2px rgba(0,0,0,0.06)` and a 1px border. Buttons never carry shadow.

## 7. Do's and Don'ts

**Do**
- Use black fill as the only "color" of emphasis.
- Set body line-height 1.6 in marketing, 1.4 in app.
- Render code blocks with Geist Mono on `--surface`.

**Don't**
- Add a brand accent color.
- Use gradients other than the corporate triangle (and only in hero illustration).
- Round corners beyond 12px.
- Use Geist below 12px — falls apart on macOS subpixel.

## 8. Responsive Behavior

- Top-nav collapses to slide-over at 768px. No bottom-nav.
- Tables wrap to two-line key-value pairs below 640px.
- Hero type scales 96 → 48 → 36 across breakpoints.

## 9. Agent Prompt Guide

Bias: Geist everywhere, single grayscale ramp, hairline borders, 6/12 radius, black-on-white CTAs, generous marketing whitespace.

Reject: chromatic accents, drop shadows on cards, gradient buttons, second font family, rounded pill UI.
