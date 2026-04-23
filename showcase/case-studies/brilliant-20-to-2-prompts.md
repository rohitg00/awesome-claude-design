# Brilliant — 20 prompts to 2

**Brand:** Brilliant
**Industry:** Education technology — interactive lessons in math, science, and programming
**Source:** [Anthropic launch post](https://www.anthropic.com/news/claude-design-anthropic-labs) (2026-04-17), corroborated in the [Linas Beliūnas Founder's Playbook](https://linas.substack.com/p/claude-design-founders-playbook)

## Workflow described

Brilliant's surfaces are animation-heavy and interaction-dense — the kind of pages that historically take a long compounding chain of prompts to recreate in a generic AI design tool, because every step of the lesson needs custom motion, custom state, and a coherent visual language that survives across screens.

Their internal loop before Claude Design:

1. Senior product designer drafts the lesson surface in Figma
2. Hand to engineering for prototype build, often lossy
3. Iterate through ~20 prompt cycles in a competing AI tool to recreate the design in working code
4. Hand the prototype to research for user testing — usually after another round of code review

After adopting Claude Design, the loop collapsed. The same complex surfaces that previously took 20+ prompts to reproduce in another tool were landing in 2 prompts. The team also started turning static mockups directly into interactive prototypes that were shareable for user testing without going through engineering code review first — a step that used to gate every research session.

## Concrete numbers

- **20+ prompts → 2 prompts** for the most complex surfaces (an order-of-magnitude reduction)
- **Static mockup → interactive prototype** without an engineering code-review gate
- Quote, Olivia Xu, Senior Product Designer at Brilliant: *"Our most complex pages, which took 20+ prompts to recreate in other tools, only required 2 prompts in Claude Design."*

## What's instructive for repo readers

Three things worth lifting from Brilliant's loop, even if you don't ship a learn-to-code product:

1. **Prompt-count is a proxy for design-system fit.** If your AI tool needs 20 prompts for one surface, you're paying tax on every iteration. The fix isn't a better prompt — it's giving the tool enough of your system upfront (tokens, components, motion rules) that it can one-shot variants. Claude Design absorbing the existing system is what cut 20 down to 2.
2. **"Prototype without code review" is a research unlock, not a shortcut.** Brilliant's win wasn't "skip engineering" — it was "stop blocking user research on engineering availability." That's a workflow change, not a tool change.
3. **Animation-heavy surfaces are the hardest test.** If a tool can survive interactive lesson UI, it can survive a marketing page. Pick your benchmark from your hardest case, not your easiest.

For your own loop: start by measuring prompt-count-per-surface in your current tool. That's your baseline. Anything that compresses it 5x is worth a workflow change.
