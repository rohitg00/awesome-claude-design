# Pitch Deck from README

Turn a project README into a 12-slide pitch deck in one Claude Design pass. Useful for OSS maintainers pitching internal champions, indie hackers preparing for a sales call, or founders walking a partner through a side project.

<img src="../assets/tags/curated.svg" alt="curated"> <img src="../assets/tags/new.svg" alt="new">

---

## Goal

Generate a polished, on-brand 12-slide deck from an existing README. The README does the work of structuring the narrative; Claude Design does the work of making it look like you spent a week in Keynote.

## Time

| Step | Wall-clock |
|---|---|
| 1. Pick + tighten the README | 5 min |
| 2. Pair it with a DESIGN.md | 1 min |
| 3. Run the deck prompt | 4 min |
| 4. Inline-edit slides 1, 6, 12 | 6 min |
| 5. Export to PDF / PPTX | 2 min |
| **Total** | **~18 min** |

## Inputs

- A README that already has: a one-line pitch, a problem statement, a "what it does" section, and either install steps or examples
- A `DESIGN.md` from `/design-md/<family>/` (or your project's own)
- One audience descriptor: *who is this deck for* (investors / engineering leadership / a specific customer)
- Optional: a logo SVG

## Steps

### 1. Pick + tighten the README

A great deck-from-README needs a great README. Fast audit before you start:

- **Lede** — does the first paragraph say what this *is* in one sentence? If no, fix it before generating.
- **Problem** — is there a paragraph that names the pain in user-language (not feature-language)? If no, write one.
- **Differentiation** — is there a "vs alternatives" line or table? If no, the deck will end up generic.
- **Proof** — any metrics, GitHub stars, customer names, screenshots? Even one helps.

Don't try to make Claude write a deck from a sparse README. Tighten the README first; the deck will inherit the quality.

### 2. Pair it with a DESIGN.md

The deck's visual system comes from `DESIGN.md`, not from defaults. Pick by audience:

- **VCs / financial audience** → [editorial/vercel.md](../design-md/editorial/vercel.md) or `mercury.md` if shipped
- **Developer audience** → [terminal/warp.md](../design-md/terminal/warp.md) or [data-dense/posthog.md](../design-md/data-dense/posthog.md)
- **Creator / consumer audience** → [cinematic/runway.md](../design-md/cinematic/runway.md)
- **Internal champion / corporate** → editorial family, neutral palette

### 3. Run the deck prompt

```
Build a 12-slide pitch deck from the attached README.

Audience: { investors / eng leadership / sales prospect / internal champion }
Goal of the deck: { fund / approve / buy / greenlight }

Use the attached DESIGN.md as the source of truth for color, type,
layout, and component style. Do not invent new tokens.

Slide structure:
 1.  Title — project name + one-line pitch + your name + date
 2.  The problem — in the audience's language, not feature-language
 3.  Why now — what changed in the world that makes this possible/urgent
 4.  Existing solutions and why they fall short — name them by name,
     1–2 sentences each, no strawmen
 5.  Our approach — the core idea in one diagram + one paragraph
 6.  How it works — 3-step flow with concrete primitives
 7.  Proof — every metric, customer, star count, or quote in the README
 8.  Differentiation — feature matrix vs the alternatives in slide 4
 9.  Roadmap — next 3 milestones with rough dates
10.  Team / maintainers — names, faces if available, one line of credibility each
11.  The ask — what specifically do you want from this audience? (dollars,
     headcount, intro, pilot)
12.  Closing — contact + repo link + one memorable line

Tone: confident, specific, no hype words ("revolutionary", "game-changing",
"seamless"). Numbers wherever the README has them. If the README doesn't
support a claim, leave the slide thin rather than pad with filler.

Speaker notes on every slide — 2–3 sentences I can read aloud.
```

Drag both files (README.md + DESIGN.md) into the chat.

### 4. Inline-edit slides 1, 6, 12

These three carry disproportionate weight:

- **Slide 1 (Title)** — the one-line pitch is the whole deck compressed. If it's flat, ask Claude to generate three alternatives and pick.
- **Slide 6 (How it works)** — diagrams are where Claude Design either ships or whiffs. Comment specifically: "the arrows are too thin, scale them to match body weight" or "this should be a 3-column flow, not a stacked list."
- **Slide 12 (Closing)** — the memorable line. Often the README's tagline works; sometimes the deck needs its own. Test by reading slide 12 out loud — does it land?

Other slides usually need light tuning only.

### 5. Export

Claude Design exports to:

- **PDF** — best for circulation, looks identical on every machine
- **PPTX** — best for handoff to a presenter who needs to edit further (sales, IR)
- **Web link** — best for async review with comments

Pick based on who's downstream. PDF for "send and done"; PPTX for "they'll edit"; link for "they'll comment."

## Quality Checks

- [ ] Slide 1's one-liner is the same one your README opens with (consistency = trust)
- [ ] Slide 4 names existing solutions by name, no strawmen
- [ ] Slide 7 contains zero invented metrics — every number traces to the README
- [ ] Slide 11 has a specific ask, not "let's chat"
- [ ] Speaker notes on every slide
- [ ] No hype words: revolutionary / game-changing / seamless / cutting-edge
- [ ] Single accent color (matches `--accent` in DESIGN.md)
- [ ] Mono numerals used in any data slide (per DESIGN.md typography rules)
- [ ] Logo (if provided) appears on slides 1 + 12, nowhere else

## Variations

- **Investor version + customer version from one README:** run the prompt twice with different audience descriptors; keep both, label clearly
- **Conference-talk variant:** swap "the ask" for "what to take away" — slide 11 becomes 3 takeaways
- **Deck-as-changelog:** generate from a CHANGELOG instead of README; useful for quarterly reviews
- **One-pager + deck combined:** ask Claude to also produce a single-page PDF summary alongside; uses same DESIGN.md tokens
- **Fundraising deep-dive:** add a slide 13 with TAM / SAM / SOM if the audience expects it; most pre-seed decks should *not*
- **Internal champion deck:** swap slide 8 (differentiation) for "implementation timeline + cost"

## Common Failures

- **The deck is generic despite a great README.** Cause: DESIGN.md was attached but not enforced — the deck used Claude Design defaults. Fix: re-prompt with "use only the colors and fonts in the attached DESIGN.md; the current deck uses a font not in that file."
- **Slide 7 invented stats.** Cause: README didn't have proof points; Claude filled in. Fix: re-prompt with "remove every claim not directly supported by the README; leave slide 7 thin."
- **Diagrams look like Visio from 2008.** Cause: default diagram styling. Fix: comment inline "redraw this diagram using the brand's accent line weight and the body font, no clip-art arrows."
- **12 slides feels thin.** Cause: README is more product-doc than pitch. Fix: tighten the README's problem + differentiation sections, regenerate. Don't pad slides.
- **Slide 11 says "let's discuss."** Cause: weak prompt for the ask. Fix: re-prompt with the specific ask in your own words ("ask for $750k seed at $7M post" / "ask for 2 engineers + Q3 launch slot").
- **Burns through quota fast.** Cause: deck generation is one of the heavier Claude Design operations. Fix: get the structure right in the first pass; iterate inline rather than regenerating from scratch.

## References

- [Anthropic — Claude Design launch](https://www.anthropic.com/news/claude-design) — pitch decks called out as a primary collateral surface
- [Linas Beliūnas — Founder's Playbook](https://linas.substack.com/p/claude-design-founders-playbook) — deck workflow #5 in the 8-workflow set
- [getpushtoprod — Everything You Need to Know](https://getpushtoprod.substack.com/p/everything-you-need-to-know-about) — 4-template workflow including Slide template
- [Lenny's Newsletter — What Claude Design is actually good for](https://www.lennysnewsletter.com/p/what-claude-design-is-actually-good) — slides covered as a top use-case
- [Adweek — Anthropic debuts Claude Design for marketing assets, decks, UIs](https://www.adweek.com/media/anthropic-debuts-claude-design-for-building-marketing-assets-decks-and-uis/) — decks as a primary launch positioning
- [Peter Yang — 16-min everything build](https://creatoreconomy.so/p/claude-design-everything-you-can-build) — deck generation included in the all-in-one demo
