# Tweaks Panel — No-Regen Iteration

The Tweaks panel is the cheapest surface in Claude Design. Reorder sections, swap variants, retune spacing — all without re-prompting and without burning vision tokens. This recipe covers when to use it (and when not to).

<img src="../assets/tags/curated.svg" alt="curated"> <img src="../assets/tags/new.svg" alt="new">

---

## Goal

Use the Tweaks sidebar for layout-level edits that would otherwise cost a chat round. Comment on elements for component-level edits. Reserve chat for structural or conceptual changes. The result: weekly allowance lasts 3–5x longer.

## Time

| Step | Wall-clock |
|---|---|
| 1. Generate the first artifact | (skip — assume already done) |
| 2. Open Tweaks panel | 5 sec |
| 3. Reorder sections | 1–2 min |
| 4. Swap variants on cards / heroes | 1–2 min |
| 5. Tune spacing + density tokens | 2–3 min |
| 6. Commit and continue | — |
| **Total per iteration** | **~5 min, ~zero tokens** |

## Inputs

- A generated artifact in Claude Design (page, deck, prototype) you want to refine
- Knowledge of which knobs the Tweaks panel exposes for that artifact type
- The mental model below: which edit goes where

## The three iteration surfaces

There are three ways to change a Claude Design artifact, and they cost wildly different amounts:

| Surface | Use for | Token cost |
|---|---|---|
| **Tweaks panel** | Layout: reorder, swap variants, density, spacing scale, accent intensity | ~0 (no LLM call) |
| **Inline comments** | Component-level edits: "this card needs more padding," "wrong icon" | Low (local re-render) |
| **Chat re-prompt** | Structural changes: new section, different page intent, conceptual pivot | High (full vision pass) |

The mistake every new user makes: chat-prompting every change. Per Austin Lau (Anthropic), the [Tweaks panel demo](https://x.com/helloitsaustin/status/2045176910569980318) shows this explicitly — section reordering and variant swaps happen in the sidebar, not the chat.

## Steps

### 1. Open the Tweaks panel

In any generated artifact, look for the **Tweaks** sidebar (right edge of the canvas in current preview build; collapsed by default on narrow viewports). Knobs typically include:

- **Section order** — drag handles to reorder hero / features / pricing / footer
- **Section variant** — swap "three-column features" for "two-column with image"
- **Density** — compact / comfortable / spacious
- **Spacing scale** — tighten or loosen the global modular scale
- **Accent intensity** — how often the accent color appears (subtle / standard / loud)
- **Component variants** — for hero, card, nav: pick from 2–4 pre-derived variants from your DESIGN.md

The exact knob set varies by artifact type. Decks expose slide-template knobs; prototypes expose nav-pattern knobs; landing pages expose section-order + variant.

### 2. Reorder sections

Most common no-regen win. Drag a section in the Tweaks panel — Claude reorders without re-rendering the section content. Hero stays the hero, just appears earlier or later.

Use this when:

- Your social-proof section should come *before* the feature grid (common edit)
- The pricing teaser belongs above the footer-CTA, not below
- You want to A/B-style two layouts: drag, screenshot, drag back, screenshot

Do **not** use chat for this. Chat will regenerate every section.

### 3. Swap variants

Each section type has 2–4 variants pre-derived from your DESIGN.md tokens. The panel shows them as thumbnails. Click to swap — same content, different layout.

Examples:

- Hero: "type-only" / "split with image" / "centered with screenshot" / "video background"
- Features: "three-card grid" / "two-column with icon" / "tabbed list" / "comparison table"
- Pricing: "three-tier" / "single-CTA" / "feature matrix" / "calculator widget"

If the variant you want isn't in the panel, *that's* a chat re-prompt (you're asking for a new variant Claude hasn't pre-derived). Otherwise, never chat for a variant swap.

### 4. Tune spacing + density

The density slider quietly does a lot. Compact = tighter padding, smaller type scale, denser cards. Spacious = the opposite. Most "this looks too crowded" or "this feels empty" complaints fix here.

Watch the meter: density and spacing changes are zero-token because they're CSS variable tweaks, not regenerations. You can scrub them live.

### 5. Commit and continue

Once the layout is right, lock it via the panel and move to inline comments for component-level edits. Save chat for the next structural change.

## When to use which surface

A practical decision tree:

```
Did the *content* change? → chat re-prompt (expensive but necessary)
Did a *new section type* appear? → chat re-prompt
Did the page *intent* change? → chat re-prompt

Did a section *move*? → Tweaks panel (free)
Did a variant *swap*? → Tweaks panel (free)
Did density / spacing *shift*? → Tweaks panel (free)

Did a single *component* need fixing? → inline comment (cheap)
Did a button copy / icon / label change? → inline comment (cheap)
Did one card need more padding? → inline comment (cheap)
```

Print this near your monitor for a week. After that you'll have it internalized.

## Quality Checks

- [ ] Section reorder happened in Tweaks, not chat
- [ ] Variant swaps happened in Tweaks, not chat
- [ ] Density / spacing tuned via slider, not chat
- [ ] Inline comments used for any single-component fix
- [ ] Chat reserved for structural / conceptual / new-section changes
- [ ] No regeneration triggered for a one-color tweak (use inline comment + the color picker)

## Variations

- **Pre-meeting iteration** — before showing a stakeholder, do all reorder + variant swaps in Tweaks. Zero tokens, real-feeling iteration.
- **A/B layout exploration** — drag a section, screenshot, drag back, screenshot. Two PNGs to compare without spending vision tokens twice.
- **Density-only audit** — scrub from compact → spacious watching one section. Find the right setting for your DESIGN.md, then lock it.
- **Variant exhaustion** — click through every variant on a section to see what Claude pre-derived. Sometimes the best layout is one you didn't ask for.
- **Sidebar-only workshop** — challenge yourself to refine an artifact for 30 minutes using only the Tweaks panel. You'll discover what the panel actually covers.

## Common Failures

- **You kept chatting and burned the weekly allowance.** Cause: muscle memory from ChatGPT — type to make changes. Fix: print the decision tree above; physically tape it next to your monitor for a week.
- **The variant you want isn't in the panel.** Cause: Claude only pre-derives 2–4 variants per section. Fix: chat-prompt for it ("add a fourth hero variant: video background with mute toggle"); after Claude generates it, it'll appear in the panel for future swaps.
- **Reordering broke the visual rhythm.** Cause: a section depended on its neighbor (e.g., gradient bleed across two sections). Fix: chat-prompt to "re-derive section transitions after reordering."
- **Density slider made type illegible.** Cause: pushed compact too far for body text. Fix: snap back one step; or comment inline "increase body type scale by one step but keep padding."
- **Tweaks panel doesn't appear on mobile preview.** Cause: it collapses on narrow viewports by design. Fix: switch to desktop preview to access it; tweaks apply across breakpoints.
- **You can't find Tweaks.** Cause: it's the right-edge sidebar; some plans hide it behind a feature-flag in early preview. Fix: check `claude.ai/design → settings`; if it's missing, your workspace hasn't been opted into the panel yet.

## References

- [Austin Lau (Anthropic) — Tweaks panel demo](https://x.com/helloitsaustin/status/2045176910569980318) — the source of the reorder + variant-swap workflow shown end-to-end
- [Ryan Mather — 7 tips for Claude Design](https://x.com/Flomerboy/status/2045162321589252458) — tip #2 ("Comment, don't chat") is the inline-comment half of the same model
- [`recipes/comment-paste-workaround.md`](comment-paste-workaround.md) — the inline-comment workaround for component-level edits when full chat re-prompts cost too much
- [`recipes/token-budget-claude-design.md`](token-budget-claude-design.md) — the broader spend model; Tweaks + comments are the two zero/low-cost surfaces
- [Anthropic — Claude Design subscription usage and pricing](https://support.claude.com/en/articles/14667344-claude-design-subscription-usage-and-pricing) — quota math; weekly allowance applies to chat prompts, not Tweaks
