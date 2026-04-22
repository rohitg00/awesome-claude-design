# Brand Extraction — URL → DESIGN.md

Point Claude Design at any live URL, get back a `DESIGN.md` describing that brand's system. For competitive analysis, brand handovers, and remix research.

<img src="../assets/tags/curated.svg" alt="curated"> <img src="../assets/tags/new.svg" alt="new">

---

## Goal

Reverse-engineer a brand's design system from its public site. Tokens, type, components, layout rules — without contacting the company.

## Time

| Step | Wall-clock |
|---|---|
| 1. Identify URL set | 1 min |
| 2. Run extraction prompt | 3 min |
| 3. Diff against assumptions | 5 min |
| 4. Save to repo | 1 min |
| **Total** | **~10 min** |

## Inputs

- A canonical URL (homepage usually)
- Optional: 3–5 supporting URLs (pricing, docs, blog) for breadth
- Pro/Max/Team Claude Design plan (web capture is gated)

## Steps

### 1. Pick the right URLs

Homepage alone misses dashboards. Use:

- Marketing homepage — hero patterns, brand voice
- Pricing — table density, mono numerals
- Docs — long-form rhythm, code-block style
- App / dashboard (if public preview exists) — chrome, density
- Mobile site (if separate) — responsive proof

### 2. Run extraction

```
Read the live sites at the URLs below. Use web capture to grab
computed CSS for the hero, primary CTA, body text, and
navigation on each.

URLs:
- {marketing}
- {pricing}
- {docs}
- {app or product preview}

Produce a DESIGN.md following the 9-section canonical format:

1. Visual Theme & Atmosphere — describe what kind of product
   this looks like to a designer
2. Color Palette & Roles — extract every used color, propose
   role names (--bg, --accent, etc.). Hex only.
3. Typography Rules — list every font-family detected, classify
   (display/body/UI/mono), produce a modular scale from
   computed font-size values
4. Component Stylings — Button (primary/secondary), Card, Input,
   Nav minimum. Extract from computed CSS.
5. Layout Principles — measure max-width, gutter, column count
6. Depth & Elevation — list every shadow/border style detected
7. Do's and Don'ts — infer from consistent patterns
8. Responsive Behavior — describe breakpoint transitions if
   visible
9. Agent Prompt Guide — bias + reject clauses, including AI-slop
   patterns this brand explicitly avoids

Each section ≤ 150 words. Hex colors with role names. No
marketing copy.

End with a "Confidence" line: HIGH / MEDIUM / LOW per section,
based on how much was directly observed vs inferred.
```

### 3. Diff against assumptions

You probably had a hunch about the brand before running this. Check:

- Did you assume Inter and the brand actually uses Söhne?
- Did you assume one accent and they use two?
- Did you miss the mono numeral choice in their pricing table?

Revise the file. Note disagreements in a `## Inferred vs Observed` section at the bottom — useful when you re-extract in 6 months.

### 4. Save to repo

Place under `/design-md/<family>/<brand>.md` in [awesome-claude-design](https://github.com/rohitg00/awesome-claude-design) or your own catalog. PR welcome.

## Quality Checks

- [ ] Every color token sourced from computed CSS, not screenshot pixels
- [ ] Type families verified via `font-family` (not visual eyeballing)
- [ ] At least one "reject" rule cites a pattern the brand explicitly avoids
- [ ] Confidence labels per section
- [ ] Component stubs match the actual brand when rendered
- [ ] No `#abcdef`-style placeholder hex remains

## Variations

- **Competitor matrix:** extract 4 competitors in the same family, produce a comparative spreadsheet of token deltas
- **Pre-pitch deck:** extract a target client's brand, then build the deck *in their system* before the meeting
- **Acquisition handover:** extract both companies, run [`/recipes/...two-brand-remix.md`](#) to propose post-merger system

## Common Failures

- **Brand uses dynamic type-scaling — extracted scale looks weird.** Cause: `clamp()` usage. Fix: extract at three viewport widths (375 / 1024 / 1440) and present three scales.
- **Capture missed the dashboard.** Cause: dashboards are auth-gated. Fix: use public marketing screenshots from press kit, label confidence LOW for component section.
- **Output names colors after the brand.** Cause: extraction defaulted to `--linear-purple`. Fix: re-prompt with "use functional names (`--accent`, `--surface`), never brand names."
- **Two brands, same DESIGN.md.** Cause: agent merged tokens from press-kit URL and product URL when they have different systems. Fix: re-extract with stricter URL list, drop press-kit.

## Ethics & Legal

- Trademarks remain the original brand's. Note this in your `DESIGN.md` header.
- "Inspired by X's public site" framing is fine. "Official X system" is not.
- Don't republish proprietary assets (logo SVGs, photography). Tokens are observable; assets are owned.
