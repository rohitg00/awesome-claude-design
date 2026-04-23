# Datadog — a week of design review in one conversation

**Brand:** Datadog
**Industry:** Cloud observability — metrics, logs, APM, security telemetry for engineering teams
**Source:** [Anthropic launch post](https://www.anthropic.com/news/claude-design-anthropic-labs) (2026-04-17)

## Workflow described

Datadog's product team runs a prototyping loop that, before Claude Design, looked like most enterprise SaaS design loops:

1. PM writes a brief
2. Designer turns the brief into mockups in Figma
3. Mockups go into a review with engineering, design system owners, and stakeholders
4. Notes come back, designer revises, another review is scheduled
5. After roughly a week of cycles, a working prototype gets handed to engineering to build for real

That sequence collapsed into a single Claude Design conversation. The team can now sit in a room — or a call — with a rough idea, generate a working prototype while the conversation is still happening, and have the prototype reflect Datadog's brand language and design guidelines without the designer manually re-applying them at the end.

The compression isn't just about speed. The conversational format means stakeholders see the prototype evolve in real time, which surfaces disagreements early instead of after a week of polished asset production.

## Concrete numbers

- **1 week of brief → mockup → review cycles → 1 conversation**
- Quote, Aneesh Kethini, Product Manager at Datadog: *"We've gone from a rough idea to a working prototype before anyone leaves the room."*
- Brand consistency and design guidelines preserved without a separate "apply the design system" pass

## What's instructive for repo readers

Datadog is observability — data-dense dashboards, dense type, hundreds of components, strict brand discipline. If a single conversation can hit that bar, the workflow generalizes downward to less-strict surfaces, not the other way around.

Three takeaways:

1. **The bottleneck is meeting cadence, not Figma speed.** A week-long loop isn't a week of design work — it's a week of waiting for the next review slot. Compressing the loop means doing the review *during* generation, while the prototype is plastic.
2. **"Before anyone leaves the room" is the real metric.** Replace your old benchmark (time-to-first-mockup) with a new one: time-to-decision-while-stakeholders-are-still-engaged. That's what Aneesh's quote is actually measuring.
3. **Brand consistency has to be built in, not bolted on.** Datadog could collapse the loop because Claude Design held their brand language across the conversation. If your tool needs a "make it on-brand" pass at the end, you haven't actually compressed anything — you've just moved the meeting.

For your team: pick one weekly design review meeting. Try replacing the prep with a live Claude Design session in the meeting itself. The output won't be a deck — it'll be a prototype people can click.
