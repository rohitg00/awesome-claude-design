# OpenCode AI — Terminal Native

Reference DESIGN.md for OSS terminal coding agent: near-black canvas, off-white text, phosphor-green action, IBM Plex Mono everywhere, hard edges.

## 1. Visual Theme & Atmosphere

Terminal native. The page reads like the product — a TUI rendered in HTML. Near-black canvas, off-white text, monospace from chrome to body. The only color belongs to the prompt cursor, the active line, and the accept-action: a single phosphor green. Nothing scales on hover, nothing softens past 4px, nothing exists that wouldn't render in 256-color terminal mode.

Mood: ascetic, kinetic, opinionated, OSS-honest.

## 2. Color Palette & Roles

```
--bg:              #080808   /* near-black canvas */
--bg-alt:          #0f0f0f
--surface:         #161616   /* terminal cell elevation */
--surface-2:       #1f1f1f
--text:            #d2d2d2   /* off-white, primary */
--text-muted:      #8a8a8a
--text-dim:        #5a5a5a
--border:          #2a2a2a
--border-strong:   #3a3a3a

--accent:          #50fa7b   /* phosphor green — primary action + active state */
--accent-hover:    #6fff95
--accent-deep:     #2cc955

/* terminal-palette echoes — used in syntax + diffs only */
--cyan:            #8be9fd
--purple:          #bd93f9
--yellow:          #f1fa8c
--orange:          #ffb86c
--red:             #ff5555   /* error, deletion */
--green-deep:      #5af78e   /* addition */
--pink:            #ff79c6
```

Rule: green carries action, active cursor, and accepted state. The terminal-palette echoes (`--cyan`, `--purple`, etc.) appear inside diffs, syntax highlighting, and log streams only. Never as marketing accents. Never gradient between them.

## 3. Typography Rules

- **Everything:** `IBM Plex Mono`, fallback `JetBrains Mono`, `SF Mono`, `Menlo`, `Consolas`, `monospace`. Weight 400/500/700.
- One typeface across chrome, body, code, headlines. Mixed weights carry hierarchy — never mixed faces.
- **Numerals:** native to mono (always tabular).
- Letter-spacing 0. Line-height 1.5 on body, 1.4 on code.

Scale: 12 / 13 / 14 / 16 / 18 / 22 / 28 / 36 / 48.

Headlines stay restrained — IBM Plex Mono at 36–48px reads as ASCII banner, not magazine display. Hero copy can lean on multi-line ASCII art for the brand moment.

## 4. Component Stylings

**Buttons**
- Primary: green fill `--accent`, near-black text `--bg`, radius 4px, padding 8/14, weight 500. Hover: `--accent-hover`. No lift, no scale.
- Secondary: transparent fill, 1px `--border-strong`, off-white text. Hover: 1px `--accent` border.
- Tertiary / link: off-white text, green underline on hover.
- Destructive: `--red` fill, near-black text, only on confirm modals.

**Cards / blocks**
- `--surface` fill, 1px `--border`, radius 4px. Padding 16. Header in 12px uppercase tracked +4%.
- Code blocks: `--bg-alt` fill, 1px `--border`, no header chrome unless filename is shown in 12px muted mono.
- Hover: 1px `--accent` border. No shadow, no lift.

**Inputs / prompt**
- `--bg-alt` fill, 1px `--border-strong`, radius 4px, padding 8/12.
- Focus: 1px `--accent` border (no offset, no ring — terminal-honest).
- Active prompt line: 1px `--accent` left border, blinking caret in `--accent`.

**Nav**
- Top nav: `--bg` fill, 1px bottom `--border`, mono links, green underline on active.
- ASCII-style breadcrumb (`~/docs/getting-started`) for in-app navigation.

**Diff + log views**
- Additions in `--green-deep`, deletions in `--red`, both at 12% opacity background plus full-opacity text.
- Line numbers in `--text-dim`, gutter in `--bg-alt`.
- ANSI-color log lines preserved (`--cyan` for paths, `--purple` for keywords, `--yellow` for warnings).

## 5. Layout Principles

- 1024px max for marketing reading. Full-width app shell.
- Single-column hero. Two-column max for spec / install steps.
- 4px base. 4 / 8 / 12 / 16 / 24 / 32 / 48.
- Density first. Generous vertical whitespace is anti-terminal — keep blocks tight.
- Code is the hero. Show a real session transcript above the fold.

## 6. Depth & Elevation

Flat. Border + tonal shift only. No drop shadows. No glows. The entire elevation language is `bg → bg-alt → surface → surface-2`. Modals use `--surface-2` with a 1px `--accent` border instead of shadow.

## 7. Do's and Don'ts

**Do**
- Use IBM Plex Mono across every surface — chrome, body, code.
- Reserve green for action, active line, accepted state.
- Show real session transcripts as the hero artifact (no stylized mockups).
- Keep corners at 4px. Hard edges read as terminal cells.
- Render ASCII banners for section breaks.

**Don't**
- Introduce a second typeface. Mono everywhere or nothing.
- Soften corners past 6px.
- Use light backgrounds. OpenCode is dark only.
- Add gradient fills, glows, or scale-on-hover lifts.
- Use the terminal-palette echoes (`--cyan`, `--purple`) outside of diff and log surfaces.

## 8. Responsive Behavior

- Single-column hero scales naturally. Mono body holds 14–16px on mobile.
- Nav collapses to drawer at 768px; ASCII breadcrumb truncates left-side.
- Code blocks become horizontally scrollable below 640px (no soft-wrap of code).
- Diff views become unified (single column) instead of split below 768px.

## 9. Agent Prompt Guide

Bias: near-black `#080808` canvas with off-white `#d2d2d2` text, single phosphor-green `#50fa7b` accent for action and active state, IBM Plex Mono across every surface (chrome, body, code), 4px radii, terminal-palette echoes reserved for diffs and log streams only, real session transcripts as hero, ASCII breadcrumbs and section banners.

Reject: light-mode pages, multi-typeface mixing (sans + mono), gradient fills, drop shadows, scale-on-hover lifts, decorative illustration in chrome, stock photography, marketing-pastel accents, the terminal-palette echoes leaking into chrome.
