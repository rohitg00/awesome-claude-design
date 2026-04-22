# Figma File → DESIGN.md

Drag a `.fig` file into Claude Design, extract a canonical `DESIGN.md` with tokens, components, and rules.

<img src="../assets/tags/curated.svg" alt="curated"> <img src="../assets/tags/new.svg" alt="new">

---

## Goal

Turn a Figma file into a portable, machine-readable design system that any LLM can consume. No plugins. No Tokens Studio JSON wrangling.

## Time

| Step | Wall-clock |
|---|---|
| 1. Export `.fig` | 1 min |
| 2. Drag into Claude Design | <1 min |
| 3. Run extraction prompt | 2 min |
| 4. Review tokens + components | 5 min |
| 5. Lock as `DESIGN.md` + `SKILL.md` | 2 min |
| **Total** | **~10 min** |

## Inputs

- A Figma file with named styles (color, text, effect)
- Components published or at least named consistently
- Pro/Max/Team Claude plan for `.fig` import

## Steps

### 1. Export `.fig`

In Figma: `File → Save local copy…` → `.fig`. Don't use a plugin export. Don't flatten frames first — Claude Design needs the layer hierarchy.

### 2. Drag into Claude Design

Open a new Claude Design project. Drag `.fig` into the chat. Wait for the parse confirmation ("read N frames, M components, K styles").

### 3. Run the extraction prompt

```
Read the attached Figma file. Produce a DESIGN.md following the
9-section canonical format:

1. Visual Theme & Atmosphere — infer from layout density,
   palette, and type weight choices
2. Color Palette & Roles — list every color style, propose
   role names (--bg, --surface, --text, --accent, etc.).
   Hex only. Reject brand-name keys.
3. Typography Rules — list every text style, group by role
   (display/body/UI/mono), produce a modular scale
4. Component Stylings — for every published component:
   tokens used, geometry (radius, padding), state styles
5. Layout Principles — derive grid + spacing scale from
   frame measurements
6. Depth & Elevation — list every effect style, classify
   (shadow vs border vs material)
7. Do's and Don'ts — infer from consistent vs ad-hoc patterns
8. Responsive Behavior — if multiple breakpoint frames exist,
   describe transitions
9. Agent Prompt Guide — bias + reject clauses

Each section ≤ 150 words. No emojis. No marketing copy.
Hex colors with role names, not brand names.

Output as one Markdown file ready to paste into a repo.
```

### 4. Review

Common edits:

- Collapse near-duplicate colors (`#fafafa` and `#f9f9f9` → one token)
- Rename Figma's "Primary/Hover/Active" stack to `--accent`, `--accent-hover`, `--accent-active`
- Remove components that are one-offs (not part of the system)
- Add explicit "reject" rules for AI-slop patterns observed

### 5. Lock as DESIGN.md and SKILL.md

In Claude Design:

```
Save this as a project skill named {brand}-design-md so every
future Claude Code session picks it up.
Also export a copy as DESIGN.md to my workspace.
```

Commit both to your repo: `DESIGN.md` at root for humans + LLMs, `SKILL.md` under `.claude/skills/` for Claude Code's auto-loading.

## Quality Checks

- [ ] All 9 sections present
- [ ] Color tokens use role names, not brand names
- [ ] Type scale is modular (each step a consistent ratio)
- [ ] No tokens left as raw hex without a `--var` name
- [ ] Spacing scale is base-4 or base-8 — never ad-hoc
- [ ] At least three "Don't" rules call out AI-slop
- [ ] Component stub renders if pasted into [tweakcn.com](https://tweakcn.com)

## Variations

- **Multi-brand company:** run extraction once per brand sub-page in Figma, output to `/design-md/<brand>/<surface>.md`
- **Mobile-only system:** add "iOS-only — use SF Pro and HIG sizing" to the extraction prompt
- **Audit instead of extract:** ask Claude Design to *grade* the Figma file against the 9-section rubric, not regenerate it

## Common Failures

- **DESIGN.md has 47 colors.** Cause: Figma file contains scratch swatches. Fix: clean Figma styles before re-extracting, or ask Claude to "consolidate near-duplicate colors within ΔE < 5."
- **Component section is empty.** Cause: components weren't published. Fix: publish components in Figma, re-export `.fig`.
- **Type scale is non-modular (12, 14, 19, 22, 31).** Cause: ad-hoc Figma sizing. Fix: ask Claude to "snap the type scale to the closest Major Third (1.250x) ramp."
- **Output reads like marketing copy.** Fix: add "no narrative, no marketing language — spec only" to the prompt.
