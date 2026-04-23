# Speaker Notes from a Generated Deck

The deck is built. Now you have to deliver it. Pull the speaker notes out of a Claude Design pitch deck so you can rehearse, hand the script to a co-presenter, or feed it to a teleprompter.

<img src="../assets/tags/curated.svg" alt="curated"> <img src="../assets/tags/new.svg" alt="new">

---

## Goal

Extract clean, presenter-ready speaker notes from a Claude Design deck — usually generated alongside the slides via [pitch-deck-from-readme](pitch-deck-from-readme.md). Output: a single Markdown file you can rehearse from, edit by hand, or load into a teleprompter app.

## Time

| Step | Wall-clock |
|---|---|
| 1. Confirm notes exist on every slide | 1 min |
| 2. Extract via the export menu | 2 min |
| 3. Edit voice + add transitions | 6 min |
| 4. Time the read-through | 8 min |
| 5. Load into teleprompter (optional) | 3 min |
| **Total** | **~20 min** |

## Inputs

- A pitch deck generated in Claude Design — ideally via the [pitch-deck-from-readme recipe](pitch-deck-from-readme.md) which already prompts for "Speaker notes on every slide — 2–3 sentences I can read aloud"
- A target delivery surface: rehearsal-only / handoff to a co-presenter / teleprompter / printed cards
- ~20 minutes (don't extract notes the morning of — the read-through reveals voice issues that need editing time)

## Steps

### 1. Confirm notes exist on every slide

Open the deck. Click each slide once and check the speaker notes pane (bottom of the editor, may be collapsed). If notes are missing on any slide, prompt:

```
Add speaker notes to every slide that doesn't have them.
2-3 sentences each, in the same voice as the existing notes.
The notes should be readable aloud, not bullet points.
Match the audience the deck targets ({investors / eng leadership /
sales prospect / internal champion}).
```

Don't extract notes from a deck with gaps. The gaps will show up in the read-through and you'll have to come back for them.

### 2. Extract via the export menu

Two paths:

- **PDF with notes** — `Export → PDF → Include speaker notes`. Produces a side-by-side: slide on left, notes on right. Best for rehearsal binders and printed cards
- **Markdown extract** — `Export → Speaker notes only → Markdown`. Produces a single `.md` file with one section per slide (`## Slide N — {title}` heading + notes paragraph). Best for teleprompter, editing, version control

If your build doesn't expose the Markdown extract option, prompt directly:

```
Export the speaker notes from every slide as a single Markdown
document. Format:

## Slide 1 — {slide title}

{speaker notes verbatim}

---

## Slide 2 — {slide title}

{speaker notes verbatim}

Continue through slide 12. Include slide titles even if not on the
slide visually. No commentary, just the notes.
```

Drop into a `.md` file in your repo (or wherever you keep delivery materials).

### 3. Edit voice + add transitions

Generated notes are usually 80% there. The remaining 20% is what makes the delivery work.

Editing checklist:

- **Cut filler** — "So basically what we're doing here is" → "We're doing this:"
- **Add transitions between slides** — "Which brings us to" / "And the receipts:" / "One more thing:" — Claude won't generate these because each slide's notes are written in isolation
- **Mark pauses explicitly** — `[pause]` after the punchline on slides 1, 6, and 11. The closing line of each section needs a beat
- **Insert your own asides** — `[if asked: $750k seed at $7M post]` for likely Q&A; `[skip if running long: cut slide 9 anecdote]` for stage-time discipline
- **Replace any hype words** — Claude sometimes drops "revolutionary" or "game-changing" into notes even if the slide copy doesn't have them. Cut on sight
- **Re-read slide 1 and slide 12 aloud first** — these set tone and land the close. They need to feel like *you* talking, not a generated script

### 4. Time the read-through

Read the whole notes file aloud at presentation pace. Use a stopwatch. Target:

| Deck length | Note read-time target |
|---|---|
| 12-slide pitch | 8–10 min spoken |
| Conference talk (20–30 slides) | 18–25 min spoken |
| Internal review (8 slides) | 5–7 min spoken |

If you're way over, the notes are too long — cut to the bones, leave only the load-bearing sentences. If you're way under, the notes are too tight — add the proof points and asides that make the delivery breathe.

### 5. Load into teleprompter (optional)

If you're using a teleprompter app (Teleprompter+ on iPad, PromptSmart on iOS, OBS Studio scenes), the Markdown extract pastes cleanly. Most teleprompters strip Markdown and render as scrolling plain text.

Settings to check:

- **Scroll speed** — calibrate against your read-through time
- **Mirror mode** — required if reading off a teleprompter glass
- **Font size** — usually 36–48pt for stage; 24pt for screen-share rehearsal
- **Auto-advance per slide** — most teleprompters can sync slide advance to your scroll position

Print a backup PDF (with notes) regardless. Teleprompters fail.

## Quality Checks

- [ ] Every slide has notes — no gaps
- [ ] Notes read aloud sound like *you*, not a generated voice
- [ ] Transitions between slides exist where the slide topic shifts
- [ ] Pauses marked on slides 1, the section break, and the close
- [ ] No hype words ("revolutionary", "game-changing", "seamless")
- [ ] Total read-through time matches your stage allotment ±15%
- [ ] Q&A asides drafted for the obvious questions
- [ ] Slide 11 (the ask) reads as a specific ask, not "let's chat"
- [ ] Backup PDF printed (or PDF on your phone) — teleprompters fail
- [ ] Co-presenter (if any) has the notes file too

## Variations

- **Co-presenter handoff** — split the notes file by speaker. Use bracket annotations: `[ALEX]` and `[YOU]` per paragraph. Re-export so each presenter has their lines highlighted
- **Conference-talk variant** — extend each slide's notes from 2–3 sentences to 4–6, since you have more stage time per slide. Re-prompt: "expand the notes on each slide to 4–6 sentences, presenter pace"
- **Demo-script variant** — for slides that include a live demo, replace notes with a step-by-step demo script: "Click X. Highlight Y. Say: 'this is the part where Z.'" Prevents on-stage fumbling
- **Internal-review variant** — strip the notes to single sentences. The reader is following along with the deck, not listening to you read; brevity matters more than cadence
- **Voice-narrated version** — feed the notes to the [frontier voice surface](frontier-3d-shaders.md) for an audio walkthrough; pair with the deck for async sharing
- **One-pager from notes** — ask Claude Design to "compress these notes into a 500-word one-pager that captures the same arc"; useful as a leave-behind

## Common Failures

- **Notes read like marketing copy.** Cause: deck was prompted with hype-word language; notes inherited it. Fix: re-prompt notes with "rewrite in spoken voice — direct, no superlatives, the voice a founder uses talking to a peer."
- **Every slide's notes start with "So,".** Cause: TTS-style filler from generation. Fix: find-and-replace `^So, ` → empty string in your editor.
- **Notes don't transition between slides.** Cause: each slide generated in isolation. Fix: add transitions yourself in step 3 — Claude won't do this without explicit slide-pair context.
- **Slide 11 (the ask) is vague.** Cause: README didn't have a specific ask, so notes hedged. Fix: hand-write slide 11's notes; this is the most important paragraph of the deck.
- **Read-through is 50% over the time budget.** Cause: notes are too long for the slide count. Fix: cut to the load-bearing sentences; you can add back during rehearsal if you have time.
- **Teleprompter scrolls past you mid-slide.** Cause: scroll speed calibrated to silent-read pace, not spoken pace. Fix: re-calibrate against a stopwatched read-through; spoken is ~150 wpm, silent-read is ~250 wpm.
- **Lost the notes file because it was only in Claude Design.** Cause: didn't export. Fix: always export to a `.md` in your repo as soon as the deck is final. Don't trust the canvas to be the source of truth for delivery materials.

## References

- [`recipes/pitch-deck-from-readme.md`](pitch-deck-from-readme.md) — the upstream recipe; the deck-generation prompt explicitly asks for "Speaker notes on every slide — 2–3 sentences I can read aloud"
- [Linas Beliūnas — Founder's Playbook](https://linas.substack.com/p/claude-design-founders-playbook) — workflow #5 covers deck delivery prep
- [Lenny's Newsletter — What Claude Design is actually good for](https://www.lennysnewsletter.com/p/what-claude-design-is-actually-good) — slide-deck output ranked as one of the strongest surfaces; speaker-notes export covered
- [Adweek — Anthropic debuts Claude Design for marketing assets, decks, UIs](https://www.adweek.com/media/anthropic-debuts-claude-design-for-building-marketing-assets-decks-and-uis/) — decks as a primary launch positioning surface
- [getpushtoprod — Everything You Need to Know](https://getpushtoprod.substack.com/p/everything-you-need-to-know-about) — Slide template workflow with hand-off detail
