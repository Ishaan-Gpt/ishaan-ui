# Path A: Create a website from scratch

## 1. Direction brief (from intake)
Visual idea, palette, type, motion personality, page list. See `intake.md` → "After answers".

## 2. Foundations first
1. **Tokens** in one CSS file: canvas, surface, surface-2, ink/ink-2/ink-3, line, accent, accent-hover, accent-ink, accent-soft, status, radii, shadows, easing curves (`--ease: cubic-bezier(.22,1,.36,1)`, `--spring: cubic-bezier(.34,1.56,.64,1)`). Map them into the styling system (e.g. Tailwind `@theme`).
2. **Fonts** via the framework loader; expose `--font-display`, `--font-body`, `--font-mono`.
3. **Utilities**: glass / glass-strong / glass-inset, skeleton shimmer, keyframes (`assets/glass.css`).
4. **Brand mark**: a custom logo mark drawn in SVG that expresses the visual idea (e.g. a loupe for a "see clearly" brand) + a wordmark set in the display face.
5. **Icon set**: draw the first 10–15 icons the site needs in one consistent hand (`assets.md`).
6. **Art**: decide the environment (sky, paper, landscape, texture). Render it with `scripts/render-art.mjs` or write prompts, and wire images with slots.

## 3. The landing page skeleton (adapt, don't copy)
A reliable premium sequence; change order and content to fit the brand:
1. **Nav**: transparent full-width bar that becomes a floating glass pill on scroll; centre links; secondary + primary button right; account menu when signed in.
2. **Hero**: big display headline (plain line + italic turn), one-sentence lede, one primary action. Below it a large rounded panel holding the environment art with the **real product UI** floating in glass, lightly interactive. Decorative elements (branches, shapes) tucked behind the panel edges with slow parallax.
3. **How it works**: centered heading whose italic line ink-fills on scroll; a numbered accordion on the left that auto-advances (progress hairline) and a panel on the right that shows the real component for each step.
4. **One or two scroll-driven, interactive sections** that teach the product's core idea by letting the visitor *do* it (see `motion.md` → scroll sections).
5. **Cards over an environment**: three glass cards, each with a small real component inside.
6. **A brand-object moment**: an emblem, a stamp, a ticket, a postcard — an object from the visual metaphor that makes the page memorable.
7. **Pricing** (honest), FAQ if useful.
8. **Closing CTA** over the environment, flowing into a **footer set inside art** (landscape, texture).

## 4. App / dashboard (if in scope)
- Same tokens, a quieter environment: blurred version of the brand art, tinted for time of day.
- Navigation as a floating glass dock (left on desktop, bottom on mobile) with a moving active "bead", hover name-tags, and an account menu that always offers Home, Tools and Sign out.
- Every page: big serif masthead (no crumb label above it), glass panes, custom data visuals (dials, ink-well gauges, glass bars), real empty states, a skeleton loading route in the page's own shape.

## 5. Auth
A memorable object (e.g. a postcard: picture side + message side with stamp and postmark) with a gentle 3D tilt toward the pointer. Inputs are glass-inset; the primary button uses the accent. Already-signed-in visitors skip the form.

## 6. Then: motion, components, assets, checklist
Read `motion.md`, `components.md`, `assets.md`, finish with `checklist.md`.
