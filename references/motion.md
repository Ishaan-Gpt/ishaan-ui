# Motion: loaders, transitions, blur, reveals, scroll, interaction

## Contents
1. Motion personality
2. The intro loader
3. Page transitions
4. Appearing: reveals and soft blur
5. Scroll-triggered and scroll-driven sections
6. Interactive components and micro-interactions
7. Loading states
8. Performance and pitfalls (read this)

---

## 1. Motion personality
Decide it once: e.g. "slow, eased, soft blur; springy only on small things you touch". Defaults:
- Ease: `cubic-bezier(.22,1,.36,1)` for most things; `cubic-bezier(.76,0,.24,1)` for sheets and curtains; springs (stiffness ~500, damping ~30–40) for small UI like a sliding active indicator.
- Durations: micro 150–300ms, reveals 600–900ms, sheets 400–600ms, intro ≤ 3s total.
- Everything respects `prefers-reduced-motion`: render the final state, no transforms.

## 2. The intro loader
Purpose: a branded first impression that **tells the metaphor**, plays once per session, and never blocks a repeat visitor.

Pattern ("the mark opens"):
1. Canvas-coloured overlay. The logo mark draws itself (SVG `pathLength` 0→1), the wordmark fades up from a slight blur.
2. The mark's interior fills with the brand's art (e.g. a sky inside a lens).
3. The overlay is revealed *through* the mark: animate a radial mask hole from 0 to ~160vmax centred on the mark (`mask-image: radial-gradient(circle at X Y, transparent R, #000 R+1px)` with a motion value).
4. Mark `sessionStorage` and unmount.

Rules: decide visibility **before first paint** with a tiny inline script that sets `html[data-intro="done"]` when it has played or reduced motion is on, and hide the overlay with CSS on that attribute (no flash, no hydration mismatch). Lock scroll only while it plays. Hide it in print.

Make it brand-specific: a stamp being pressed, a page being turned, a dial sweeping, ink pouring: whatever the metaphor suggests.

## 3. Page transitions
Purpose: continuity and a sense of place, **without slowing navigation**. Related to the loader in vocabulary, different in shape.

Pattern ("the sheet / the scan"):
- Intercept internal link clicks (capture phase; skip modifier keys, new tabs, downloads, same-path hash links). **Call `router.push` immediately**: the animation dresses the wait, it must never add to it.
- A canvas-coloured sheet rises with a curved leading edge (animate border-radius from a large ellipse to 0), shows the destination name in the display face, while a small brand object (e.g. a loupe) travels a hairline.
- When the pathname changes (the new route rendered), wait only for the sheet to finish rising (~400ms minimum), then lift it away with a curved trailing edge.
- If loading is slow, keep the sheet up and switch the object into a looping "scanning" motion with a quiet "Loading…": the transition becomes the loader.
- Treat "the route changed away from where the click happened" as arrival, so redirects (e.g. to login) also lift the sheet. Add a long fallback timeout.
- **Prefetch** on `pointerenter`, `touchstart` and `focusin` of internal links.
- Skip entirely for reduced motion.

## 4. Appearing: reveals and soft blur
- Section content: fade + 14–24px rise + blur(6px→0) on enter, once, staggered 60–100ms.
- Headlines: masked word rise, or the **scroll-fill**: letters of the italic line ink from a pale tone to full ink as the line scrolls from 90% to 45% of the viewport.
- Panels with art: scale 1.04→1 crossfade when content changes.
- Glass appears with backdrop blur already applied; don't animate `backdrop-filter`.
- Data visuals animate their value: dials sweep (stroke-dashoffset transition), numerals count up, gauges fill.

## 5. Scroll-triggered and scroll-driven sections
Use 2–3 per landing page, each one teaching the product by letting the visitor *do* the core action.
- **Sticky stage**: section height 300–420vh, inner container `sticky top-0 h-[100svh]`; map `scrollYProgress` to a step or a continuous value.
- **Story in steps**: left list of steps (active expands, others dim); right stage changes scene per step.
- **Live re-scoring**: scrolling applies improvements one by one and the real score UI re-computes and animates; clicking takes manual control ("Back to scroll mode" link).
- **Typed file / config playground**: lines appear as you scroll; real logic re-evaluates the result per line; lines are clickable to toggle.
- **Accordion that auto-advances** while in view, pauses on hover, with a hairline progress bar on the active item.
- Mobile: drop stickiness (render the same content in flow) but keep the interactivity.
- Reduced motion: show the final state, keep click interactivity.

## 6. Interactive components and micro-interactions
- Magnetic primary buttons (small spring pull toward the pointer), 1px press on active.
- Cursor-following warm spotlight inside cards (`radial-gradient` at pointer position).
- Icon medallions that tilt (−8deg) and scale on card hover, with a spring curve.
- Shared-layout "bead" behind the active nav/dock item and segmented controls (`layoutId`).
- Tooltips/name-tags that slide out of glass on hover.
- Pointer-driven 3D tilt (±2–3deg) on a hero object such as an auth postcard; mouse only.
- Toggle pills that pop (scale 0.8→1 spring) when their state changes.
- A delete icon whose lid lifts on hover; a compass that rotates when its menu opens. Every icon can have one tiny behaviour.

## 7. Loading states (never a blank screen)
- Route-level skeleton in the **page's own shape** (glass panes, shimmer blocks matching cards and lists) plus a small brand-object loader line ("Opening your studio…").
- In-tool async work: a "working" checklist where steps go up next → in process (spinner) → done (check), paced by a timer while the request runs.
- Buttons show a spinner and a verb ("Signing out…", "Saving…") and disable.
- Optimistic UI where safe; graceful errors with a way to retry.

## 8. Performance and pitfalls (read this)
- **Never animate live SVG filters** (feTurbulence/displacement) on large areas, they stall rendering. Pre-render art to WebP (`scripts/render-art.mjs`).
- **`backdrop-filter` breaks under some ancestors**: an ancestor with `filter`, `opacity < 1`, `mask`, or `backdrop-filter` becomes the "backdrop root", so glass inside blurs nothing. Don't put blur/filter animations on containers of glass; animate opacity/transform only, or animate the glass element itself.
- **Body background paints above negative z-index**: a `fixed -z-10` backdrop disappears behind the body background. Use `z-0` for the backdrop and `relative z-10` for content.
- **Hydration**: values computed differently on server and client (floating-point SVG coordinates, `Date.now()`, locale dates, local hour) cause mismatches. Round coordinates, compute time-dependent text after mount (via `setTimeout(…,0)`, since `requestAnimationFrame` pauses in background tabs).
- **Decorative layers must not cover UI**: put overlapping art behind panels (lower z) and clip/fade it with a mask so it never trails into the next section.
- Sticky scroll sections are measured in vh; tall headless screenshots distort them, so verify those in a normal-height browser.
- Prefer transforms and opacity; avoid animating layout. Respect reduced motion.
