# Connectors — Slack, Drive, Docs into Claude Design

Wire your team's actual context into Claude Design so it builds against real meeting notes, decks, and threads — not made-up product copy.

<img src="../assets/tags/curated.svg" alt="curated"> <img src="../assets/tags/new.svg" alt="new">

---

## Goal

Pull a Slack thread, a Google Doc, or a Drive folder directly into a Claude Design session so the prototype, deck, or design system reflects what your team actually said. Per Ryan Mather (Anthropic): *"Read the notes from yesterday's product roast meeting and create a deck that addresses every concern."*

## Time

| Step | Wall-clock |
|---|---|
| 1. Enable connectors | 2 min (one-time) |
| 2. Pick the source artifact | 2 min |
| 3. Run the connector-aware prompt | 4 min |
| 4. Verify Claude pulled the right context | 3 min |
| 5. Generate + iterate | 8 min |
| **Total (after one-time setup)** | **~17 min** |

## Inputs

- Pro / Max / Team / Enterprise plan with Claude Design enabled
- An admin who can authorize connectors at the org level (or your own personal connectors if Free-text linked)
- A real source: Slack channel, Slack thread URL, Google Doc URL, or Drive folder
- A target artifact: deck, landing page, prototype screen, or DESIGN.md update

## Steps

### 1. Enable connectors (one-time)

In Claude (claude.ai → Settings → Connectors), authorize:

- **Slack** — gives `slack_search_*`, `slack_read_thread`, `slack_read_channel`
- **Google Drive** — gives Doc + Sheet + Slide reads, folder listings
- **GitHub** (optional but useful for repo-derived briefs)

Org admins enable per-workspace. Personal Pro users can authorize their own. If you only see "Web Search" and no connectors, your plan or workspace policy hasn't enabled them yet.

### 2. Pick the source artifact

Three patterns work cleanly. Don't mix them in one prompt — Claude handles a single source much better than a junk drawer.

- **Single Slack thread** — copy the thread permalink from Slack (right-click message → Copy link)
- **Single Google Doc** — share with your Claude account, copy the URL
- **Drive folder** — share the folder, give Claude the folder URL; expect it to read the top 5–10 docs by recency

### 3. Run the connector-aware prompt

```
Read the [Slack thread / Google Doc / Drive folder] at:
{paste URL}

Summarize the concrete asks in three buckets:
- Decisions made
- Open questions
- Concerns / objections raised by name

Then build a 12-slide deck that:
- Opens with the problem framed in the team's own language
- Addresses every concern in the "Concerns" bucket on its own slide
  with the objector's name in the speaker notes
- Closes with the decisions made and the open questions as next steps

Use the attached DESIGN.md (`/design-md/<family>/<brand>.md`) as the
source of truth for color, type, and component style. Quote at least
three direct phrases from the source so I can verify you actually read it.
```

Drag your `DESIGN.md` into the chat alongside the connector reference.

### 4. Verify Claude pulled the right context

This is the step most people skip. Connectors silently fail when:

- The artifact is in a workspace you forgot to authorize
- The doc is shared with "your org" but Claude is auth'd as a different identity
- The thread is in a private channel Claude wasn't invited to

Sanity check by asking:

```
Before generating, paste back the three most recent timestamps from the
Slack thread and the last edit time on the doc. If you can't, stop and
tell me what failed.
```

If it hallucinates timestamps, the connector isn't actually wired. Re-auth and retry.

### 5. Generate + iterate

Once the source is confirmed, let it build. Then comment inline on slides where the framing missed nuance ("slide 4 misses Priya's point about onboarding friction — pull her exact quote"). Inline comments on the artifact beat re-prompting from scratch.

## Quality Checks

- [ ] Each "concern" slide names the person who raised it
- [ ] At least three direct quotes from the source artifact appear verbatim
- [ ] No invented stats — if the source says "users complained," the deck doesn't claim "47% of users"
- [ ] DESIGN.md tokens are honored (no rogue accent colors)
- [ ] Speaker notes cite the source URL on every slide that pulls from it
- [ ] If Drive folder: list of files actually read appears in the response

## Variations

- **Standup-to-status-page:** point Claude at this week's standup channel, generate a public-facing weekly status page in your DESIGN.md
- **Customer-call-to-landing-page:** transcript in a Doc + DESIGN.md → landing page that uses customer language verbatim
- **Roast-meeting-to-redesign-brief:** the Mather example — design critique notes become a prioritized redesign list with mockups
- **Cross-doc synthesis:** point Claude at a Drive folder of 6 PRDs, ask for a unified roadmap deck

## Common Failures

- **Claude invents quotes.** Cause: connector silent-failed; it generated plausible team-speak instead of reading the source. Fix: always run the verification prompt in Step 4 before generating.
- **Burns through quota fast.** Cause: connectors pull large context windows on every turn. Fix: bundle the connector read into the *first* prompt; don't re-trigger it on every iteration. Subsequent edits should reference what was already loaded.
- **"I don't have access to that link."** Cause: the share permission is "anyone in org" but Claude's connector identity isn't in that org. Fix: share directly with the email tied to your Claude account, or re-auth the connector.
- **Slack thread truncated.** Cause: long threads (>200 messages) get summarized lossily. Fix: ask Claude to read the thread in two passes — first 100 messages, then 100–200 — and merge.
- **Output mixes two unrelated docs.** Cause: pointed at a folder with mixed content. Fix: move the relevant docs to a fresh folder, or pass URLs one at a time.

## References

- [Ryan Mather — 7 tips for Claude Design](https://x.com/Flomerboy/status/2045162321589252458) — tip #4 (connectors-to-Slack/docs) is the source of this recipe
- [Claude connectors documentation](https://support.claude.com/en/articles/10167454-using-connectors-with-claude) — official setup
- [Anthropic Labs — Claude Design overview](https://www.anthropic.com/news/claude-design)
- [Department of Product — Claude Design is here](https://departmentofproduct.substack.com/p/claude-design-is-here-everything) — connector workflow examples
- [Linas Beliūnas — Founder's Playbook](https://linas.substack.com/p/claude-design-founders-playbook) — workflow #6 covers Drive + Doc inputs
