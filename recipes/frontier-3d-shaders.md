# Frontier Features — 3D, Shaders, Voice, Video

Claude Design ships native generation for the surfaces that previously needed Three.js, Spline, ElevenLabs, or Runway. This recipe covers how to actually use them — and the one public worked example to study before you start.

<img src="../assets/tags/curated.svg" alt="curated"> <img src="../assets/tags/new.svg" alt="new">

---

## Goal

Build a real frontier feature — a 3D hero, an animated shader background, a voice walkthrough, or a 90-second brand video — inside one Claude Design session. Avoid the trap of treating the frontier surfaces as gimmicks; treat them as design primitives with their own constraints.

## Time

| Step | Wall-clock |
|---|---|
| 1. Pick the surface + reference | 5 min |
| 2. Brief Claude Design with constraints | 4 min |
| 3. First generation pass | 3–8 min (depends on surface) |
| 4. Tighten via inline comments | 10 min |
| 5. Export to the right format | 3 min |
| **Total** | **~25–30 min** |

## Inputs

- A `DESIGN.md` from `/design-md/<family>/` so the frontier output inherits your system tokens (color, type, motion)
- One concrete surface picked: 3D scene · shader background · voice narration · short brand video
- A reference (one URL, one screenshot, or one short description of the motion you want)
- A target context: where this lives — hero section, loading state, splash screen, demo page

## Surfaces, briefly

Per the [Anthropic launch post](https://www.anthropic.com/news/claude-design-anthropic-labs), Claude Design ships native generation for **Voice, Video, 3D, and Shaders** alongside the standard prototype/deck/page surfaces. Each has different cost and iteration shape:

| Surface | What it's good for | What it's not |
|---|---|---|
| **3D** | Hero objects, product spins, abstract geometry | Full game scenes, physics simulations |
| **Shaders** | Animated backgrounds, gradient fields, hover effects | Photorealistic textures, video-quality lighting |
| **Voice** | Narration over a deck, an audio walkthrough, accessibility passes | Multi-character dialogue, music |
| **Video** | 30–90s brand films, screen-recording-style demos | Long-form (>2 min), live action, complex VFX |

## Steps

### 1. Pick the surface + reference

Don't let Claude pick. Walk in with a decision: *"3D helix as the hero, slowly rotating, brand-accent gradient on the strands."* Vague briefs ("make it pop with 3D") burn tokens generating things you'll throw away.

Reference shapes that work:

- **For 3D** — a still screenshot of the geometry you want, or a CodePen URL
- **For shaders** — a `.glsl` snippet you like, or "the [Vercel](https://vercel.com) hero gradient"
- **For voice** — 1–2 paragraphs of narration text + a tone descriptor ("warm, deliberate, no hype")
- **For video** — a moodboard URL, a competitor's hero video, or "screen-recording style with terminal cursor"

### 2. Brief Claude Design

Use this template — the constraint blocks matter most.

```
Build a {3D scene / shader background / voice narration / brand video}
for the {hero / loading state / demo page / about page}.

Reference: {paste URL or describe in one sentence}

Use the attached DESIGN.md as the source of truth for color, type,
motion easing, and accent placement. The frontier output must inherit
the same tokens — do not introduce new colors or fonts.

Constraints:
 - Surface: {explicit format — WebGL canvas / GLSL fragment shader /
   MP3 narration / MP4 video at 1920x1080}
 - Duration / size: {3D = "loops every 8s" / shader = "60fps target" /
   voice = "under 90s" / video = "under 60s"}
 - Performance budget: {must run on mid-tier laptop without fan spin /
   under 200KB shader code / under 2MB MP3 / under 10MB MP4}
 - Accessibility: {prefers-reduced-motion fallback / captions for
   voice + video / static frame fallback for 3D + shader}

Output one version. I will iterate inline; do not generate variants
in this pass.
```

Drag the `DESIGN.md` into the chat with the brief.

### 3. First generation pass

Frontier surfaces take longer than a 2D page — budget 3–8 minutes for the first paint depending on surface:

- **3D** — 3–5 min (geometry + materials + lighting)
- **Shaders** — 1–2 min (single fragment shader is fast)
- **Voice** — 1–2 min (TTS render)
- **Video** — 5–8 min (longest; multi-frame composition)

Don't refresh or re-prompt during this. Each false start re-loads vision context and burns weekly allowance. See the [token budget recipe](token-budget-claude-design.md) for the full spend model.

### 4. Tighten via inline comments

This is where frontier output usually breaks. Default 3D scenes are too busy, default shaders are too saturated, default voice is too announcer-y, default video is too montage-cut. Comment specifically on the failure:

- **3D** — "the helix rotation is too fast — slow to one revolution per 12 seconds" / "ambient light is washing out the accent — drop ambient by 40%"
- **Shaders** — "the noise pattern is too high-frequency — scale the noise period 2x" / "the gradient stops are at 50%, push to 30/70"
- **Voice** — "the narrator sounds rushed in sentence 2 — add a 0.4s pause after 'we shipped'" / "drop the upward inflection on 'right?'"
- **Video** — "cut 1 (logo zoom) is too aggressive — replace with a slow dolly-in over 3s" / "the title card holds too long — trim to 1.2s"

Inline comments are massively cheaper than chat re-prompts on frontier surfaces because the renderer reuses the existing scene/audio/video and edits in place. (See Austin Lau's [Tweaks demo](https://x.com/helloitsaustin/status/2045176910569980318) for the same pattern on 2D layouts.)

### 5. Export

| Surface | Best export |
|---|---|
| 3D | `<canvas>` + Three.js scene file, or compiled GLB for a portfolio |
| Shader | GLSL fragment + a JS wrapper, or compiled MP4 loop for sites without WebGL |
| Voice | MP3 + WebVTT captions in one zip |
| Video | MP4 (H.264) + a poster frame PNG; ask for a vertical 9:16 cut if you need socials |

## Quality Checks

- [ ] The frontier output uses the DESIGN.md accent color, not a default purple/teal
- [ ] Motion eases match DESIGN.md easing tokens (no default `ease-in-out` everywhere)
- [ ] `prefers-reduced-motion` fallback exists (static frame for 3D/shader, no autoplay for video)
- [ ] Shader runs at 60fps on a 2021 MacBook Air or equivalent
- [ ] 3D scene has no more than one accent material — busy = AI-slop tell
- [ ] Voice narration has no hype words ("revolutionary", "game-changing")
- [ ] Video is under 90s and exports a poster frame
- [ ] Captions / transcript ship for any voice or video output

## Variations

- **3D portfolio piece** — see Ileana Marcut's [3D Helix portfolio](https://ileanamarcut.substack.com/p/claude-design) for the full prompt sequence; the only public worked example with prompts visible end-to-end. Useful as a calibration point: how she briefed the geometry, how she iterated the lighting, how she handed off to Three.js
- **Shader-as-section-divider** — generate a thin (200px tall) animated band that loops; use as a section break instead of a static SVG
- **Voice walkthrough on a deck** — pair with the [pitch-deck recipe](pitch-deck-from-readme.md): generate the deck first, then ask Claude Design to narrate the speaker notes in one pass
- **Brand video from a static landing page** — capture your shipped landing in [web-capture-to-prototype](web-capture-to-prototype.md), then ask for a 30s motion version using the same DESIGN.md tokens
- **Loading-state shader** — replace the standard skeleton-loader with a brand-colored shader; pairs cleanly with the system from any DESIGN.md in `/design-md/cinematic/` or `/design-md/glass/`

## Common Failures

- **3D scene looks like a stock asset.** Cause: brief was too generic; Claude defaulted to a "hero geometry" template. Fix: re-brief with an explicit reference URL and one constraint about geometry style ("low-poly, faceted normals, no smooth shading")
- **Shader pegs the GPU.** Cause: nested loops in the fragment shader, or `texture()` calls in a tight loop. Fix: ask Claude to "rewrite without dynamic loops; precompute the noise field"
- **Voice narration sounds like a podcast ad.** Cause: default TTS preset. Fix: re-prompt with explicit tone — "deliberate, no rising inflection, pauses between clauses, like a museum audio guide"
- **Video is a slideshow with transitions.** Cause: Claude assembled stills with crossfades because no motion direction was given. Fix: re-brief with explicit camera direction ("3s slow dolly in on logo, hold 2s, cut to product detail")
- **Generated 3D / video doesn't inherit DESIGN.md colors.** Cause: vision-model defaulted to its own palette for the new surface. Fix: paste the hex values directly into the brief — "primary surface: #1a1a1a, accent: #c96442, background: #f4f1ec, do not deviate"
- **Burns through quota in one frontier prompt.** Cause: video and 3D are the heaviest operations Claude Design runs. Fix: budget the entire weekly allowance for one frontier piece if it's hero-grade; keep iteration in inline comments per [token budget](token-budget-claude-design.md)

## References

- [Anthropic — Claude Design launch post](https://www.anthropic.com/news/claude-design-anthropic-labs) — frontier features (Voice, Video, 3D, Shaders) called out as native generation surfaces
- [Ileana Marcut — Claude Design: Building a 3D Helix Portfolio](https://ileanamarcut.substack.com/p/claude-design) — the only public worked 3D example with prompts shown end-to-end
- [Peter Yang — 16-min everything build](https://x.com/petergyang/status/2045527271650558383) — includes brand video generation; "creates beautiful videos, more so than slides"
- [Ryan Mather — 7 tips for Claude Design](https://x.com/Flomerboy/status/2045162321589252458) — tip #3 (demo with video) sets the prior for motion-as-input
- [`recipes/token-budget-claude-design.md`](token-budget-claude-design.md) — frontier surfaces cost more; budget accordingly
