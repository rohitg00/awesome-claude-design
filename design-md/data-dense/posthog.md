# PostHog — Friendly Data-Dense

Reference DESIGN.md for analytics products that don't want to feel cold. Saturated cobalt + warning yellow on white. Hedgehog-tier personality without losing chart density.

## 1. Visual Theme & Atmosphere

Charts are the hero, but the chrome around them is warm and a bit goofy. Cobalt-blue brand action, yellow warning, black ink. Reads like Grafana that took a design review.

Mood: pragmatic, energetic, slightly mischievous.

## 2. Color Palette & Roles

```
--bg:              #ffffff
--bg-alt:          #f3f4ef
--surface:         #eeefe9
--bg-dark:         #1d1f27
--surface-dark:    #2c2e36
--text:            #000000
--text-muted:      #5f5e5b
--text-dim:        #8a8980
--border:          #d0d1c9
--border-strong:   #b6b6ad
--accent:          #1d4aff
--accent-hover:    #1639cc
--warning:         #f9bd2b
--success:         #29dbbb
--danger:          #db3707

/* categorical chart palette — preserve order */
--chart-1: #1d4aff
--chart-2: #f9bd2b
--chart-3: #29dbbb
--chart-4: #db3707
--chart-5: #621da6
--chart-6: #ff9d3a
--chart-7: #36a2eb
--chart-8: #6a3700
```

Rule: cobalt for action, yellow as warning OR brand-personality fill (never the same surface). Categorical palette assigned in declared order — don't re-roll for aesthetics.

## 3. Typography Rules

- **UI + body:** `Matter`, fallback `Inter`. Weight 400/500/700.
- **Headlines:** Matter weight 700, tracking −1.5%.
- **Code + numerals:** `Matter Mono`, fallback `JetBrains Mono`.

Scale: 11 / 12 / 13 / 14 / 16 / 18 / 22 / 28 / 36 / 48.

Tabular figures globally on metric surfaces.

## 4. Component Stylings

**Buttons**
- Primary: `--accent` fill, white text, radius 6, padding 8/14, weight 500, 1px inset highlight.
- Secondary: white fill, 1px `--border-strong`, black text.
- Brand-personality: `--warning` fill, black text — used for "Try the playground"-class moments only.

**Cards**
- `--bg` fill, 1px `--border`, radius 6. Header bottom-border 1px `--border`.
- Hover: border to `--border-strong`. No lift.

**Inputs**
- 1px `--border-strong`, radius 6, padding 8/12.
- Focus: 2px `--accent` ring, 1px offset.

**Tables**
- Tight: 32px row height. Hairline `--border` separators. Sticky headers on scroll.

**Charts**
- 1px tick marks, `--text-dim` axis labels, gridlines `--border`.
- Tooltip: `--bg-dark` fill, white text, radius 6, padding 8/12.

## 5. Layout Principles

- 1440px max app shell. 12-column.
- 4px base unit. 4/8/12/16/24/32/48 scale.
- Sidebar persistent at 240px. Charts dominate the right pane.

## 6. Depth & Elevation

Border + tonal-shift only on light surfaces. Modals get `0 8px 24px rgba(0,0,0,0.12)`. No card shadows.

## 7. Do's and Don'ts

**Do**
- Use yellow as personality on hero, cobalt for action. Never both as primary CTA.
- Render numbers in tabular Matter Mono.
- Show categorical legends in declared chart-palette order.

**Don't**
- Use cobalt for chart fill if it's also the page CTA — viewers will misread chart bars as buttons.
- Soften corners past 8px.
- Add a sixth UI color outside the categorical chart ramp.
- Drop the hedgehog mascot for "professionalism" — it's the brand's anti-corporate signal.

## 8. Responsive Behavior

- Sidebar collapses to icon rail at 1024px, hidden at 768px.
- Tables transform to stacked KV pairs below 640px.
- Charts compress legend to top instead of right below 768px.

## 9. Agent Prompt Guide

Bias: cobalt action + yellow personality, Matter UI, tabular Matter Mono numerals, 6px radius, hairline table rules, persistent sidebar.

Reject: dark-only themes, gradient charts, three-decimal precision, removing brand personality (mascot, micro-copy), pastel CTAs.
