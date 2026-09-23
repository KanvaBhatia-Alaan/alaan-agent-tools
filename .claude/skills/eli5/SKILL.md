---
name: eli5
description: "Explain anything like the user is 5 — build a picture-first HTML page with huge visuals, tiny amounts of text, and publish it as an artifact. Use when the user types /eli5 or asks for a dead-simple, visual explanation of a concept, codebase, system, or error."
---

# ELI5 — Explain Like I'm 5

Turn a topic into a **picture book for grown-ups**: giant visuals, almost no words.

## Steps

1. **Understand the thing first.** If it's about this codebase, read the relevant files / run the searches you need. Never explain from a guess — a simple explanation of the wrong thing is worse than no explanation. If the topic is genuinely ambiguous, ask one short question before building.
2. **Compress to 5–7 beats.** Every page is one idea. If you can't draw it, you don't understand it yet.
3. **Find one everyday metaphor** and hold it for the whole page — mailroom, lunchbox, LEGO, waiter in a restaurant, bouncer at a door. Don't mix metaphors mid-way.
4. **Write the HTML** to a file (scratchpad dir unless the user names a place).
5. **Publish with the Artifact tool** and hand back the link. Load the `artifact-design` skill first, as Artifact requires. Give it a playful `favicon` and a short `<title>`.
6. **Reply in chat with 2–3 lines max** plus the link. Don't re-explain the thing in the terminal — the page is the answer.

## The word budget (this is the whole skill)

- Page title: **≤ 6 words**
- Each section heading: **≤ 5 words**
- Each caption under a visual: **≤ 15 words, one sentence**
- Total prose on the page: **under 150 words**
- Ban: jargon, acronyms (unless drawn), "leverage", "utilize", nested clauses, bullet lists of 6+
- Allowed: one "Now the grown-up words" glossary strip at the very bottom mapping baby-word → real term. This is where `idempotent`, `mutex`, `webhook` are finally allowed to appear.

If a sentence needs a comma to survive, cut it in two.

## The pictures matter more than the words

Visuals must be **self-contained** — the artifact CSP blocks every external host. No image URLs, no CDN icon fonts.

Build them from:
- **Inline SVG** — hand-authored, thick strokes (6–10px), flat bold fills, rounded caps. This is the default.
- **Mermaid** in `<pre class="mermaid">` blocks — artifacts render it natively. Good for flows and sequences.
- **Big emoji** as characters in a scene (4–8rem), arranged with CSS grid/flex.
- **CSS-drawn shapes** — boxes, pipes, arrows, stacked layers.

Rules of thumb:
- Each visual is at least **300px tall** and dominates its section — the caption is a footnote to the picture, not the reverse.
- Use a **small cast**: pick 3–4 recurring characters (e.g. 🙋 the user, 📮 the request, 🏭 the server, 🗄️ the database) and reuse the exact same glyph/shape/color for each one on every page. Consistency is what makes it click.
- **Color = meaning.** One hue per character, reused everywhere. Never decorative-only color.
- Label things *in* the picture (text inside the SVG), so the caption can stay short.
- Animate only if it teaches — a dot travelling along a request path, yes; a spinning logo, no. Respect `prefers-reduced-motion`.

## Page shape

```
[ Giant title + one-line "what this is" ]
[ Beat 1: huge visual → 1 caption ]
[ Beat 2: huge visual → 1 caption ]
...
[ "Now the grown-up words" — baby term → real term glossary ]
```

Big type (body ≥ 20px), generous whitespace, high contrast, light+dark themed per the Artifact rules, one visual per vertical scroll-stop. Playful is good; childish-condescending is not — the reader is smart and busy, not stupid.

## Don'ts

- Don't dumb down to the point of being **wrong**. Simplify the shape, keep the truth. If a simplification leaks, say so in one line at the bottom ("Real life is messier: …").
- Don't produce a wall of text with a decorative header image. That's the failure mode this skill exists to prevent.
- Don't skip the artifact — a `.html` file left on disk isn't the deliverable; the link is.
