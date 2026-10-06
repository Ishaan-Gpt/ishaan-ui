# Taste: what makes a website feel premium

## Contents
1. The core idea
2. Finding the visual idea (never the first one)
3. Colour
4. Typography
5. Layout and rhythm
6. Copy
7. Honesty
8. The anti-slop list (with reasons)

---

## 1. The core idea

Premium sites feel *authored*. One person with taste made consistent decisions about everything: a single visual metaphor, one accent colour, two typefaces, a motion personality, and an asset style that could only belong to this brand. Generic sites feel *assembled*: a hero from here, a feature grid from there, icons from a library, a gradient because gradients are popular.

So every decision should answer: *does this belong to this brand and this idea?* If a component could be dropped onto any other site unchanged, it is not finished.

## 2. Finding the visual idea (never the first one)

Before designing, generate 3 or 4 directions and write each as one sentence. Examples of the shape (not to copy):
- "Painted pastoral skies with glass panes floating over them; calm, warm, human."
- "A printed field guide: engraved line art, stamps, postmarks, paper grain."
- "Instrument panel: watch-bezel dials, hairlines, precise mono numerals."

Discard the first (it's usually the most common), then pick the one that best fits the brand's promise. Strong sites often combine one *environment* (sky, paper, studio, night city) with one *object language* (glass, stamps, dials, lenses). Name the metaphor and let it generate details: a "lens" brand gets a loupe logo, a loader where the lens opens, a scanning transition.

Write down why you chose it in one line; tell the user.

## 3. Colour

- **Derive, don't default.** Start from the brand's existing colours, the product's subject, and the reference. Never ship a framework's default palette.
- **Structure**: canvas (the page), surface (cards), ink (text, 2–3 steps), one accent, status colours (success/warning/danger) tuned to the palette, a line colour at low alpha.
- **Warm neutrals beat pure greys.** Off-white canvases (e.g. a cream around `#f2efe5`) and warm near-black ink (e.g. `#2b2927`) read as crafted; pure `#fff`/`#000` read as default.
- **One accent, used with intent**: primary buttons, key highlights, focus rings, a few accent words. If everything is accented, nothing is.
- **Pastel accents need contrast care.** If the accent is soft (e.g. a pastel apricot), put ink-coloured text on it, and create a darker "accent-ink" shade for any small accent text so it passes contrast.
- **Status colours** should be desaturated to sit in the palette (a sage green, a burnt amber, a brick red), not neon.
- Put colours in CSS custom properties (tokens) and map them into the styling system; components only use tokens.

## 4. Typography

- **Pairing**: an expressive display face for headings + a calm grotesk for UI and body. A serif display with an *italic second line or italic accent word* is a strong default for warm brands; a tight grotesk display suits technical brands.
- **Scale with confidence**: hero headlines are big (64–110px desktop), tight leading (0.95–1.05), slight negative tracking. Body 15–18px with 1.5–1.6 line height, muted ink.
- **Italic as emphasis**, not bold. Split headlines into a plain line and an italic line.
- **Numbers**: tabular figures; big numerals in the display face look editorial.
- Load fonts with the framework's font loader (no layout shift). At most two families plus a mono if genuinely needed.

## 5. Layout and rhythm

- Generous vertical rhythm (100–160px between sections on desktop), narrow measure for text (≤ 600px), wide for product visuals.
- Centered headline sections alternate with asymmetric splits (text left / live UI right).
- Big rounded "panels" (24–32px radius) that hold an environment (painted sky, photo, texture) with glass UI floating inside are a reliable premium device.
- Let decorative elements break the grid (branches overlapping a panel edge), but never cover content or interactive UI; put them behind the panel if they collide.
- Mobile is designed, not squashed: re-order, reduce decoration, keep tap targets ≥ 44px, no horizontal scroll.

## 6. Copy

- Headlines are specific and human: what the product does for the reader, in their words. Avoid category slogans.
- Short sentences. No hype words ("revolutionary", "unlock", "supercharge", "seamless", "leverage").
- Every section heading should make sense on its own, without a label above it.
- Microcopy is part of the design: empty states, loading labels, errors ("A passing cloud").

## 7. Honesty

- Never invent testimonials, logos, user counts, ratings or metrics. Leave them out or ask.
- Sample data in demos uses obviously fictional names and `.example` domains, and is labelled as sample where it could be mistaken for real.
- Label estimates as estimates. Don't claim integrations or features that don't exist.

## 8. The anti-slop list (and why)

| Don't | Why | Do instead |
|---|---|---|
| Icon libraries (lucide, heroicons, etc.) | Instantly recognisable; makes every site look the same | Draw a custom SVG set in one hand (`assets.md`) |
| Prebuilt component kits used as-is | Same shapes and spacing as thousands of sites | Write components for the brand; restyle any library you must keep |
| Eyebrow/kicker tags above titles ("FEATURES", "Built for:", "STUDIO / OVERVIEW") | Reads as AI template filler and clutters the hierarchy | Let the heading carry the meaning; put context in body copy |
| Purple-blue gradients, glowing orbs, glassmorphism with no environment behind it | The default "AI startup" look | Glass only over a real painted/photographic environment; palette from the brand |
| Emoji as icons or bullets | Cheapens the voice | Custom glyphs or nothing |
| Mock UIs drawn as grey boxes | Feels fake and generic | Render the product's real components with sample data, animated and interactive |
| Fake social proof | Damages trust, can be screenshotted | Omit, or show honest proof (live tool results, real numbers) |
| Animating everything on load | Noise; slows perception | Motion with purpose: reveal, explain, reward |
| Default fonts and default colours | Unauthored | Chosen pairing, derived palette |
| Generic stock photos | Interchangeable | Custom procedural art, or precise generation prompts |
