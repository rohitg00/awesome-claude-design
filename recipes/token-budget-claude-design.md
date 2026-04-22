# Token Budget for Claude Design

Concrete sequence to get production work out of Claude Design without burning your weekly Pro/Max quota in two prompts. Distilled from [Ryan Mather's 7-tip thread](https://x.com/Flomerboy/status/2045162321589252458) (Anthropic verticals team), [Quasa's token-economics walkthrough](https://quasa.io/media/claude-design-looks-great-but-it-devours-your-token-limits-here-s-how-to-use-it-smartly), and Reddit launch-week receipts ("two prompts ate 95% of my weekly limit").

<img src="../assets/tags/curated.svg" alt="curated"> <img src="../assets/tags/new.svg" alt="new">

---

## Goal

Spend tokens on what compounds (system + reference screens) and stop spending them on what doesn't (full-page rebuilds for a one-color tweak). Ship a real project on a single Pro plan in a week.

## Why this matters

Claude Design routes every generation through Opus 4.7's vision model. Vision tokens are roughly 3x text tokens per equivalent surface. Long context (100k+) plus a full re-render every iteration is how Pro caps blow up before Wednesday.

Reddit data points from launch week:

- "Two to three full prompts and you're at the weekly limit" — r/ClaudeAI launch thread
- "I used 95% of my weekly Claude Design usage on one project" — HN [item 47818700](https://news.ycombinator.com/item?id=47818700)
- "Pro users report Claude Code sessions running up to 3x longer on Opus 4.7 vs 4.6" — [Pasquale Pillitteri](https://pasqualepillitteri.it/en/news/1211/claude-code-removed-pro-plan-anthropic-april-2026)

## The Sequence

| Phase | What you spend tokens on | What you DON'T |
|---|---|---|
| 1. System scaffold | One detailed brief + DESIGN.md upload | Asking for "a website" with no system |
| 2. Reference screens | 3-4 canonical screens (hero, dashboard, settings, empty state) | All 12 screens you'll eventually need |
| 3. Iteration | Inline comments on specific elements | Chat re-prompts that trigger full regeneration |
| 4. Variants | "Branch from screen 2 with dark mode" | "Make it dark mode" (regenerates everything) |
| 5. Hand-off | Bundle to Claude Code once | Bundling per-screen separately |

## Phase 1 — System Scaffold (~1 hour, biggest spend, highest ROI)

Spend an hour here. Mather's tip 1 says it explicitly — this is worth it.

```
Brief Claude Design ONCE with:

1. The DESIGN.md (drag the file in)
2. Brand context (one paragraph about voice, audience, market)
3. Three explicit "reject" rules (use the break-default-aesthetic
   prompt pack — neutralizes the teal/serif/container-soup defaults)
4. The list of canonical screens you'll need across the project
   (don't generate them yet — just declare them)

Ask Claude Design to:
- Confirm the system it understood
- Show you the token palette + type scale + component library
- NOT generate any screen yet

If the system summary is wrong, fix it now. Every later token
spends against this base. Wrong base = wasted compounding.
```

## Phase 2 — Reference Screens (~30 min)

Generate 3-4 canonical screens, never more.

**Why:** every additional screen in the same conversation pulls the existing screens into context (vision tokens). Four screens is roughly the inflection point where the next generation starts costing more than it's worth.

Pick screens that anchor the system:

- **Hero / landing** — establishes display type, color, layout rhythm
- **Dashboard or app shell** — establishes density, sidebar, table style
- **Settings / form** — establishes input, focus, error states
- **Empty state OR error 404** — establishes voice + illustration palette

Skip:

- Marketing sub-pages (they'll inherit from hero)
- Component variants (use Phase 4 instead)
- Mobile breakpoints (inherit from desktop unless they break)

## Phase 3 — Iteration (use comments, not chat)

The single biggest token saver. Inline comments on a specific element trigger a local edit, not a full regeneration.

| Want to change | Use | Don't use |
|---|---|---|
| Hero button color | Inline comment on the button | "Change the hero button to terracotta" in chat |
| Card padding | Inline comment on a card + slider | "Tighten all card padding by one step" in chat |
| Heading weight | Inline comment on the heading | "Make headings heavier across the site" in chat |
| Whole-system color tweak | Slider on the token | Chat asking for re-render |

Mather's tip on this: comments are for local component-level revisions, chat is for structural or conceptual changes. The cookbook help docs say it explicitly.

## Phase 4 — Variants

For light/dark, compact/comfortable, marketing/app variants, use the **branch** action — Claude branches from your existing base tokens instead of regenerating from scratch. Way cheaper.

```
Branch screen 2 (dashboard) into a dark-mode variant.
Use the dark tokens already declared in DESIGN.md.
Do not re-derive tokens.
```

## Phase 5 — Hand-off (one bundle)

When the system is locked, bundle to Claude Code **once** with all screens at the same time. Bundling per-screen separately re-uploads the system context every time.

```
Bundle screens [hero, dashboard, settings, empty-state] as a
single Claude Code handoff. Include the DESIGN.md, all CSS
variables, and component stubs in one transfer.
```

In Claude Code, ask for the rest of the screens (pricing, about, blog, etc.) — Claude Code is text-only, much cheaper per token, and inherits the system from the bundle.

## Quality Checks

- [ ] System scaffold reviewed and approved before any screen generation
- [ ] No more than 4 reference screens in a single Claude Design conversation
- [ ] Token-level tweaks done via slider, not chat
- [ ] Component-level tweaks done via inline comment, not chat
- [ ] Variants created via branch action, not full regeneration
- [ ] Handoff to Claude Code is a single bundle, not per-screen
- [ ] Marketing sub-pages and component variants generated in Claude Code (text-only) after handoff

## Watch the meter

Claude Design has its own usage tracking, separate from Claude chat and Claude Code. Hit `claude.ai/design → settings → usage`. Per Anthropic, the design quota does NOT come out of your chat quota — but if you also use Claude Code, that quota is shared.

## Variations

- **One-shot landing page (no app):** skip Phase 4 entirely. Two reference screens (hero + footer-anchor) is enough; bundle once.
- **Slide deck:** generate the title slide + section-divider + content-slide + closing as your 4 reference screens. Variants for each new section.
- **Brand video:** Phase 1 + a single reference frame is enough — most token cost is in the video render itself, not the surface design.
- **Iteration-heavy / client-facing comp:** budget Phase 3 at 60% of weekly quota; the back-and-forth is where designers actually live.

## Common Failures

- **Burned weekly quota in 2 prompts.** Cause: full-page chat re-prompts in Phase 3. Fix: switch to inline comments.
- **System drift.** Cause: skipped Phase 1 confirmation step; Claude built a system you didn't see, then iterated against it. Fix: always confirm the scaffold output before moving to Phase 2.
- **Vision tokens spike on screen 5.** Cause: too many screens loaded into context. Fix: cap at 4 per conversation; spawn a new project for additional screens, re-loading the saved SKILL.md.
- **Bundle to Claude Code is missing components.** Cause: bundled per-screen instead of all at once. Fix: re-bundle the full set in one action.
- **Branch action produced a different system.** Cause: brief asked for "redo in dark mode" rather than "branch from existing tokens." Fix: use the explicit "branch" verb in your prompt.

## When to break the rules

If your design is for personal use or the output quality doesn't matter (internal tools, throwaway prototypes, a single-shot demo), ignore the sequence. Just chat-prompt and accept the regeneration cost. The sequence exists for billable work that has to ship.

## References

- [Ryan Mather X thread (Anthropic verticals team)](https://x.com/Flomerboy/status/2045162321589252458)
- [Quasa — token economics walkthrough](https://quasa.io/media/claude-design-looks-great-but-it-devours-your-token-limits-here-s-how-to-use-it-smartly)
- HN [Thoughts and feelings around Claude Design](https://news.ycombinator.com/item?id=47818700)
- [Pasquale Pillitteri — Pro plan + Opus 4.7 quota dynamics](https://pasqualepillitteri.it/en/news/1211/claude-code-removed-pro-plan-anthropic-april-2026)
- [The Neuron Daily — Reddit reactions](https://www.theneurondaily.com/p/anthropic-s-claude-design-launched-and-reddit-has-thoughts)
