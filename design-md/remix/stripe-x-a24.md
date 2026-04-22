# Stripe × A24 — Fintech Pitch With Personality

Remix. Stripe's grid + A24's poster boldness. For pitch decks, investor sites, premium fintech that needs to feel less corporate.

## Parent DNA: Stripe 50% · A24 50%

## 1. Visual Theme & Atmosphere

Stripe geometry holds the page; A24 makes the hero feel like a film poster. Layout is rigorously gridded, but headlines run oversized in A24's editorial display serif and sit on full-bleed image plates. CTAs stay Stripe — the trust signal cannot break.

Mood: confident, cinematic, financial-trust-preserving.

## 2. Color Palette & Roles

```
/* base from Stripe */
--bg:              #ffffff
--bg-alt:          #f6f9fc
--surface:         #ebeef3
--text:            #0a2540   /* Stripe deep navy */
--text-muted:      #425466
--border:          #e3e8ee

/* dark from A24 — film-poster black */
--bg-dark:         #000000
--bg-dark-alt:     #0a0a0a
--text-dark:       #ffffff
--text-dark-muted: rgba(255,255,255,0.72)

/* accent from Stripe — preserves trust */
--accent:          #635bff
--accent-hover:    #5048e5

/* accent from A24 — used on dark-mode hero only */
--accent-warm:     #f4ede4   /* warm cream — A24 print-stock palette */
--accent-pop:      #d9351c   /* deep film red — used once per page max */
```

Arbitration: A24's iconic black background wins on hero plates. Stripe's white wins on app, pricing, docs. Stripe purple stays as primary CTA across both modes — replacing it kills the fintech trust signal. A24 red is allowed once per page as a callout (asterisk, sale tag, single label).

## 3. Typography Rules

- **Display / hero h1:** `Söhne Breit` weight 600 OR a free A24-adjacent display serif like `Fraunces` weight 600 — set at 96px+ for poster effect.
- **h2–h4 + body:** `Söhne` (Stripe). Weight 400/500/600.
- **UI labels + pricing tables:** `Söhne Mono` for numerals.

Scale: Stripe's marketing ramp, extended at the top for A24 hero. 12 / 14 / 16 / 18 / 22 / 28 / 36 / 56 / 96 / 144.

Display serif allowed at 56px+ only. Anything smaller stays Söhne for legibility.

## 4. Component Stylings

**Buttons**
- Primary: `--accent` (Stripe purple) fill, white text, radius 6, padding 10/16, weight 500.
- Secondary on white: `--text` color, 1px `--border`, white fill.
- Secondary on black: `--text-dark`, 1px `rgba(255,255,255,0.24)`, transparent fill.

**Hero plates**
- Full-bleed black panel (`--bg-dark`), display serif headline, single image or generative still. Stripe's grid still holds — text starts at column 2, ends at column 11.

**Cards**
- Stripe pattern: `--bg` fill, 1px `--border`, radius 12, no shadow.
- On dark hero: cards drop to `--bg-dark-alt` with 1px `rgba(255,255,255,0.12)`.

**Inputs**
- Stripe geometry: `--surface` fill, 1px `--border`, radius 6, padding 10/12.
- Focus: 2px `--accent` ring, 2px offset.

**Pricing tables**
- Söhne Mono numerals tabular. Header row in display serif at 36px. Body rows Söhne 14px.

## 5. Layout Principles

Stripe's grid governs everything.

- Marketing: 1180px max, 24px gutter, 12-col.
- App: 1440px max app shell.
- 4px base. 4/8/12/16/24/32/48/64/96/144 scale.

A24 contribution: full-bleed image / black panels break the column grid horizontally — vertical rhythm still respects 8px multiples.

## 6. Depth & Elevation

Flat. Border depth on light, alpha-border on dark. Shadows reserved for popovers (`0 4px 12px rgba(10,37,64,0.08)` on light, `0 12px 32px rgba(0,0,0,0.7)` on dark hero).

A24 contributes no shadows — its design is fundamentally print, not screen-elevated.

## 7. Do's and Don'ts

**Do**
- Use display serif at 56px+ on full-bleed black plates.
- Keep Stripe purple CTA across both light and dark surfaces — never substitute.
- Cap A24 red to one label per viewport.
- Render pricing in Söhne Mono tabular.

**Don't**
- Use display serif for body or UI controls.
- Add a third chromatic accent.
- Replace Stripe purple with A24 red for CTA — fintech trust loss.
- Drop the grid for full-bleed art on dashboard / data screens.

## 8. Responsive Behavior

- Hero serif scales 144 → 96 → 64 → 48.
- Full-bleed black plates remain full-bleed at all breakpoints.
- Pricing tables collapse to per-tier cards below 768px.
- Stripe app shell collapses sidebar to overlay at 1024px.

## 9. Agent Prompt Guide

Bias: Stripe grid + Söhne UI everywhere, full-bleed black A24 hero plates, display serif at 56px+, Stripe purple as the only CTA color, A24 red sparingly, tabular pricing.

Reject: display serif in UI controls, A24 red as CTA, multi-color accent palettes, abandoning the column grid in app surfaces, pastel Stripe substitutes.

## Creative Tensions (documented for team)

- **Trust vs theatricality.** A24's poster aesthetic risks reading as marketing-only on a fintech surface. Solution: confine A24 contribution to hero / case-study / about pages — never on dashboard, pricing, or compliance copy.
- **Display serif legibility.** Below 56px the serif reads decorative. Enforce a hard size floor in tokens.

## Parent-brand DNA

Tokens traced:
- From Stripe: 22 (Söhne stack, navy `--text`, `--accent` purple, button geometry, card radius 12, marketing 1180 max, app 1440, focus ring, light surface palette, mono pricing)
- From A24: 19 (full-bleed black hero, display serif 56px+, cream secondary palette, single-label red, print-flat depth, edge-to-edge image plates)

Net DNA: Stripe 50% · A24 50%.
