# Existing Repo → Design System

Point Claude Design at a real codebase. Get back a canonical `DESIGN.md` that reflects what your CSS actually does — not what your style guide *claims* it does.

<img src="../assets/tags/curated.svg" alt="curated"> <img src="../assets/tags/new.svg" alt="new">

---

## Goal

Generate a working design system from a live repository. Claude Design reads CSS variables, component files, and computed styles, then writes a `DESIGN.md` you can drop back into the repo as the source of truth.

Per Linas Beliūnas's *Founder's Playbook*: Mercury reported Claude inferring **~90% of their design system directly from the codebase**. The remaining 10% is the editorial pass.

## Time

| Step | Wall-clock |
|---|---|
| 1. Pick the right scope (subdirectory, not monorepo) | 3 min |
| 2. Connect the repo | 2 min |
| 3. Run the inference prompt | 5 min |
| 4. Edit the 10% Claude got wrong | 15 min |
| 5. Commit `DESIGN.md` to the repo | 2 min |
| **Total** | **~25–30 min** |

## Inputs

- A repo with a non-trivial CSS layer (Tailwind config, CSS vars, styled-components, or vanilla CSS)
- GitHub access via the GitHub connector OR a public repo URL OR a local folder you can drag in
- One existing component you trust to be "on-brand" (your reference truth)
- ~30 min of editor time for the polish pass

## Steps

### 1. Pick the right scope — subdirectory, not monorepo

Per *AI For Developers* ([How to Actually Use Claude Design](https://aifordevelopers.substack.com/p/how-to-actually-use-claude-design)): pointing Claude at a 200-package monorepo gets you nowhere. The context window chokes, inference quality degrades, and the resulting `DESIGN.md` is mush.

Instead:

- For a monorepo: point Claude at **one app** (e.g. `apps/marketing/`) or **one package** (`packages/ui/`)
- For a single Next.js app: target `src/components/` + `tailwind.config.js` + `src/app/globals.css`
- For a Rails / Django app: target `app/javascript/` or the equivalent component folder

If you must cover a monorepo, run this recipe **once per package** and merge the resulting files manually. Don't ask Claude to do the merge — that's the editorial pass.

### 2. Connect the repo

Three options, ordered by quality of result:

- **GitHub connector** (best) — Claude reads file-by-file, follows imports, sees the whole tree
- **Repo URL paste** — Claude clones a snapshot; works for public repos
- **Drag a `.zip`** — for private repos you can't expose; less reliable on file size limits (~25MB)

### 3. Run the inference prompt

```
Read the codebase rooted at {subdirectory path or repo URL}. Focus on:

- CSS variables (look in globals.css, theme.ts, tailwind.config.{js,ts})
- Component primitives (Button, Card, Input, Nav, Modal — whichever exist)
- Typography stack (font-family declarations + computed sizes)
- Spacing scale (margin/padding patterns; Tailwind's `space-*`, CSS calc() chains)
- Color usage (every hex / hsl / oklch reference, grouped by semantic role)

Produce a DESIGN.md following the 9-section canonical format used in
awesome-claude-design (see /design-md/<family>/*.md for examples):

1. Visual Theme & Atmosphere — what kind of product this looks like
2. Color Palette & Roles — every color, role-named (--bg, --accent, --surface)
3. Typography Rules — font stack with fallbacks, modular scale extracted
   from real font-size values
4. Component Stylings — Button (primary/secondary), Card, Input, Nav minimum
5. Layout Principles — max-width, grid, spacing scale
6. Depth & Elevation — every shadow/border style detected
7. Do's and Don'ts — inferred from consistent patterns in the code
8. Responsive Behavior — breakpoints used, transition patterns
9. Agent Prompt Guide — bias + reject clauses for future LLM use

Each section ≤ 150 words. Hex only. No marketing copy.

For every claim, cite the file + line you pulled it from. If a token is
inferred not observed, label it "inferred" — don't fabricate.
```

### 4. Edit the 10% Claude got wrong

The Mercury number is 90%. The other 10% is real:

- **Color roles get crossed** — Claude may name your warning yellow `--accent` because it's used in a CTA somewhere
- **Spacing scale collapses** — Tailwind's full scale (0.5, 1, 1.5, 2, 3, 4...) often gets compressed to (1, 2, 4, 8) in the inference
- **Component variants missed** — secondary buttons used twice in a 200-component repo will be ignored
- **Dark mode tokens** swallowed into light mode if your `dark:` prefixes aren't dense enough

Open the `DESIGN.md` next to your component reference (the one you trust). For each section, ask: *would I onboard a new designer with this doc?* Edit until yes.

### 5. Commit `DESIGN.md` to the repo

Place it at `/DESIGN.md` (root) or `/docs/DESIGN.md`. Future Claude Design sessions on this repo will pick it up automatically as the design system file.

```bash
git add DESIGN.md
git commit -m "add: canonical design system inferred from codebase"
```

For multi-package monorepos: one `DESIGN.md` per package (`packages/ui/DESIGN.md`, `apps/marketing/DESIGN.md`) — keep them scoped to what they describe.

## Quality Checks

- [ ] Every color in section 2 traces back to a file:line reference
- [ ] Type stack matches the actual `font-family` cascade (fallbacks included)
- [ ] Modular scale uses real values from your CSS, not the default 1.25 ratio
- [ ] At least one "Don't" in section 7 cites a pattern you've actively rejected in code review
- [ ] Spacing scale matches your Tailwind config (or equivalent) — not a Claude default
- [ ] No `inferred` tokens hide in places that should be observed (re-prompt if so)
- [ ] Dark mode coverage matches what your repo actually ships

## Variations

- **Refactor-driven:** run the recipe **before** a CSS refactor to capture current state, then re-run after to diff what changed
- **Acquisition due-diligence:** run on the acquired company's repo to produce a design-system gap analysis
- **Polyrepo merge:** generate `DESIGN.md` per repo, then run [`recipes/two-brand-remix.md`](#) (when shipped) to propose a unified system
- **Storybook-first:** if you have Storybook, point Claude at `*.stories.tsx` files — variant coverage is much higher

## Common Failures

- **The inference is generic.** Cause: pointed Claude at the monorepo root; it averaged everything. Fix: scope to one package or app, re-run.
- **Tokens look invented.** Cause: Claude couldn't access the file (private repo without connector auth). Verify by asking it to quote three real lines back. If it can't, fix the access.
- **`DESIGN.md` already exists and got overwritten.** Cause: Claude regenerated from scratch instead of reconciling. Fix: rename the existing file before re-running, then merge by hand. Don't ask Claude to "merge with existing" — quality drops.
- **Subdirectory has weird build artifacts.** Cause: Claude read `dist/`, `build/`, or `.next/` instead of source. Fix: explicitly say "read only `src/` and `tailwind.config.ts`, ignore `dist/` and `node_modules/`."
- **Component coverage is patchy.** Cause: components live in 4 directories you didn't mention. Fix: re-prompt with the full directory list.

## Case Studies

- **Mercury — 90% codebase inference** ([Linas Beliūnas](https://linas.substack.com/p/claude-design-founders-playbook)) — banking interface design system reconstructed from production CSS
- **Brilliant — 20→2 prompts** ([Anthropic launch post](https://www.anthropic.com/news/claude-design)) — interactive lessons platform; iteration count dropped 10× once `DESIGN.md` existed
- **Datadog — week → 1 conversation** ([Anthropic launch post](https://www.anthropic.com/news/claude-design)) — observability dashboard design system inference

## References

- [Linas Beliūnas — Founder's Playbook](https://linas.substack.com/p/claude-design-founders-playbook) — Mercury 90% inference cited
- [AI For Developers — How to Actually Use Claude Design](https://aifordevelopers.substack.com/p/how-to-actually-use-claude-design) — subdirectory-not-monorepo gotcha
- [Anthropic — Claude Design launch](https://www.anthropic.com/news/claude-design) — Brilliant + Datadog case studies
- [google-labs-code/design.md spec](https://github.com/google-labs-code/design.md/blob/main/docs/spec.md) — the canonical DESIGN.md format
- [Mejba Ahmed — Claude Design as the visual layer Claude Code was missing](https://www.mejba.me/blog/claude-design-visual-workflow-claude-code) — engineer-side workflow notes
