# Renault — Aurora Pop Geometric

Reference DESIGN.md for European mobility brands that need to feel modern and warm at once. Paper-white canvas with full-bleed aurora gradients (yellow → magenta → cyan), the diamond logomark as primary geometric anchor, NouvelR across the page, restrained 4px corner softening on inputs only.

## 1. Visual Theme & Atmosphere

Aurora pop. The page is mostly paper, then drops into full-bleed aurora panels — yellow easing into magenta into cyan — that echo the Renault diamond logomark. NouvelR carries every word; geometry leans into the diamond shape on dividers and section anchors. Vehicle photography is sun-lit, color-rich, never moody.

Mood: optimistic, European, current, electric.

## 2. Color Palette & Roles

```
--bg:              #ffffff
--bg-alt:          #f4f4f4
--surface:         #ffffff
--ink:             #000000
--ink-muted:       #5a5a5a
--ink-dim:         #9a9a9a
--accent-yellow:   #efdf00   /* primary brand mark, CTA fill */
--accent-red:      #e91630   /* secondary CTA, inline link */
--accent-red-hover: #c41229
--accent-blue:     #1885d1   /* tertiary, electric-vehicle slabs */
--gradient-aurora: linear-gradient(120deg, #efdf00 0%, #ff6b9d 45%, #1885d1 100%)
--gradient-soft:   linear-gradient(180deg, rgba(232, 22, 48, 0.08) 0%, transparent 100%)
--border:          #d9d9d6
--rule:            #000000
```

Rule: the aurora gradient is the identity moment — used on hero backdrop and one large text fill per page. Buttons stay flat yellow or flat red, never gradient.

## 3. Typography Rules

- **Display + headings:** `NouvelR`, fallback `sans-serif`. Weight 700 for hero, weight 500 for editorial heads. Tracked −1% above 40px.
- **Body + UI:** NouvelR regular, 16–18px body, 1.55 line-height.
- **Labels + spec rows:** uppercase, tracked 8%, 12px, ink-muted.
- **Numerals (range, kWh, 0-100):** tabular, weight 700, paired with small unit labels.

Scale: 12 / 14 / 16 / 20 / 28 / 40 / 56 / 80 / 120.

Single typeface for the whole site. NouvelR carries the brand alone — never pair with a serif or grotesque sibling.

## 4. Component Stylings

**Buttons**
- Primary: `--accent-yellow` fill, ink text, radius 4px, padding 12/24, weight 700.
- Secondary: `--accent-red` fill, white text, radius 4px.
- Ghost: transparent, 1px ink border, ink text, radius 4px.
- Hover: 8% darken on yellow, `--accent-red-hover` on red. No scale, no glow.

**Cards / model tiles**
- White surface, 1px `--border`, radius 4px. Photo top, model name in NouvelR 28px, range/price strip below.
- Hover: border shifts to `--accent-red`. No shadow lift.

**Inputs**
- White fill, 1px `--border`, radius 4px, 10/14 padding. Focus: 2px `--accent-blue` ring, no offset.

**Nav**
- Fixed top, white fill, 1px bottom border. Diamond logomark left, model groups center, account/build right. Active link gets a 2px `--accent-yellow` underline.

**Hero gradient panel**
- Full-bleed `--gradient-aurora` slab, 60–80vh tall.
- Headline overlaid in white at 80–120px, weight 700, tight tracking.
- Yellow primary CTA bottom-left, ink text on the gradient.

**Diamond motif**
- Used as section anchor: a single outline diamond, 24–48px, ink-stroke 2px, sitting at the start of editorial sections. Never as repeating pattern.

## 5. Layout Principles

- 1320px max, 24px gutter, 12 column.
- 4px base. 4 / 8 / 16 / 24 / 32 / 48 / 80 / 120.
- Alternate paper-white slab → full-bleed aurora hero → spec slab → blue EV slab.
- Section breaks at 96–120px on desktop.
- Asymmetric column splits (60/40 photo + spec) over symmetric grids.

## 6. Depth & Elevation

Atmospheric, soft. Depth from gradient saturation and tonal step between white and `--bg-alt`. Allowed: 1px borders, 2px keyline rules, soft `--gradient-soft` wash behind featured cards. Forbidden: drop shadows on cards, glow effects, backdrop blur on nav.

## 7. Do's and Don'ts

**Do**
- Deploy the aurora gradient on hero backdrop once per page, plus one large text fill maximum.
- Keep buttons flat: yellow primary, red secondary, ghost tertiary. Never gradient buttons.
- Use the diamond motif as a single section anchor, not a repeating wallpaper.
- Hold to 4px radius across the system — softer than Ferrari, sharper than Cal.com.

**Don't**
- Apply the aurora gradient to buttons, links, or body type.
- Pair yellow and red in the same component — alternate by section.
- Add drop shadows, glows, or backdrop-blur nav.
- Mix in a serif or condensed grotesque — NouvelR carries the page.
- Use the diamond as a repeating tile background.

## 8. Responsive Behavior

- Hero headline scales 120 → 40 on mobile, retains weight 700.
- Aurora gradient backdrop retains full bleed; CTA stacks below headline.
- Nav collapses to ink hamburger on white below 1024px; diamond logomark stays.
- 12-column grid reflows to single column below 768px; 64px section rhythm.

## 9. Agent Prompt Guide

Bias: paper-white canvas, full-bleed aurora gradient (yellow → magenta → cyan) on hero, single NouvelR typeface, flat yellow primary + flat red secondary CTAs, 4px radii, diamond motif as section anchor, alternating white / aurora / blue-EV slabs, sun-lit color-rich vehicle photography.

Reject: dark-mode default, gradient-filled buttons or text links, multi-typeface mixing, repeating diamond wallpaper, drop shadows on cards, backdrop-blur nav, moody automotive lighting, pill buttons, glassmorphism, replacing NouvelR with Inter or a serif.
