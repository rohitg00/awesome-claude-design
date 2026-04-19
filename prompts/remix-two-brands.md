# `remix-two-brands`

Combine tokens from two DESIGN.md files into a coherent third system. Not copy-paste — actual token arbitration with reasoning.

<img src="../assets/tags/remix.svg" alt="remix"> <img src="../assets/tags/new.svg" alt="new">

---

## Input Prompt

```
You are a design systems architect performing a two-brand remix.
Inputs: {DESIGN_A.md} and {DESIGN_B.md}.
Goal: produce {REMIX_NAME}.md — a coherent third system that
inherits the best of each, resolves conflicts deliberately, and
maintains all 9 canonical DESIGN.md sections.

Arbitration rules:
1. TYPOGRAPHY from A or B, not both. Justify the pick.
2. COLOR: take primary neutrals from A, accent from B (or vice versa).
   Never mix two accents — pick one.
3. SPACING: use whichever has the stricter scale.
4. RADII: use whichever fits the chosen typography.
5. DEPTH: inherit the MORE restrained system's approach.
6. COMPONENTS: for every component, state which parent contributed
   which token, and why.
7. DO'S AND DON'TS: merge both lists, remove contradictions,
   flag any remaining tension as "creative tension — document for team."

Output must not read like a blend. It must read like a third brand
that could stand on its own.

End with: "Parent-brand DNA: A=XX%, B=YY%" based on token count.
```

---

## Example Run

**Input:**

```
DESIGN_A = /design-md/editorial/linear.md
DESIGN_B = /design-md/warm/claude.md
REMIX_NAME = Linear x Claude
```

**Expected output (abridged):**

```markdown
# Linear × Claude — Editorial SaaS with a Soul

## Parent DNA: Linear=55%, Claude=45%

## 1. Visual Theme
Linear's surgical information density meets Claude's warm editorial
restraint. Body reads like a New Yorker feature; UI feels like
Linear. Terracotta punctuates — never dominates.

## 2. Color Palette
/* neutrals from Linear — cold whites, dense grays */
--bg:             #ffffff
--bg-alt:         #fafafa
--text:           #0f0f14
--text-muted:     #6b6b76
--border:         #e4e4e7

/* accent from Claude */
--accent:         #c96442   /* terracotta, replaces Linear purple */
--accent-hover:   #b55738

Reasoning: Claude's cream base was too soft for dashboard scan
patterns. Linear's whites retain clarity. Terracotta wins over
Linear purple for emotional warmth.

## 3. Typography
Stack: Linear's Inter for UI + Claude's Tiempos Headline for h1/h2.
Justification: editorial-serif headlines signal calm; Inter at UI
sizes preserves density.

Scale: Linear's tighter scale (11/13/14/16/18/22/28/36/48/64).
Headlines use Tiempos at the upper four steps only (28+).

## 4. Components
Button: Linear geometry (radius 6, padding 8/14) + Claude color
(terracotta fill).
Card: Linear (1px border, no shadow, radius 8) — Claude's flat
surface principle reinforces.
Input: Linear (2px accent focus ring) + terracotta color.

[... remaining sections ...]

## 8. Creative Tensions
- Linear is dense, Claude is generous. For dashboards use Linear
  density; for marketing pages use Claude whitespace.
- Documented for team to arbitrate case-by-case.

## Parent-brand DNA
Tokens from Linear: 23/42 (55%)
Tokens from Claude: 19/42 (45%)
```

---

## Stock remixes to try

| Remix | Feel |
|---|---|
| Linear × Claude | Editorial SaaS with a soul |
| Warp × Sentry | Dev dashboard that doesn't feel cold |
| Stripe × A24 | Fintech pitch deck with personality |
| Vercel × Pitchfork | Editorial docs site |
| Granola × Criterion | Premium note app with gravitas |
| Ollama × ElevenLabs | CLI tool landing page |
| Notion × Duolingo | Friendly education SaaS |

Ship your own: `/design-md/remix/<brand-a>-x-<brand-b>.md` + screenshot.
