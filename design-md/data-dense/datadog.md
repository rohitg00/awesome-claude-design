# Datadog — Observability Density

Reference DESIGN.md for monitoring dashboards: deep navy chrome, royal-purple brand, warm-cool categorical chart palette tuned for stacked time series at 1px tick precision.

## 1. Visual Theme & Atmosphere

The product is the dashboard. Chrome shrinks, charts dominate, density is the feature. Marketing chrome is light and editorial; the in-app shell is dark navy so multi-series charts pop. One royal purple is the only branded color — everything else is a measured chart hue or a status state.

Mood: dense, technical, on-call, never decorative.

## 2. Color Palette & Roles

```
/* marketing surface — light */
--bg:              #ffffff
--bg-alt:          #f7f6f9
--text:            #110617   /* near-black ink */
--text-muted:      #51495d
--border:          #e3e0e8

/* in-app shell — dark navy */
--bg-app:          #110617   /* deep navy-ink */
--bg-app-alt:      #1a0f23
--surface-app:     #2a1f37
--text-app:        #ffffff
--text-app-muted:  #b8b0c4
--border-app:      #3d3050

/* brand */
--accent:          #632ca6   /* royal purple */
--accent-hover:    #51228a
--accent-soft:     #774aa4   /* tinted purple, hover/highlight */

/* status */
--status-ok:       #29a347
--status-warn:     #f4b400
--status-error:    #d73a49
--status-info:     #4a90e2

/* categorical chart palette — preserve order */
--chart-1: #774aa4   /* purple */
--chart-2: #4a90e2   /* blue */
--chart-3: #29a347   /* green */
--chart-4: #f4b400   /* yellow */
--chart-5: #ec6d3f   /* orange */
--chart-6: #d73a49   /* red */
--chart-7: #2bb5b2   /* teal */
--chart-8: #b86bd9   /* lilac */
```

Rule: status colors (ok/warn/error) are reserved for state. Never reuse green-status for an arbitrary chart series — viewers misread it as "healthy".

## 3. Typography Rules

- **UI + body:** `National 2 Web` (NationalWeb), fallback Helvetica Neue, Arial. Weight 400/500/700.
- **Headlines:** National 2 weight 700. Marketing display goes to 68px.
- **Numerals:** tabular figures globally on dashboards, alerts, query rows.
- **Code + query language:** `Roboto Mono`, fallback `SF Mono`, `JetBrains Mono`. Used for query syntax, log lines, span IDs.

Scale: 11 / 12 / 13 / 14 / 16 / 20 / 28 / 36 / 48 / 68.

## 4. Component Stylings

**Buttons**
- Primary: purple fill, white text, radius 4px, padding 8/14, weight 500.
- Secondary on light: white fill, 1px `--border`, ink text.
- Secondary on dark shell: navy `#110617` fill, 1px white border, white text.
- Destructive: `--status-error` fill, white text, only on confirm modals.

**Cards / dashboard tiles**
- App: `--surface-app` fill, 1px `--border-app`, radius 4px. Header in 12px uppercase eyebrow.
- Marketing: white fill, 1px `--border`, radius 4px.
- Hover: 1px `--accent-soft` border. No shadow, no lift.

**Inputs**
- 1px border, radius 4px, padding 6/10. Focus: 2px purple ring, 1px offset.

**Tables**
- 28px row height. Hairline border separators. Sticky header in 11px uppercase mono. Tabular numerals throughout. Right-align numbers, left-align strings.

**Charts**
- 1px tick marks, axis labels in `--text-app-muted` 11px. Gridlines `--border-app` at 30% opacity.
- Series rendered in `--chart-1..8` declared order. Legend chips top-right with 8px swatch.
- Tooltip: `--bg-app` fill, white text, 1px `--accent-soft` border, radius 4px.

## 5. Layout Principles

- App shell uses 100% viewport. Left nav 200px, content fills.
- Marketing 1280px max, 24px gutter, 12 column.
- 4px base. 4 / 8 / 12 / 16 / 24 / 32 / 48.
- Dashboards default to 12-column draggable grid, tiles snap to 6/4/3/2 widths.

## 6. Depth & Elevation

Flat. Border + tonal shift only. Modals get `0 16px 48px rgba(17, 6, 23, 0.40)` over a 60% scrim. Tooltips lift via 1px accent border, not shadow.

## 7. Do's and Don'ts

**Do**
- Render every metric in tabular National numerals.
- Lock chart series to the declared categorical palette order across all dashboards — colors carry meaning across views.
- Keep the in-app shell on `#110617` navy. Light mode is for marketing only.

**Don't**
- Use status green for arbitrary chart series.
- Soften corners past 4px — this is dashboard chrome, not a SaaS card.
- Replace tabular figures with proportional figures inside metric tiles.
- Add gradient fills under area charts. Solid fills with 30% opacity only.
- Introduce a second brand color "for variety". Purple is the only branded hue.

## 8. Responsive Behavior

- Left nav collapses to 48px icon rail at 1280px, hidden behind hamburger below 768px.
- Dashboard tiles reflow 12 → 6 → 3 → 1 column at 1440 / 1024 / 768.
- Tables become stacked KV cards below 640px, numbers retained in tabular.
- Chart tooltips become bottom-sheet on mobile.

## 9. Agent Prompt Guide

Bias: deep navy `#110617` app shell, royal-purple `#632ca6` brand, National 2 with tabular numerals, 4px radii, 8-color categorical chart palette in declared order, dense 28px table rows, persistent left nav, hairline-only borders.

Reject: light-mode dashboards, multi-color brand palettes, gradient chart fills, rounded "bubble" tiles, proportional numerals on metrics, hero illustrations on the in-app shell, decorative emoji in chrome.
