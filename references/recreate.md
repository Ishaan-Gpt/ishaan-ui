# Path B: Recreate an existing website into a polished one

Two flavours, often combined:
- **Upgrade**: the client's current site → same content, brand and functionality, rebuilt to a premium standard.
- **Inspired rebuild**: "make mine feel like <reference site>": take ~90–95% of the reference's layout language, effects and rhythm, applied to this brand's content and colours.

## 1. Audit what exists (upgrade)
Read the codebase and the live site before touching anything:
- Routes, components, data flows, forms, auth, payments, APIs: list what **must keep working**.
- Content inventory: every heading, claim, feature, price, testimonial. Mark what's real vs filler.
- What's wrong: generic components, library icons, labels above titles, default colours, fake proof, slow navigation, missing states (loading/empty/error), broken mobile, dead links.
- Brand assets: logo, colours, fonts. Keep the brand recognisable; push it, don't replace it, unless asked.

Write a one-screen audit: keep / fix / remove / add. Share it in a few lines, then build.

## 2. Study the reference (inspired rebuild)
Do this properly; it's where the quality comes from.
1. Open the reference in a browser at desktop width (~1440px). Scroll top to bottom slowly; screenshot each section.
2. Extract computed values with a quick script in the page: background, text and button colours, font families/weights/styles, radii, max widths.
3. For every section note: layout, the heading pattern (e.g. "plain line + italic line"), the asset type (painting, photo, UI), and **every effect and its trigger**: on load, on scroll into view, scroll-scrubbed, sticky, hover, click, auto-cycle, parallax, nav changes on scroll.
4. Note the reload sequence (what animates first, in what order) and the page-change behaviour.
5. Map each reference section to an equivalent for this brand (e.g. their "documents find their file" accordion → your "paste a URL" steps with your real UI).

Then follow the same craft system: their skeleton, your content, your palette (or theirs adjusted toward the brand), your custom assets and icons. Don't copy their images or text; recreate the *feel* with custom work.

## 3. Rebuild strategy
- **Don't break working things.** Keep APIs, data, routes; redirect any URL you move.
- **Re-skin at the token level first**: changing tokens and shared primitives (Card, Button, Input, StatTile) instantly lifts every legacy screen. Then rebuild key screens by hand.
- **Legacy screens you can't rewrite yet**: scope a CSS layer that remaps their old classes to the new language (glass backgrounds, display font, accent-ink text) without touching their markup.
- Replace library icons everywhere with the custom set; remove all labels above headings.
- Replace mockups with the real components on sample data.
- Fix the experience bugs: sign-out that actually clears the session (cookie path!), a visible way back home from every page, an account menu on public pages, fast navigation, loading states.

## 4. Verify like a reviewer
Screenshot every page at desktop and mobile; compare against the reference side by side; list the gaps; fix the biggest three; repeat. Finish with `checklist.md`.
