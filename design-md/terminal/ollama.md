# Ollama — Terminal-Core

Reference DESIGN.md for monochrome, mono-everywhere, CLI-first aesthetic.

## 1. Visual Theme & Atmosphere

Terminal-core. Black and white. Monospace. No decoration. Feels like a well-formatted man page. The product is the command; the UI gets out of the way.

Mood: precise, pragmatic, unceremonious.

## 2. Color Palette & Roles

```
--bg:             #000000
--bg-alt:         #0a0a0a
--surface:        #111111
--text:           #ffffff
--text-muted:     #8a8a8a
--text-dim:       #5a5a5a
--border:         #1f1f1f
--accent:         #ffffff   /* NO chromatic accent */
--inverse-bg:     #ffffff
--inverse-text:   #000000
```

Rule: no color. Contrast is a feature. If you reach for a hue, reconsider.

## 3. Typography Rules

- **Everything:** monospace. `SF Mono`, `JetBrains Mono`, `IBM Plex Mono`, fallback `ui-monospace`.
- Weights: 400 regular, 600 for emphasis. No 300 or 700.
- Line-height: 1.5 body, 1.2 headings.
- Tabular numerals always on.
- No italics. No small-caps.

Type scale: 12 / 14 / 16 / 20 / 28 / 40. That's it.

## 4. Component Stylings

**Buttons**
- Primary: white fill, black text, no radius (0px). Hover: invert.
- Secondary: 1px white border, white text, transparent. Hover: fill white.
- No ghost buttons. If it needs to disappear, it should not be there.

**Inputs**
- 1px `--border`, 0px radius. Focus: 1px white border, no glow.
- Placeholder in `--text-dim`.

**Cards**
- No card. Use `--border` lines to section content.

**Code blocks**
- Inline: `--bg-alt` background, 2px padding.
- Block: `--bg-alt` background, 1px `--border`, 16px padding, no radius.

**Navigation**
- Horizontal text links, divider `|` between items. Active: underline.

## 5. Layout Principles

- Single-column dominant. 720px max readable width.
- 8px base unit. No 10, no 12. 8, 16, 24, 32.
- Page sections separated by horizontal rules, not whitespace gaps.

## 6. Depth & Elevation

Zero depth. Ever. No shadows. No gradients. No transforms.

## 7. Do's and Don'ts

**Do**
- Treat every pixel as a character cell.
- Use ASCII-art where appropriate (tree views, box drawings).
- Write copy in imperative: "run this", "install that".

**Don't**
- Introduce color.
- Use rounded corners.
- Animate anything that isn't feedback (loading spinner = OK, hover lift = no).
- Add illustrations, mascots, or decorative graphics.

## 8. Responsive Behavior

- Collapses gracefully to 360px.
- Horizontal rules become edge-to-edge.
- Monospace preserves layout even at narrow widths.

## 9. Agent Prompt Guide

Bias toward: pure monochrome, mono type, sharp corners, ASCII diagrams, imperative copy.

Reject: any hex code that isn't `#000`, `#fff`, or a gray between. Icon libraries. Rounded buttons. Hero gradients.

When in doubt, remove something.
