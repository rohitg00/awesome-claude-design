# Comment-Paste Workaround

When a full chat re-prompt would cost too much weekly allowance, paste the would-be prompt as an inline comment on the element instead. Same intent, fraction of the tokens.

<img src="../assets/tags/community.svg" alt="community"> <img src="../assets/tags/new.svg" alt="new">

---

## Goal

Get the precision of a written prompt without paying the full chat-regeneration cost. The community-discovered move (catalyzed by [MacStories' "comment-on-element covers 95%" observation](https://www.macstories.net/stories/hands-on-with-anthropic-labs-claude-design-preview/)): when you find yourself about to type a long chat prompt, stop, right-click the specific element, and paste the prompt into the comment field instead.

## Time

| Step | Wall-clock |
|---|---|
| 1. Catch yourself about to chat | 3 sec |
| 2. Right-click the target element | 2 sec |
| 3. Paste the would-be prompt as a comment | 30 sec |
| 4. Wait for local re-render | 20–60 sec |
| 5. Iterate or move on | — |
| **Total** | **~1 min, low token cost** |

## Inputs

- A generated artifact open in Claude Design
- A specific element you want to change (button, card, image, heading, section)
- The exact prompt you would otherwise have typed in chat

## Why this works

Chat re-prompts re-load the entire artifact into vision context every turn. A 4-screen prototype at iteration 6 might be eating 80k+ vision tokens per chat round just to re-derive what's already on the canvas.

Inline comments scope the operation to a single element. Claude Design re-renders that element (and whatever depends on it) without re-deriving the whole scene. Per [Ryan Mather's tip 2](https://x.com/Flomerboy/status/2045162321589252458), comments are the canonical move for component-level edits.

The MacStories piece pushed this further: even prompts that *feel* like they need full chat — voice / phrasing / iconography swaps across a whole section — often work as comments on the section header. "95% of what's needed" was the framing, and the launch-week iteration data backs it.

## Steps

### 1. Catch yourself

The discipline is hard. Most users default to chat because it's the most prominent surface. Build the reflex: every time you start typing in the chat box, ask "could this be a comment instead?"

If the answer is "yes" or "maybe" — close the chat box, comment instead.

### 2. Right-click the target

In the canvas, right-click (or two-finger click on Mac) the element you want to change. The comment popover appears anchored to that element.

If the element is a section header, your comment scopes to the whole section. If it's a single button, it scopes to that button. Pick the smallest scope that captures the change.

### 3. Paste the would-be prompt

Take the prompt you were about to type in chat — *exactly the same words* — and paste it into the comment field. Don't shorten it. Don't water it down. Comments accept the same prompt language chat does.

Examples of prompts that work as comments:

```
On a hero headline:
"Rewrite this with more confidence — drop the hedging.
The current copy says 'might help you ship'; aim for
'ships your design system in 20 minutes.'"
```

```
On a feature card:
"Replace the icon with one that matches the editorial
family — current icon reads as a generic SaaS lucide
icon. Use a custom illustration in the brand palette."
```

```
On a section header:
"Tighten this whole section. Cut the third feature card,
move the CTA up, reduce the section padding by one step
on mobile. Keep the same copy."
```

```
On a deck slide:
"Re-write the speaker notes for this slide in a more
direct voice. Current notes are too presenter-y. Aim for
the voice in slide 1's notes."
```

That last one — speaker notes edits — is one most people reach for chat on. Comment-on-slide handles it.

### 4. Wait for the local re-render

Component re-renders are 20–60 seconds. Section re-renders are slightly longer. You can keep working in another part of the canvas while it processes.

### 5. Iterate or move on

If the comment landed: move on. If it didn't: refine the comment on the same element rather than escalating to chat. Three comment iterations on one element still cost less than one chat re-prompt of the full artifact.

## When this is the right move (and when it isn't)

**Use comment-paste for:**

- Voice / phrasing changes scoped to a section
- Icon / image / illustration swaps
- Layout tweaks within a single component
- Speaker-notes rewrites on a deck slide
- Color / weight / spacing adjustments to a heading or CTA
- Removing or adding a single feature card / row / item
- "Make this more X" prompts where X is local (more confident, more compact, more on-brand)

**Use chat for:**

- Adding a whole new section that doesn't exist yet
- Changing the page intent ("this is now a pricing page, not a product page")
- Conceptual pivots ("redo for a B2C audience instead of B2B")
- Re-deriving the whole token system

A working test: if you can point at the change with your finger, comment. If you can't, chat.

## Quality Checks

- [ ] Caught yourself before typing the chat prompt
- [ ] Comment scope is the smallest element that captures the change
- [ ] Prompt language is the same precision as chat — not watered down
- [ ] Re-render produced what you wanted (don't accept "close enough" silently)
- [ ] If three comment iterations didn't land, you escalated to chat rather than spamming comments
- [ ] You logged which prompt patterns work as comments — internalizing for next session

## Variations

- **Speaker-notes-only edits on a deck** — every notes rewrite via comment-on-slide; reserve chat for new slides only
- **Whole-section voice rewrite** — comment on the section header, write the prompt there; Claude rewrites all child copy in one local pass
- **Iconography pass** — go through every icon on a page, comment-replace each. Faster than asking chat to "review all icons"
- **Mobile-only adjustments** — comment with "mobile only: tighten padding by one step, hide the secondary CTA"; Claude scopes the change to the mobile breakpoint
- **Empty-state polish** — empty states almost always need 3–5 small fixes. Comment them all instead of one big chat prompt

## Common Failures

- **Comment didn't trigger a re-render.** Cause: comment was on the canvas background, not on an element. Fix: right-click *on* the element (button, card, image), not next to it. Look for the popover anchor visual.
- **Re-render changed more than you wanted.** Cause: comment scope was the section header, not the specific child. Fix: comment on the smaller element next time. Or comment with explicit scope: "only the third card, not the others."
- **You watered down the prompt.** Cause: comments feel like they should be short. Fix: comments accept the same prompt complexity chat does. Paste the full prompt.
- **Three comments in, still not right.** Cause: the change is actually structural, not local. Fix: escalate to chat. The comment-paste workaround is for component-level work; structural changes need full chat context.
- **You forgot which element you commented on.** Cause: comments are anchored visually but easy to lose track of in a long iteration session. Fix: open the comments panel periodically; resolve completed comments to keep the canvas clean.
- **Burned quota anyway because of comment volume.** Cause: ten comments at once, each triggering a partial re-render. Fix: batch related comments before triggering re-render; or pause briefly between comments to let one finish before the next.

## References

- [MacStories — Hands-On with Anthropic Labs' Claude Design Preview](https://www.macstories.net/stories/hands-on-with-anthropic-labs-claude-design-preview/) — the "comment-on-element covers 95% of what's needed" observation that named this pattern
- [Ryan Mather — 7 tips for Claude Design](https://x.com/Flomerboy/status/2045162321589252458) — tip #2 ("Comment, don't chat") is the broader version of this
- [Austin Lau (Anthropic) — Tweaks panel demo](https://x.com/helloitsaustin/status/2045176910569980318) — pairs cleanly: Tweaks for layout, comments for components, chat for structure
- [`recipes/tweaks-panel-sidebar.md`](tweaks-panel-sidebar.md) — the layout-level half of the no-regen iteration model
- [`recipes/token-budget-claude-design.md`](token-budget-claude-design.md) — Phase 3 of the broader budget recipe is built on this exact workaround
