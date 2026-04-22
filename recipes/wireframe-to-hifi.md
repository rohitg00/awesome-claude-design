# Wireframe → Hi-Fi

Low-fi sketch (Whimsical, paper, balsamiq, plain ASCII) to pixel-perfect comp using a `DESIGN.md` as the substrate.

<img src="../assets/tags/curated.svg" alt="curated"> <img src="../assets/tags/new.svg" alt="new">

---

## Goal

Skip the mid-fi step. Go from rough box-and-arrow wireframe to production-ready hi-fi in one pass — bound to a DESIGN.md so the result feels like your brand, not a generic template.

## Time

| Step | Wall-clock |
|---|---|
| 1. Capture wireframe | 2 min |
| 2. Pair with DESIGN.md | <1 min |
| 3. Generate hi-fi | 3 min |
| 4. Inline iterations | 7 min |
| 5. Export to code | 2 min |
| **Total** | **~15 min** |

## Inputs

- Wireframe: photo, screenshot, ASCII, or `.fig` low-fi
- A `DESIGN.md` for your brand
- Notes about microcopy / states (optional but recommended)

## Steps

### 1. Capture the wireframe

Doesn't matter how rough. A photo of a napkin works. ASCII works:

```
┌─────────────────────────────────────┐
│  LOGO          NAV NAV NAV    [CTA] │
├─────────────────────────────────────┤
│                                     │
│   BIG HEADLINE                      │
│   sub-line of supporting copy       │
│   [PRIMARY CTA]  [secondary]        │
│                                     │
│   --- hero image / video ---        │
│                                     │
├─────────────────────────────────────┤
│   3 FEATURE CARDS IN A GRID         │
│   [card] [card] [card]              │
└─────────────────────────────────────┘
```

Drop into Claude Design.

### 2. Pair with DESIGN.md

Drag your DESIGN.md alongside the wireframe.

### 3. Generate

```
Convert the attached wireframe into a hi-fi composition.

Use the attached DESIGN.md as the only source for color, type,
spacing, radius, and component style. Do not invent new tokens.

Where the wireframe is ambiguous, default to:
- Density: dashboard-tight if DESIGN.md skews data-dense,
  generous if it skews editorial
- Hero image: type-only if no image is shown
- Card hover: border-shift, never lift
- CTAs: one primary, secondary as ghost or outlined per
  DESIGN.md component spec

Output: full responsive layout, desktop + mobile, light + dark
if DESIGN.md ships both modes.
```

### 4. Iterate inline

Comment on specific elements. Concrete moves:

- "Tighten hero vertical padding by one spacing step"
- "Replace stock photo with a generative still in our brand palette"
- "Change the third feature card icon to a custom mark, not Lucide default"
- "Swap headline weight 500 → 600 — it reads thin against the body type"
- "Add a kbd hint next to the CTA per DESIGN.md keyboard-hint pattern"

Stop when the comp matches what you'd ship.

### 5. Export

Bundle to Claude Code. The export should include:

- Component code (TSX / Vue / Svelte per your stack)
- CSS variables wired to DESIGN.md tokens
- Responsive media queries matching DESIGN.md breakpoints
- Accessibility attributes (aria-label, focus styles, semantic HTML)

## Quality Checks

- [ ] Every spacing value is on the DESIGN.md scale (no `padding: 13px`)
- [ ] Every color references a `--var`, no inline hex
- [ ] Type matches DESIGN.md scale exactly
- [ ] Primary CTA appears once per viewport
- [ ] Mobile layout collapses per DESIGN.md responsive section
- [ ] Dark mode renders if shipped
- [ ] No AI-slop tells (purple gradient hero, glass card stack, default Lucide icon grid)

## Variations

- **Whiteboard photo input:** mark sections in the photo with sticky notes labeled `H1`, `CTA`, `IMG`. Claude reads them.
- **From competitor screenshot:** capture a competitor's page, ask Claude to "rebuild this layout in our DESIGN.md system" — useful for client briefs that say "make it look like X."
- **Accessibility-first pass:** add "every interactive element must meet WCAG 2.2 AA contrast and ≥44px target" to the brief.
- **Voice-driven:** dictate the wireframe instead of drawing — Claude Design accepts spoken structural descriptions.

## Common Failures

- **Hi-fi looks identical to a Tailwind UI template.** Cause: DESIGN.md was loose enough that defaults won. Fix: tighten the "Reject" clauses in DESIGN.md (no purple gradients, no glass cards, no Inter if your brand uses something else), regenerate.
- **Layout collapsed to single column on desktop.** Cause: ambiguous wireframe. Fix: redraw the wireframe with explicit columns or label them in text.
- **CTA appears 4 times on the page.** Cause: agent over-anchored on conversion. Fix: comment "one primary CTA per viewport" inline.
- **Generative hero image clashes with brand palette.** Fix: ask "regenerate the hero image using only colors from `--bg`, `--accent`, `--text`."
