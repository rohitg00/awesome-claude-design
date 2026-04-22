# Landing Page in 20 Minutes

End-to-end flow: pick a `DESIGN.md` → generate in Claude Design → hand off to Claude Code → deploy on Vercel.

<img src="../assets/tags/curated.svg" alt="curated"> <img src="../assets/tags/new.svg" alt="new">

---

## Goal

Ship a real, indexable landing page in 20 minutes. No Figma, no design back-and-forth, no boilerplate copy.

## Time

| Step | Wall-clock |
|---|---|
| 1. Pick DESIGN.md | 1 min |
| 2. Brief in Claude Design | 3 min |
| 3. Inline tweak with sliders | 5 min |
| 4. Bundle to Claude Code | 1 min |
| 5. Wire copy + analytics | 6 min |
| 6. `vercel --prod` | 4 min |
| **Total** | **~20 min** |

## Inputs

- A `DESIGN.md` file from `/design-md/<family>/` (or your own)
- One sentence about the product
- Hero image / logo / favicon (optional — Claude Design will generate placeholders)
- A Vercel project (free tier OK)

## Steps

### 1. Pick a DESIGN.md

Use `prompts/family-picker.md` if unsure. For a dev-tool landing, [terminal/warp.md](../design-md/terminal/warp.md). For a fintech, [editorial/vercel.md](../design-md/editorial/vercel.md). For a creator product, [cinematic/runway.md](../design-md/cinematic/runway.md).

### 2. Brief Claude Design

```
Build a landing page for {product name}: {one-sentence pitch}.

Use the attached DESIGN.md as the source of truth for color,
type, geometry, and component style. Do not invent new tokens.

Sections: hero, social proof, three-feature grid, pricing teaser,
secondary CTA, footer.

Tone: {pick one} confident · curious · honest · playful.

Generate in dark mode if DESIGN.md ships dark-only; otherwise
default light, dark-mode toggle in nav.
```

Drag the `DESIGN.md` into the chat. Wait ~90 seconds for first paint.

### 3. Tweak inline

Use the live sliders. Concrete moves that matter:

- Hero headline weight — ratchet to 600/700 if it reads thin
- Section padding — knock down 1 step on mobile
- Card hover state — set to border-shift, not lift
- Single accent moment per viewport — kill duplicates

Comment on specific elements ("the third feature card has too much top padding") instead of broad rewrites.

### 4. Bundle to Claude Code

Click **Bundle → Claude Code**. Paste the resulting prompt. Claude Code receives:

- HTML / TSX scaffold
- CSS variables matching DESIGN.md tokens
- Component stubs (Button, Card, Nav, Footer)
- One `npm install` instruction

Run it.

### 5. Wire copy + analytics

In Claude Code:

```
Replace placeholder copy with real strings from {marketing brief URL}.
Add Vercel Analytics (@vercel/analytics).
Add a /favicon.svg and /opengraph-image.tsx.
Set <title> and meta description from the hero headline.
```

### 6. Deploy

```bash
vercel --prod
```

Or push to main if Vercel is wired to GitHub.

## Quality Checks

- [ ] First Contentful Paint < 1.5s on 4G
- [ ] Lighthouse Accessibility ≥ 95
- [ ] All hero copy is product-specific (no `Lorem`, no `Get Started`)
- [ ] One accent color across the page (matches `--accent` in DESIGN.md)
- [ ] OG image renders in [opengraph.dev](https://opengraph.dev) preview
- [ ] Dark mode toggles cleanly if shipped
- [ ] Mobile view: nav collapses, hero text scales one step down

## Variations

- **Marketing site (multi-page):** repeat steps 2–4 for `/pricing`, `/changelog`, `/about`. Reuse the bundle.
- **Docs-style landing:** swap `editorial/vercel.md` and ask for "docs hero with a search bar and three card-categories below."
- **Single-day full launch:** add `/recipes/16-min-everything-build.md` to layer in a 90s brand video and a pitch deck from the same DESIGN.md.

## Common Failures

- **The page looks generic.** Cause: Claude Design ignored DESIGN.md tokens because the brief was too loose. Fix: re-prompt with "use only the tokens defined in the attached DESIGN.md — do not invent new colors or fonts."
- **Hero illustration clashes with brand.** Cause: default generative image. Fix: replace with your own asset or add "no hero illustration — use type-only hero" to the brief.
- **Three accent colors instead of one.** Fix: comment on the duplicates inline; ask Claude Design to consolidate to `--accent`.
- **Vercel build fails on first deploy.** Cause: missing `next.config.js` or `package.json` script. Fix: run `npm run build` locally first; let Claude Code resolve before pushing.
