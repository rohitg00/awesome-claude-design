# Mercury — 90% of a component library inferred in 10 minutes

**Brand:** Mercury
**Industry:** Fintech — banking and financial workflows for startups
**Source:** [Linas Beliūnas — Claude Design Founder's Playbook](https://linas.substack.com/p/claude-design-founders-playbook) (cited in the awesome-claude-design [showcase seed table](../README.md))

## Workflow described

Mercury runs a public marketing site and a substantial product surface, both built on a refined in-house component library — buttons, form controls, data tables, modals, marketing-grade typography, the lot. Replicating that library inside a generic AI design tool is normally a multi-day project: you screenshot, you token-pick, you re-create components one by one and hope the spacing scale lines up.

Linas Beliūnas's reported workflow was different. He pointed Claude Design at the existing Mercury codebase — the public surface plus what was inspectable — and let it do system inference end-to-end:

1. Feed the existing site / repo into Claude Design as the source of truth
2. Let it walk components, tokens, type stack, color roles, spacing scale
3. Get back a working component library that matched the source

The outcome: roughly 90% of Mercury's component library reproduced faithfully — colors, typography, spacing, component variants — in around 10 minutes of inference. Not 90% of the visible UI. 90% of the *system underneath it*. That's the part that normally takes weeks to extract by hand.

## Concrete numbers

- **~90% of the component library inferred** from the existing codebase
- **~10 minutes** of wall-clock time
- Source: Linas Beliūnas, *Claude Design — Founder's Playbook*, citing Mercury as the canonical "existing repo to design system" example

## What's instructive for repo readers

Mercury's 90% in 10 minutes is the cleanest data point we have on Claude Design's *inference* ceiling — what it can extract from a real, in-production system without hand-holding. Three things worth lifting:

1. **Inference quality scales with source quality.** Mercury has a disciplined codebase. The 90% number is a function of that discipline, not just the tool. If your codebase is inconsistent, inference will be too — garbage in, garbage out, but coherent in to coherent out faster than you'd expect.
2. **The remaining 10% is where humans still earn their pay.** Brand voice, motion personality, edge-case components, accessibility tradeoffs — the long tail that makes a system feel like *yours* and not like a competent average. Don't fight the 90/10 split, plan for it.
3. **"Existing repo to design system" is a real workflow, not a demo.** This is the move when you've shipped product but never wrote down a system. Point Claude Design at what you already built, get a system back, then refine. Faster than writing tokens from scratch and grounded in reality from the first commit.

For your own work: if you have a codebase older than six months and no documented design system, this is the first workflow to try. The output is a starting point, not the finish line — but it's a starting point you got in 10 minutes instead of 10 days.
