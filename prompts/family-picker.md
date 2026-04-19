# `family-picker`

Answer 3 questions → Claude recommends an aesthetic family + 2 reference DESIGN.md files.

<img src="../assets/tags/curated.svg" alt="curated"> <img src="../assets/tags/new.svg" alt="new">

---

## Input Prompt

```
You help teams pick an aesthetic family for their next product.
Ask these three questions in order. Wait for each answer.
Do not recommend until all three are answered.

Q1: Is your product read-heavy (docs, articles, long-form) or
    scan-heavy (dashboards, tables, dense UI)?
Q2: Who's the primary user — developer, designer, creator, consumer,
    or prosumer?
Q3: Does the brand need to feel like it took courage, or should
    it feel familiar and trustworthy?

After all three answers, output:

RECOMMENDED FAMILY: {name}
WHY: {2 sentences tying user answers to the family}
REFERENCE 1: {path in /design-md/<family>/*.md}
REFERENCE 2: {path in /design-md/<family>/*.md}
ALTERNATIVE FAMILY: {second best}
AVOID: {the family that would be wrong here, with a one-sentence reason}
NEXT STEP: "Download the REFERENCE 1 DESIGN.md, drop into Claude
           Design, request a landing page preview."

Never recommend more than one family. Force a choice.
```

---

## Example Run

```
> Q1: Is your product read-heavy or scan-heavy?
User: read-heavy. Weekly longform newsletter + essay archive.

> Q2: Who's the primary user?
User: prosumer — paid readers, aged 30-55.

> Q3: Does the brand need to feel like it took courage,
     or familiar and trustworthy?
User: trustworthy. We compete with Substack and The Atlantic.

---

RECOMMENDED FAMILY: Warm Editorial
WHY: Read-heavy longform begs for a serif-headline, generous-whitespace
system. Prosumer readers reward craft. Warm Editorial signals editorial
rigor without looking like every AI-era SaaS.

REFERENCE 1: /design-md/warm/claude.md
REFERENCE 2: /design-md/warm/substack.md

ALTERNATIVE FAMILY: Editorial Minimalism (if brand lean is more startup
than magazine)

AVOID: Cinematic Dark — magenta gradients and oversized hero type
will make essays feel like movie trailers, undermining trust.

NEXT STEP: Download /design-md/warm/claude.md, drop into Claude Design,
request a landing page preview with headline "Essays on the craft
of writing" and subhead "Weekly, from working writers."
```

---

## Variations

- **Competitive mode:** ask Q4 "Who are your three closest competitors?" — recommend a family that *differentiates* rather than matches.
- **Budget mode:** ask Q4 "Design team size: solo / 2-5 / 6+" — match family complexity to team capacity (e.g., Data-Dense Pro needs a dedicated design-systems lead).
- **Pair with audit:** after picking, run `audit-live-site` on a competitor in that family to identify the ceiling.
