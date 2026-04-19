# Linear — Editorial Minimalism

Reference DESIGN.md for calm-neutral SaaS with one surgical purple accent.

## 1. Visual Theme & Atmosphere

Editorial minimalism. Surgical. Understated. Every pixel earns its place. Inspired by late-90s Swiss graphic design meeting modern SaaS.

Mood: precise, fast, quietly confident.

## 2. Color Palette & Roles

```
--bg:              #ffffff   /* light mode */
--bg-alt:          #fafafa
--surface:         #f4f4f5
--bg-dark:         #0f0f14   /* dark mode base */
--surface-dark:    #1a1a20
--text:            #0f0f14
--text-muted:      #6b6b76
--text-dim:        #a0a0ab
--border:          #e4e4e7
--border-strong:   #d4d4d8
--accent:          #5e6ad2   /* Linear purple, use sparingly */
--accent-hover:    #4e5acb
```

Rule: accent only on primary action, link underlines, and focus rings. Never on backgrounds.

## 3. Typography Rules

- **Headlines + body:** `Inter`, fallback system-ui. Weight 400/500/600. Letter-spacing −0.5% at headline sizes.
- **UI labels:** Inter, weight 500, 13–14px.
- **Mono:** `Berkeley Mono`, fallback `SF Mono`.

Scale: 11 / 13 / 14 / 16 / 18 / 22 / 28 / 36 / 48 / 64.

No serif. No italics for emphasis — use weight 600.

## 4. Component Stylings

**Buttons**
- Primary: `--accent` fill, white text, radius 6px, padding 8/14, weight 500.
- Secondary: `--surface` fill, `--text` color, `--border` outline.
- Ghost: text-only, accent on hover.

**Cards**
- `--bg-alt` background, `--border` 1px, radius 8px.
- Hover: border shifts to `--border-strong`. No shadow ever.

**Inputs**
- 1px `--border`, radius 6px, padding 8/12.
- Focus: 2px `--accent` ring, 2px offset.

**Keyboard hints**
- `kbd` styled as outlined mono characters, 11px, `--surface` background, `--border` outline, 4px radius.

## 5. Layout Principles

- 1200px max, 24px gutter, 12-column.
- 4px base unit. 4/8/12/16/24/32/48/64 spacing scale.
- Dense by default. Information per pixel is the goal.

## 6. Depth & Elevation

Flat. Border-based depth only. Shadows reserved for popovers and dropdowns (single `0 2px 8px rgba(0,0,0,0.04)`).

## 7. Do's and Don'ts

**Do**
- Use Linear purple as punctuation, not paragraph.
- Keep UI density high — users are pros.
- Ship keyboard shortcuts. Surface them in the UI.

**Don't**
- Round corners beyond 8px.
- Use drop shadows on cards or buttons.
- Introduce a second accent color.
- Apply gradients to anything.

## 8. Responsive Behavior

- Sidebar collapses to bottom-nav at 768px.
- Tables transform to stacked key-value pairs below 640px.
- Headlines scale down one step per breakpoint.

## 9. Agent Prompt Guide

Bias: high information density, Inter everywhere, one purple accent, 1px borders, 8px radius max, keyboard-first UX.

Reject: shadowed cards, multi-color palettes, rounded pills, icon-heavy interfaces, hero illustrations.
