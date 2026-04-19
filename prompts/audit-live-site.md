# `audit-live-site`

One URL → structured design audit. Accessibility, hierarchy, spacing, contrast, AI-slop patterns. Ship as review comments or a punch list.

<img src="../assets/tags/curated.svg" alt="curated"> <img src="../assets/tags/new.svg" alt="new">

---

## Input Prompt

```
You are a senior product designer doing a design-review pass.
Audit {URL} against this rubric:

1. HIERARCHY (type scale, visual weight, scan path)
2. SPACING (rhythm, breathing room, alignment)
3. COLOR (palette coherence, contrast, role clarity)
4. ACCESSIBILITY (WCAG AA text/background, focus states, target sizes)
5. AI-SLOP PATTERNS (Inter everywhere, purple gradients, card-grid
   monotony, fake-3D glass, generic rounded buttons, emoji-heavy copy)
6. MOTION (purposeful vs decorative, reduced-motion handling)
7. COPY (microcopy tone, CTA clarity, error-state voice)

For each category, output:
- Score: 0–10
- Top 3 issues with element selector + screenshot coordinate
- Concrete fix with CSS snippet or copy rewrite
- Priority: P0 / P1 / P2

End with a Punch List — ordered by impact × effort.

Don't recommend what you can't verify. Cite evidence.
```

---

## Example Run

**Input:**

```
URL = https://example-saas.com
```

**Expected output:**

```markdown
# Design Audit — example-saas.com

## Scores
| Category | Score | Verdict |
|---|---|---|
| Hierarchy | 6/10 | H1 and H2 too close in size |
| Spacing | 4/10 | 8px/12px/20px mixed — no scale discipline |
| Color | 7/10 | Coherent but purple gradient cliche in hero |
| Accessibility | 5/10 | 3 contrast failures in footer |
| AI-slop | 3/10 | Hero = purple gradient + Inter + glass card |
| Motion | 8/10 | Reduced-motion respected |
| Copy | 6/10 | CTA says "Get Started" — generic |

## Top Issues

### P0 — Footer contrast fails WCAG AA
- Element: `footer a` at #a0a0a0 on #ffffff
- Ratio: 2.85:1 (needs 4.5:1)
- Fix: change `color: #a0a0a0` → `color: #595959`

### P0 — Hero is the AI-slop template
- `.hero` uses `linear-gradient(135deg, #a855f7, #ec4899)` + Inter
- Fix: replace with brand colors; swap Inter for a chosen typeface

### P1 — Spacing scale is ad-hoc
- Found 8, 10, 12, 14, 20, 24, 28, 32, 40, 48 across the site
- Fix: settle on 4 / 8 / 12 / 16 / 24 / 32 / 48 / 64

## Punch List
1. [P0] Footer contrast — 10 min
2. [P0] Hero redesign — 2 hours
3. [P1] Spacing scale lock — 4 hours
4. [P1] CTA copy rewrite — 20 min
5. [P2] Motion purpose pass — 1 hour
```

---

## Pair with Claude Design

After the audit, drop the Punch List back into Claude Design:

```
Take this audit punch list. Regenerate the hero section, footer,
and spacing tokens. Keep existing brand colors. Export new
DESIGN.md + CSS variables.
```

---

## Variations

- **Competitor benchmark:** audit 3 URLs, produce a comparative matrix
- **Pre-launch gate:** run before shipping; block on any P0
- **Accessibility-only:** skip categories 1, 3, 5–7; deep-dive 4
