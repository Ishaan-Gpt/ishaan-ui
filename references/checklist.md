# Ship checklist

Run through this before showing work and again before deploying. Fix, don't just note.

## Taste
- [ ] One clear visual idea; you can name it in a sentence.
- [ ] Palette is derived (no framework defaults); one accent used with intent; small accent text passes contrast.
- [ ] Two typefaces; headings have an italic turn; no tag/label above any heading.
- [ ] No icon library imports anywhere (search the code for them); all icons custom.
- [ ] No prebuilt-looking components; no emoji icons; no purple-gradient/orb clichés.
- [ ] No invented testimonials, logos or numbers; sample data clearly fictional.
- [ ] Mocks replaced by real components with sample data.

## Motion
- [ ] Intro plays once per session, hidden before first paint otherwise, skipped for reduced motion.
- [ ] Page transitions never delay navigation; prefetch on hover/touch/focus; slow loads show the looping loader.
- [ ] Reveals are subtle and once; scroll sections work on desktop and degrade gracefully on mobile.
- [ ] `prefers-reduced-motion` honoured everywhere.
- [ ] No animated `filter`/`opacity`/`mask` on ancestors of glass; glass actually blurs.

## Function
- [ ] Every link goes somewhere; every form submits and shows loading, success and error.
- [ ] From every page there's a visible way home, to the app, and to sign out.
- [ ] Sign-out clears the session cookie with the same path/attributes it was set with, and revokes server-side if possible; then a full reload.
- [ ] Signed-in users skip login/signup.
- [ ] Route loading skeletons exist for data-heavy pages; empty and error states exist.

## Quality
- [ ] Typecheck and lint clean; production build passes.
- [ ] No console errors and no hydration warnings (round SVG floats; time/locale after mount).
- [ ] Screenshots at ~1440px and ~375px reviewed; no horizontal overflow; decorative art never covers UI.
- [ ] Images pre-rendered and small; no live SVG filters on large areas.
- [ ] Metadata, Open Graph, favicon, sitemap and robots updated to the brand.
- [ ] Old URLs redirected if routes moved.

## Hand-off
- [ ] Plain summary: what was built, what was verified (and how), what still needs the human (credentials, real content, real art).
