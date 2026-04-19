# ClickHouse — Data-Dense Pro

Reference DESIGN.md for dashboard-first, chart-heavy, saturated-on-charcoal dev-tool aesthetic.

## 1. Visual Theme & Atmosphere

Data-dense pro. Charts are the hero. Tables are hero. Dashboards over marketing pages. Dark-first. Fast. Everything optimized for scanning thousands of rows.

Mood: industrial, precise, performance-obsessed.

## 2. Color Palette & Roles

```
--bg:              #181818
--bg-alt:          #202020
--surface:         #2a2a2a
--text:            #f5f5f5
--text-muted:      #a0a0a0
--text-dim:        #6a6a6a
--border:          #333333
--accent:          #faff69   /* signature yellow */
--accent-alt:      #ff6ec7   /* magenta for contrast */

/* categorical palette for charts */
--series-1:        #faff69
--series-2:        #ff6ec7
--series-3:        #7bdff2
--series-4:        #ffa07a
--series-5:        #b5e48c
--series-6:        #c7a9ff
--series-7:        #ff9b54
--series-8:        #90e0ef

--success:         #b5e48c
--warning:         #ffa07a
--danger:          #ff6b6b
```

## 3. Typography Rules

- **UI / body:** `Inter`, tabular numerals ALWAYS on (`font-variant-numeric: tabular-nums`).
- **Headlines:** Inter, weight 600, tight letter-spacing.
- **Mono / code / data:** `JetBrains Mono`, `SF Mono`. Used for numbers, SQL, logs, IDs.

Scale: 11 / 12 / 13 / 14 / 16 / 20 / 24 / 32.

11–13px dominates. Users read dashboards at arm's length.

## 4. Component Stylings

**Tables**
- Row height 28–32px.
- Zebra striping with `--bg-alt`.
- Sticky header, sticky first column.
- Right-align all numeric columns.
- Truncate with ellipsis, reveal full on hover.

**Charts**
- Grid lines `--border`, axis labels `--text-dim`.
- No 3D. No chartjunk.
- Categorical palette above. Sequential for heatmaps.

**Buttons**
- Primary: `--accent` fill, black text, radius 4px, 12px padding.
- Secondary: `--surface` fill, `--text` color.

**Inputs**
- `--bg-alt` fill, 1px `--border`, radius 4px.
- Mono font for any input that accepts code or IDs.

**Badges**
- Pill-shaped but small (20px tall), mono font, uppercase.

## 5. Layout Principles

- Max width: dashboards use full viewport, no max.
- 4px grid.
- Sidebar 220–260px, collapsible to 48px icon rail.
- Resizable panels everywhere. Users define layout.

## 6. Depth & Elevation

Flat. Depth via background steps (`--bg` → `--bg-alt` → `--surface`). Shadows only on dropdowns and modals.

## 7. Do's and Don'ts

**Do**
- Show more data per screen, not less.
- Make every column sortable.
- Use mono for numbers, IDs, and anything copyable.
- Color-code severity consistently.

**Don't**
- Add marketing illustrations to dashboards.
- Use serif fonts anywhere.
- Animate chart rendering beyond 200ms.
- Center-align numeric data.

## 8. Responsive Behavior

Dashboards don't apologize for being desktop-first. Mobile: show a single KPI per viewport with a drill-down link. Don't cram a 12-column grid into 375px.

## 9. Agent Prompt Guide

Bias: dark canvas, tabular numerals, mono for numbers, saturated categorical palette, 4px grid, dense tables with sticky headers.

Reject: light backgrounds for primary dashboards, hero illustrations, non-tabular numerals, icon libraries that use soft strokes.
