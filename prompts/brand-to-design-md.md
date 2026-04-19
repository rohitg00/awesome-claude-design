# `brand-to-design-md`

Scrape any live website or brand page into a working `DESIGN.md` ready to drop into Claude Design.

<img src="../assets/tags/curated.svg" alt="curated"> <img src="../assets/tags/community.svg" alt="community"> <img src="../assets/tags/family-warm.svg" alt="warm editorial">

---

## Input Prompt

```
You are a senior design systems architect. Analyze the brand at {URL}
and produce a DESIGN.md file that captures its visual language for
coding agents to replicate.

Inspect:
1. Computed CSS of body, h1, primary button, primary link
2. Hero section tokens (color, type, spacing)
3. Font stack and licensing notes
4. Distinctive visual signatures (radii, shadows, motion, grid)

Output MUST include all 9 canonical sections:
- Visual Theme & Atmosphere
- Color Palette & Roles (CSS variables)
- Typography Rules (scale + stack)
- Component Stylings (button, card, input, nav)
- Layout Principles (grid, max-width, spacing scale)
- Depth & Elevation
- Do's and Don'ts
- Responsive Behavior
- Agent Prompt Guide

Rules:
- Only describe what you can verify from rendered output.
- Never hallucinate typography names — mark "unknown" if unclear.
- Color values as hex with role names, not brand names.
- Keep each section under 150 words.

Begin with: URL = {URL}
```

---

## Example Run

**Input:**

```
URL = https://linear.app
```

**Expected output (abridged):**

```markdown
# Linear — Editorial Minimalism

## 1. Visual Theme & Atmosphere
Editorial minimalism. Swiss-grid discipline meeting modern SaaS.
Every pixel earns its place. Quiet confidence through typography
hierarchy, not decoration.

## 2. Color Palette & Roles
--bg:            #ffffff
--text:          #0f0f14
--text-muted:    #6b6b76
--border:        #e4e4e7
--accent:        #5e6ad2   /* surgical purple */

## 3. Typography Rules
Inter throughout, weights 400/500/600.
Scale: 11 / 13 / 14 / 16 / 18 / 22 / 28 / 36 / 48 / 64.
Letter-spacing −0.5% at headline sizes.

## 4. Component Stylings
Button (primary): #5e6ad2 fill, white text, radius 6, padding 8/14.
Card: #fafafa fill, 1px #e4e4e7 border, radius 8, no shadow.
Input: 1px border, radius 6, 2px accent focus ring with 2px offset.

[... 5 more sections ...]
```

**What to do next:**
1. Save output as `/design-md/editorial/{brand}.md`
2. Drag into Claude Design
3. Click "Create new design system from this file"
4. Preview generated UI kit

---

## Quality Checks

Before committing, verify:

- [ ] All 9 sections present
- [ ] Color values are hex (not `rgb()` or names)
- [ ] Font stack includes fallbacks
- [ ] No purple-gradient defaults
- [ ] No emoji in the DESIGN.md itself
- [ ] Spacing scale uses numeric values (not "small/medium/large")
- [ ] Agent Prompt Guide ends with a rejection clause

---

## Variations

**Screenshot input:** replace `URL = {URL}` with `Attached: {N} screenshots. Infer tokens from pixel values. Use ColorThief-style sampling for palettes.`

**Design system audit:** add "Also compute a contrast-ratio report for all text/background pairs against WCAG AA."

**Dark/light variants:** append "Output both light and dark tokens. Naming convention: `--text-primary` works in both; tokens that differ use `--bg-light`/`--bg-dark`."
