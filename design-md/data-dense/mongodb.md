# MongoDB — Data-Dense Atlas

Reference DESIGN.md for developer database UIs: forest-green leaf brand, deep slate chrome, dashboard-first density with marketing surfaces in light editorial.

## 1. Visual Theme & Atmosphere

The cluster is the page. Marketing reads like a developer brochure — light backgrounds, generous whitespace, code panels framed as the hero. The Atlas console flips to deep slate so collection counts, IOPS sparklines, and shard maps stay legible across long on-call windows. One forest-green leaf earns the brand moment; everything else is slate, ink, or a measured chart hue.

Mood: technical, enterprise-trustworthy, never decorative.

## 2. Color Palette & Roles

```
/* marketing surface — light */
--bg:              #ffffff
--bg-alt:          #f9fafb
--surface:         #f3f5f4   /* tinted leaf wash */
--text:            #001e2b   /* slate ink */
--text-muted:      #5d6c74
--border:          #e1e7e4

/* in-app shell — slate */
--bg-app:          #001e2b   /* MongoDB slate */
--bg-app-alt:      #023430
--surface-app:     #0a3a3f
--surface-app-2:   #112c33
--text-app:        #ffffff
--text-app-muted:  #c1c7c6
--border-app:      #1c4a4f

/* brand */
--accent:          #00ed64   /* leaf green, primary CTA + brand */
--accent-hover:    #00c757
--accent-deep:     #00684a   /* forest, ink-on-light variant */
--accent-soft:     #c0fae6   /* tinted callouts */

/* status */
--status-ok:       #00684a
--status-warn:     #b45309
--status-error:    #db3030
--status-info:     #016bf8

/* categorical chart palette — preserve order */
--chart-1: #00684a   /* forest */
--chart-2: #016bf8   /* electric blue */
--chart-3: #b45309   /* amber */
--chart-4: #889397   /* slate gray */
--chart-5: #00d2ff   /* cyan */
--chart-6: #db3030   /* error red */
--chart-7: #5d4caf   /* indigo */
--chart-8: #00ed64   /* leaf — reserve for highlight */
```

Rule: leaf green is reserved for primary action and the brand mark. On dashboards, the deep `--accent-deep` carries text that needs to read as "MongoDB-flavored" without screaming. Status hues are reserved for state; never reuse for arbitrary series.

## 3. Typography Rules

- **UI + body:** `Euclid Circular A`, fallback `Inter`, fallback system. Weight 400/500/700.
- **Headlines:** Euclid weight 500–700. Marketing display tops out near 64px.
- **Numerals:** tabular figures globally on metric tiles, query rows, alert tables.
- **Code + query language:** `Source Code Pro`, fallback `JetBrains Mono`, `SF Mono`. Used for query syntax, log lines, document JSON, shell prompts.

Scale: 11 / 12 / 14 / 16 / 18 / 22 / 28 / 36 / 48 / 64.

Body lines hold a measure of 65–72 characters on marketing pages; in-app rows ignore measure and let tables breathe to viewport.

## 4. Component Stylings

**Buttons**
- Primary: leaf fill `--accent`, slate text, radius 6px, padding 10/18, weight 500.
- Secondary on light: white fill, 1px `--border`, slate text. Hover: `--surface`.
- Secondary on dark shell: transparent fill, 1px `--text-app-muted`, white text.
- Destructive: `--status-error` fill, white text, only on confirm modals.

**Cards / dashboard tiles**
- Marketing: white fill, 1px `--border`, radius 8px, 24px padding.
- App: `--surface-app` fill, 1px `--border-app`, radius 6px, 16px padding. Eyebrow in 11px uppercase tracked +4%.
- Hover: 1px `--accent` border on app tiles. No shadow, no lift.

**Inputs**
- 1px border, radius 6px, padding 10/12. Focus: 2px `--accent` ring with 1px offset.
- Code inputs (Compass shell, Atlas query bar) use `--bg-app-alt` fill on light surfaces — terminal-in-page treatment.

**Tables**
- 32px row height. Hairline border separators. Sticky header in 12px uppercase mono. Tabular numerals throughout. Right-align numerics, left-align strings, center status pills.

**Charts**
- 1px tick marks, axis labels in `--text-app-muted` 11px. Gridlines `--border-app` at 30% opacity.
- Series rendered in `--chart-1..8` declared order. Legend chips top-right with 8px swatch.
- Tooltips: `--bg-app` fill, white text, 1px `--accent-deep` border, radius 4px.

## 5. Layout Principles

- App shell uses 100% viewport. Left nav 240px, content fills.
- Marketing 1200px max, 24px gutter, 12-column.
- 4px base. 4 / 8 / 12 / 16 / 24 / 32 / 48 / 64.
- Dashboards default to 12-column draggable grid; tiles snap to 6/4/3/2 widths.

## 6. Depth & Elevation

Flat. Border + tonal shift only. Modals get `0 16px 48px rgba(0, 30, 43, 0.32)` over a 60% slate scrim. Tooltips lift via 1px accent border, not shadow. Marketing cards get a single `0 1px 2px rgba(0, 30, 43, 0.04)` for soft definition only.

## 7. Do's and Don'ts

**Do**
- Render every metric in tabular Euclid numerals.
- Lock chart series to the declared categorical palette order across all dashboards — colors carry meaning.
- Keep the in-app shell on slate `#001e2b`. Light marketing only.
- Use code panels in the hero — show a `db.collection.aggregate(...)` block, not stock photography.

**Don't**
- Use leaf green for body text or as a tint behind paragraphs.
- Soften corners past 8px on marketing, 6px in-app.
- Replace tabular figures with proportional figures inside metric tiles.
- Add gradient fills under area charts. Solid fills with 30% opacity only.
- Introduce a second brand color "for variety". Leaf is the only branded hue.

## 8. Responsive Behavior

- Left nav collapses to 56px icon rail at 1280px, hidden behind hamburger below 768px.
- Dashboard tiles reflow 12 → 6 → 3 → 1 column at 1440 / 1024 / 768.
- Tables become stacked KV cards below 640px, numbers retained in tabular.
- Code panels in marketing become horizontally scrollable (no soft-wrap of JSON).
- Hero headline scales 64 → 32 on mobile.

## 9. Agent Prompt Guide

Bias: deep slate `#001e2b` app shell paired with light marketing, leaf green `#00ed64` primary action, Euclid Circular A with tabular numerals, 6–8px radii, eight-color categorical chart palette in declared order, dense 32px table rows, persistent left nav, hairline-only borders, code panels as the hero artifact.

Reject: light-mode dashboards, multi-color brand palettes, gradient chart fills, rounded "bubble" tiles, proportional numerals on metrics, hero illustrations in place of code, decorative emoji in chrome, "growth-marketing" pastel washes.
