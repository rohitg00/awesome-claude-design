# `break-default-aesthetic`

One-paste system prompt that neutralizes Claude Design's default "AI-slop" aesthetic — the teal-accent, blinking-status-dot, container-soup look that Reddit identified within hours of launch.

<img src="../assets/tags/curated.svg" alt="curated"> <img src="../assets/tags/new.svg" alt="new"> <img src="../assets/tags/anthropic.svg" alt="Anthropic">

---

## When to use

- First message in a new Claude Design project, before any generation
- Top of any DESIGN.md you hand to Claude Design or Claude Code
- System prompt for the [Anthropic `frontend-design` skill](https://github.com/anthropics/skills/blob/main/skills/frontend-design/SKILL.md) when you want stricter guardrails

## Input Prompt

```
Before you generate anything, internalize the following constraints.
These exist because Claude Design has observable default patterns
that I do not want in my output.

EXPLICIT REJECTIONS — do not produce any of these unless I ask:

1. ACCENT COLOR
   - Do not default to teal (#16d5e6 or near). My accent is defined
     in DESIGN.md and must be the only chromatic action color.
   - Do not introduce a second accent for variety. One accent only.

2. STATUS INDICATORS
   - No animated dots, blinking lights, "live" badges, or pulsing
     orbs in nav, header, or hero.
   - Status surfaces use static glyphs and explicit text.

3. CONTAINER NESTING
   - Maximum container depth: 2 (e.g., section > card, not
     section > card > pill > tag > content).
   - No card-on-card decoration. If something needs visual separation,
     use border or tonal shift, not another wrapper.

4. TYPOGRAPHY
   - No serif headline + sans body unless DESIGN.md specifies it.
   - No Inter, Roboto, Arial, system-ui, "system stack" fallback as
     the chosen primary face.
   - Headline weight, tracking, and optical-size all stated in tokens.

5. LAYOUT CLICHES
   - No three-column feature grid in hero / section 2.
   - No identical-aspect card grids when the data is heterogeneous.
   - No "Get Started" / "Learn More" CTA pair as the default duo.

6. DECORATIVE LEFT RULES
   - The 4px coloured left-rule on every card is reserved for ONE
     semantic role (e.g., severity, status). Never decorative.

7. ICON FAMILY
   - Pick exactly one icon family per project: Phosphor, Heroicons,
     Tabler, custom. Do not mix.
   - If no family is provided, prefer type-only solutions over
     defaulting to Lucide.

8. GENERATIVE IMAGES
   - Hero illustrations and generative stills must use only colors
     declared in DESIGN.md (--bg, --surface, --accent, --text).
   - No purple-pink gradient on dark backgrounds.
   - No glass / frosted card stack as hero composition.

9. MOTION
   - Motion serves a purpose: communicate state, hierarchy, or
     spatial relationship. Decorative motion (floating particles,
     bobbing icons, scroll-tied parallax) requires explicit request.
   - Respect prefers-reduced-motion at all times.

10. COPY
    - Microcopy is product-specific. No "Welcome to {Product}" hero,
      no "Built for teams" subtitle, no "Get Started" CTA without a
      verb that names the action.

POSITIVE BIAS — when in doubt, prefer:

- Distinctive type choices that suit the brand voice
- One bold aesthetic direction over hedged "modern minimal"
- Border-based depth over drop shadows
- Editorial rhythm (max-width, vertical breathing) over uniform grids
- Content-first hero (type, table, demo) over decorative hero
- Real product surfaces (settings, empty states, edge cases) over
  marketing hero alone

VERIFICATION — after generating, audit your own output:

- Did I use teal as accent? (FAIL)
- Is there an animated status dot? (FAIL)
- Are there 3+ levels of nested containers anywhere? (FAIL)
- Did I use Inter / Roboto / Arial as primary face? (FAIL)
- Is there a three-column feature grid in section 2? (FAIL)
- Are there decorative coloured left-rules on more than one role? (FAIL)
- Is the hero illustration outside the DESIGN.md palette? (FAIL)

If any FAIL, regenerate the offending region before showing it to me.
```

## Example Run

**Input:**

```
{paste the prompt above}

Now build a landing page for our open-source database, "Halite",
using the attached DESIGN.md (data-dense family, deep navy + amber
accent, JetBrains Mono headlines).
```

**Expected behavior:**

- Hero uses amber accent (DESIGN.md), not teal
- No animated status dot in nav
- Section 2 is single-column with a code-block demo, not a three-card feature grid
- Type stack respects JetBrains Mono headlines + the body face declared in DESIGN.md
- Hero illustration uses navy + amber + the surface tokens; no purple-pink gradient
- "Get Started" replaced with "Run halite locally" or similar verb-first CTA

**If anti-slop guardrails work, the output should not be confusable with another Claude Design project — even at thumbnail scale.**

## Quality Checks

- [ ] Accent color matches DESIGN.md, not teal
- [ ] No animated status indicators anywhere
- [ ] Container nesting ≤ 2 levels
- [ ] Primary type face is project-specific, not Inter/Roboto/Arial
- [ ] Section 2 layout is not a three-column feature grid
- [ ] Coloured left-rules carry semantic role, not decoration
- [ ] Single icon family throughout
- [ ] Generative hero uses only DESIGN.md palette
- [ ] CTA verbs are product-specific
- [ ] Motion either purposeful or absent

## Variations

- **Strict mode (no AI-slop tolerance):** add "On any FAIL, halt generation and ask me before continuing." Slower, but useful for production handoffs.
- **Brand-handover mode:** swap "DESIGN.md" references for "the brand kit at {URL}" — works when the system isn't yet a DESIGN.md.
- **Cookbook-only:** strip sections 1, 2, 6, 8 if your DESIGN.md already covers those rules; keep 3, 4, 5, 7, 9, 10 as universal.
- **Inverse audit:** paste this *after* generation as a "now audit what you just produced against this rubric and report FAILs" prompt — useful when you didn't seed the project up front.

## Pair with Claude Design

After the first generation, comment inline on any FAIL. Example concrete comments:

- "The hero accent is teal — replace with `--accent` from DESIGN.md."
- "Remove the green dot in the top nav — DESIGN.md specifies static status surfaces."
- "Section 2 is the default three-card grid. Redo as a single-column demo with code block."

## References

- Anthropic [`frontend-design` SKILL.md](https://github.com/anthropics/skills/blob/main/skills/frontend-design/SKILL.md) — the underlying skill Claude Design routes through
- Anthropic [frontend-aesthetics cookbook](https://github.com/anthropics/claude-cookbooks/blob/main/coding/prompting_for_frontend_aesthetics.ipynb) — original "AI-slop" framing
- [`anthropics/skills` PR #210](https://github.com/anthropics/skills/pull/210) — 75% win-rate clarity revision
- [Sam Henri Gold — Thoughts and feelings around Claude Design](https://samhenri.gold/blog/20260418-claude-design/)
- [The Neuron Daily — Reddit reactions](https://www.theneurondaily.com/p/anthropic-s-claude-design-launched-and-reddit-has-thoughts)
- [Banani — Claude Design first impressions](https://www.banani.co/blog/claude-design-review)
- HN: [Thoughts and feelings around Claude Design](https://news.ycombinator.com/item?id=47818700)
