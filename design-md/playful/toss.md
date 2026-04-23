# Toss — Playful Fintech

Reference DESIGN.md for Korean-fintech playful: Toss Blue against bright white, Toss Product Sans paired with Noto Sans KR, generous radii, friendly mood, mobile-first density.

## 1. Visual Theme & Atmosphere

Playful fintech. The page reads like a friend explaining money — bright white surfaces, one confident blue, generous radii, illustrations of cards and coins rendered in flat vector. The brand is warm without being childish; type stays geometric, copy stays plainspoken, and every CTA invites a tap. Korean-first, but the system holds in Latin script.

Mood: friendly, approachable, confident, never sterile.

## 2. Color Palette & Roles

```
--bg:              #ffffff   /* canvas */
--bg-alt:          #f9fafb
--surface:         #f2f4f6   /* cool gray surface lift */
--surface-2:       #e8f3ff   /* tinted blue wash for callouts */
--text:            #191f28   /* near-ink */
--text-secondary:  #333d4b   /* body copy */
--text-muted:      #6b7684
--text-dim:        #8b95a1
--border:          #e5e8eb
--border-strong:   #d1d6db

--accent:          #3182f6   /* Toss Blue — primary action + brand */
--accent-hover:    #1b64da
--accent-deep:     #1e40af   /* pressed / dark variant */
--accent-soft:     #e8f3ff   /* tinted callouts, secondary button bg */

--success:         #00c896   /* mint, positive balance */
--warning:         #ff9500   /* amber, attention */
--danger:          #f04452   /* coral red, decline / loss */
--info:            #3182f6
```

Rule: Toss Blue is the only branded hue. Status colors are reserved for state (positive balance, attention, decline). Never reuse status hues for decoration. The tinted blue wash `--surface-2` carries callouts and secondary buttons — it is the brand's softening move.

## 3. Typography Rules

- **Headlines + display:** `Toss Product Sans`, fallback `Pretendard`, `-apple-system`, `BlinkMacSystemFont`, `Apple SD Gothic Neo`, `Noto Sans KR`, system. Weight 600–700, tight tracking (−1% at large sizes).
- **Body + UI:** `Toss Product Sans`, fallback as above. Weight 400/500. Line-height 1.5–1.6. Korean glyphs rendered via `Noto Sans KR` and `Apple SD Gothic Neo` fallbacks.
- **UI labels:** Toss Product Sans weight 500, 13–15px.
- **Numerals:** tabular figures globally on balances, transaction lists, charts.
- **Mono:** `JetBrains Mono`, fallback `SF Mono`. Used for transaction IDs, code samples, OTPs.

Scale: 12 / 14 / 15 / 17 / 20 / 24 / 32 / 40 / 50 / 66.

Hero headlines run 50–66px on desktop. Korean and Latin glyphs share metrics within Toss Product Sans.

## 4. Component Stylings

**Buttons**
- Primary: Toss Blue fill `--accent`, white text `#f9fafb`, radius 7px, padding 14/20, weight 500. Hover: `--accent-hover`. Pressed: `--accent-deep`. No lift, no scale.
- Secondary: tinted blue fill `--surface-2`, deep blue text `--accent-hover`, radius 7px. The two-step blue is Toss's signature hierarchy.
- Tertiary / link: `--text-secondary`, blue underline on hover.
- Destructive: `--danger` fill, white text, only on confirm modals.

**Cards / list items**
- White fill, 1px `--border`, radius 12px, padding 20. Soft shadow `0 1px 3px rgba(25, 31, 40, 0.04)` only.
- Transaction rows: 1px hairline divider, no card chrome, 64px row height for tap targets.
- Hover: 1px `--border-strong`. No lift.

**Inputs**
- `--surface` fill, no border at rest, radius 12px, padding 16/20 (large tap targets).
- Focus: 2px `--accent` ring, no offset. Label floats above on focus.
- Currency inputs use right-aligned tabular numerals.

**Nav**
- Mobile bottom-tab nav primary, 56px tall, 5 icons max, blue active state.
- Web top nav: white fill, 1px bottom `--border`, blue underline on active.

**Illustrations**
- Flat vector. Cards, coins, characters. 2–3 hues per illustration drawn from blue + soft neutrals.
- Avoid photorealism, avoid drop shadows on illustration art.

## 5. Layout Principles

- Mobile-first. 360–430px primary canvas. Web mirrors mobile column at 480px max content width inside a 1200px shell.
- 4px base. 4 / 8 / 12 / 16 / 20 / 24 / 32 / 48.
- Generous vertical rhythm between content blocks (32–48px).
- Dense list views at 64px row height for tap-target compliance.

## 6. Depth & Elevation

Soft shadows allowed sparingly — single `0 1px 3px rgba(25, 31, 40, 0.04)` on cards, `0 8px 24px rgba(25, 31, 40, 0.08)` on modals and bottom sheets. No neumorphism. No stacked shadows. Tap targets get a brief scale(0.98) press feedback (96ms ease-out).

## 7. Do's and Don'ts

**Do**
- Use Toss Blue as the single confident accent.
- Pair primary blue with the tinted blue secondary — the two-step is the signature.
- Ship bottom-sheet modals on mobile, not page-pushed dialogs.
- Render every monetary value in tabular numerals.
- Write copy in plainspoken Korean / English — short sentences, friendly verbs.

**Don't**
- Introduce a second saturated brand hue.
- Soften corners past 16px (Toss tops out at 12–16px on cards, 7px on buttons).
- Use dark mode as the default canvas.
- Fill backgrounds with gradients (flat fills only).
- Mix more than two type weights per screen.

## 8. Responsive Behavior

- Mobile is canonical. Desktop mirrors the mobile column inside a centered 480px content lane.
- Headlines scale 66 → 28 on mobile.
- Bottom-tab nav on mobile becomes top nav with same 5 destinations on web.
- Modals become full-screen sheets below 640px.
- Lists become full-bleed at 360px viewport.

## 9. Agent Prompt Guide

Bias: bright white `#ffffff` canvas, single Toss Blue `#3182f6` accent paired with a tinted blue `#e8f3ff` secondary, Toss Product Sans with Noto Sans KR fallback, 7px radii on buttons and 12px on cards, mobile-first 480px content lane, 64px tap-target row heights, tabular numerals on every monetary value, flat-vector illustrations of cards / coins, bottom-sheet modals on mobile.

Reject: dark-mode marketing as default, multi-accent palettes, gradient fills, drop-shadow heavy cards, photorealistic imagery, soft-pill buttons over 16px radius, dense desktop-first dashboards, decorative emoji in chrome.
