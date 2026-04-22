# Web Capture → Prototype

Use Claude Design's native web capture to grab live elements from your production site, then build a prototype that matches reality — not a Figma file that drifted six releases ago.

<img src="../assets/tags/curated.svg" alt="curated"> <img src="../assets/tags/new.svg" alt="new">

---

## Goal

Capture a live page (or specific elements within it) directly inside Claude Design, then prototype a new flow on top. The prototype inherits the production tokens — type, color, component shape — without anyone exporting tokens by hand.

## Time

| Step | Wall-clock |
|---|---|
| 1. Open Claude Design + paste URL | 1 min |
| 2. Select capture targets | 3 min |
| 3. Brief the prototype | 2 min |
| 4. Generate + inline-tweak | 8 min |
| 5. Bundle to Claude Code (optional) | 1 min |
| **Total (capture-only)** | **~15 min** |

## Inputs

- A public URL — production site, marketing page, or web app preview
- A clear ask: *what new flow am I prototyping on top of this?*
- Pro / Max / Team / Enterprise Claude plan (web capture is gated)
- Optional: an existing `DESIGN.md` for the same brand to cross-check token extraction

## Steps

### 1. Open Claude Design + paste URL

In a new Claude Design session, paste the URL into the prompt box. Claude offers two read modes:

- **Page capture** — entire viewport at one or more breakpoints
- **Element capture** — pick specific components (hero, nav, pricing card)

For prototyping a new flow that should *feel native*, element capture beats page capture. Less noise.

### 2. Select capture targets

Concrete picks that actually matter:

- **Primary nav** — proves your prototype's chrome matches
- **Hero** — establishes type scale + accent usage in context
- **Primary CTA** — button shape, hover state, color role
- **One content card** — proves card geometry (radius, shadow, padding)
- **Footer** — easy to forget, easy to make wrong

Skip: ad units, third-party embeds, anything in an iframe. Capture quality drops on those.

### 3. Brief the prototype

```
Capture the following elements from {URL}:
- Top navigation
- Hero section
- Primary CTA button (in any state)
- One representative content card
- Footer

Extract the actual computed CSS for each. Build a DESIGN.md-shaped
internal token sheet from what you captured (color roles, type scale,
spacing rhythm, radius, shadow). Show me the token sheet before
generating any prototype.

Then prototype a new flow on top of this captured system:

{ describe the flow — e.g. "a 3-step onboarding wizard that lives at
/welcome, matches the home page chrome, and uses the same primary
CTA shape" }

Constraints:
- Use only the tokens you captured. Do not invent new colors or fonts.
- Match the spacing rhythm of the captured page within ±4px.
- New components (Stepper, ProgressBar) must be derived from existing
  primitives — don't invent a third button style.
```

The "show me the token sheet first" line is doing real work. It catches mismatches before you spend cycles on a prototype built on bad tokens.

### 4. Generate + inline-tweak

Once the token sheet looks right, let it generate. Then comment inline on:

- **Spacing inconsistencies** — your prototype's hero should breathe like the captured one
- **One-too-many accent colors** — capture often pulls a secondary accent that wasn't in your DESIGN.md
- **Type weight drift** — captured CSS sometimes reads display weight as `600` when it's actually `700` due to OS rendering. Verify against the live page.

Use specific, element-level comments. "The third onboarding step's CTA reads thinner than the home-page CTA — match weight."

### 5. Bundle to Claude Code (optional)

Same flow as [`landing-page-20-min.md`](landing-page-20-min.md): **Bundle → Claude Code**, paste the prompt in your terminal. Claude Code receives the prototype scaffold + the captured token CSS variables + component stubs.

```bash
npm install
npm run dev
```

If your production site is a Next.js app, you can drop the new flow at `/welcome` and it will render against your existing `globals.css` with no token conflicts.

## Quality Checks

- [ ] Token sheet was reviewed before prototype generation (not after)
- [ ] Captured CTA matches the production CTA's shape, weight, and color exactly
- [ ] No invented accent colors (compare prototype palette to capture sheet)
- [ ] Spacing rhythm holds within ±4px of captured baseline
- [ ] New components (Stepper, ProgressBar) are derived from existing primitives, not net-new
- [ ] If bundled to Claude Code: dev server renders the new flow against production `globals.css` without overrides
- [ ] Mobile breakpoint captured separately if your site has distinct mobile chrome

## Variations

- **Auth-gated app capture:** capture is public-only at launch. For dashboards behind auth, screenshot the relevant views and drag them in alongside a public marketing URL for the brand chrome.
- **Competitor capture for moat research:** capture a competitor's pricing page, then prototype your own pricing in *your* DESIGN.md to test "would mine convert better?"
- **Component library audit:** capture every page on your site, ask Claude to flag inconsistencies (3 button styles where there should be 2)
- **Pre-redesign baseline:** capture before refactor to lock the current visual contract; replay after refactor to verify nothing regressed
- **Multi-breakpoint capture:** capture the same page at 375 / 1024 / 1440 to extract the responsive token deltas (especially `clamp()` ranges)

## Common Failures

- **Captured tokens don't match the production site at runtime.** Cause: capture grabbed a stale CDN'd CSS file. Fix: hard-refresh the URL, recapture; or paste the URL with a cache-busting query param.
- **Hero looks right, but card geometry is off.** Cause: Claude only captured one card; your site has three card variants. Fix: explicitly list each card type to capture by URL anchor.
- **The new flow feels generic despite capture.** Cause: Claude defaulted to its own component library and only used your tokens for color. Fix: re-prompt with "use the captured Button primitive verbatim — same border-radius, same padding-y, same font-weight."
- **`clamp()` type scaling looks wrong in the prototype.** Cause: capture happened at one viewport. Fix: recapture at 375 + 1024 + 1440, ask Claude to extract the scaling formula.
- **Capture missed an iframe-embedded section.** Cause: Claude can't see across iframe boundaries. Fix: provide the iframe's source URL separately, or screenshot.
- **"Web capture is unavailable on your plan."** Cause: Free / personal plan without Claude Design enabled. Fix: upgrade or run on a Pro account.

## References

- [Anthropic — Claude Design overview](https://www.anthropic.com/news/claude-design) — feature listing for web capture
- [Department of Product — 5 examples + GitHub mock setup](https://departmentofproduct.substack.com/p/claude-design-is-here-everything) — capture used in walkthrough #3
- [Sorted Pixels — Claude for Designers Ultimate Guide](https://nervegna.substack.com/p/claude-for-designers-the-ultimate) — three-tier framing covers capture as "practitioner" move
- [DesignerUp — How to Use Claude Design for UX/UI](https://designerup.co/blog/how-to-use-claude-design-for-ux-ui/) — capture-then-iterate workflow
- [BSWEN — Good Enough for Professional Websites?](https://docs.bswen.com/blog/2026-04-18-claude-design-quality-professional/) — quality bar discussion (relevant when prototyping for production)
- [Lenny's Newsletter — What Claude Design is actually good for](https://www.lennysnewsletter.com/p/what-claude-design-is-actually-good) — capture covered in landing-page workflow
