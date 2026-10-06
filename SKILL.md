---
name: ishaan-ui
description: Ishaan UI — a complete design brain for building or rebuilding websites that feel hand-crafted, premium and alive, never generic or "AI-made". Use it whenever someone wants a new website, landing page, dashboard, web app UI, auth flow or design system built from scratch, OR wants an existing site redesigned, reskinned, polished, "made premium", modernised or rebuilt in the style of a reference site. Also use it for adding loaders, page transitions, scroll-triggered sections, glass/soft-blur UI, micro-interactions, custom icons or custom illustrated assets to a site. Trigger even if the user only says "make this look better", "redo my landing page", "make it feel like [some site]", or "build me a website for my brand".
---

# Ishaan UI

A way of thinking about websites, not a component kit. It produces sites that look art-directed: one clear visual idea, a restrained palette, real typography, motion with a purpose, custom icons and custom art, and the product's real UI instead of mockups. Everything is built by hand for the brand in front of you.

The skill has a short **intake**, then one of two **paths**, then a shared **craft system** and a **ship checklist**.

```
Intake (ask first) ─┬─> Path A: Create from scratch   ─┐
                    └─> Path B: Recreate an existing site ┴─> Craft system ─> Ship checklist
```

## 1. Intake: always start by asking

Before writing any code, open with one short message offering to brainstorm, then ask what you need. Use the questions in `references/intake.md`. Keep it to one round of questions where possible; group them, offer sensible defaults, and let the person answer only what they care about. Whatever they skip, decide yourself and say what you chose.

What you must leave intake with:
- **Path**: A (new site) or B (recreate an existing site), plus any reference sites they love.
- **Brand**: name, what it does, who it is for, the one promise it makes.
- **Palette**: their colours if they have them; otherwise derive one (see `references/taste.md` → Colour).
- **Type**: their fonts if they have them; otherwise propose a pairing.
- **Pages / scope** and the **stack** (framework, styling, animation library), defaulting to what the repo already uses.
- **Honesty constraints**: what claims, numbers, logos or testimonials are real. Never invent social proof.

If a reference site is given, study it before designing: scroll it end to end, note layout rhythm, type, colour values, every effect and when it fires. `references/recreate.md` has the exact study procedure.

## 2. Paths

- **Path A, create from scratch** → follow `references/from-scratch.md`.
- **Path B, recreate an existing site into a polished one** → follow `references/recreate.md`. This includes faithful "95% inspired by <reference>" rebuilds and upgrading a client's dated site while keeping their content and brand.

Both paths end in the same craft system.

## 3. The craft system (read the parts you need)

| Read | When |
|---|---|
| `references/taste.md` | Always. The principles, the colour/type/layout rules, and the **anti-slop list**. |
| `references/motion.md` | Any animation: intro loader, page transitions, reveals, soft blur, scroll-driven sections, micro-interactions, loading states. Includes the performance and stacking pitfalls. |
| `references/components.md` | Building UI: glass surfaces, buttons, inputs, dials, nav, dock, cards, empty states, real-UI demos. |
| `references/assets.md` | Icons, illustrations, painted backgrounds, emblems, textures. How to make every asset custom. |
| `references/checklist.md` | Before showing work and before shipping. |

Scripts and assets:
- `scripts/render-art.mjs`: procedural painted art (skies, foliage, landscapes) rendered to static WebP with sharp. Edit palette and seeds per brand.
- `assets/glass.css`: glass, glass-strong, glass-inset, skeleton and keyframe utilities to adapt.
- `assets/icon-template.tsx`: the custom icon base and drawing rules.

## 4. Non-negotiables (the short version of the anti-slop list)

These come from real feedback; the reasons are in `references/taste.md`.

1. **No icon libraries, no prebuilt component kits.** Every icon is drawn as custom SVG in one consistent hand. Every component is written for this brand. If a library is already installed, you may keep its *logic* (e.g. charts) but restyle all visuals.
2. **No small tags above titles.** No eyebrows, kickers, "HOW IT WORKS", "Built for:" badges or mono labels sitting above a heading. Put the meaning in the heading itself.
3. **No AI slop.** No gradient-purple defaults, no stock "glowing orb", no emoji bullets, no fake logos, fake testimonials or invented metrics, no lorem, no "Unlock the power of…" copy.
4. **No generic colours.** Derive a palette from the brand; one accent, used with intent. Never ship framework default colours.
5. **Real UI over mocks.** Show the product's actual components with sample data (clearly fictional, e.g. `.example` domains), animated and lightly interactive.
6. **Never the first idea.** Sketch three or four directions in your head, discard the obvious one, and build the strongest. Say in one line which idea you chose and why.
7. **Custom assets.** If a section needs art, make it (procedural SVG rendered to images, hand-drawn SVG, CSS) or write exact generation prompts and leave drop-in file slots.

## 5. How to work

- Build in vertical slices: tokens → layout shell → one section done properly → the rest. Show progress early.
- Verify visually. Render pages (dev server, headless browser screenshots at desktop and ~375px), look at them, fix what is off. Check for horizontal overflow, overlap, contrast, console and hydration errors.
- Keep functionality real: forms submit, links go somewhere, states (loading, empty, error, success) all exist.
- Respect `prefers-reduced-motion` everywhere; motion is a layer, not a dependency.
- End with the checklist, then a short, plain summary of what was built, what was verified, and what still needs the human.

## Updating this skill

This folder is the whole skill. Edit `SKILL.md` for the workflow, the `references/` files for craft knowledge, and `scripts/` / `assets/` for reusable tools. Bump `VERSION` and note changes in `CHANGELOG.md`. See `README.md` for packaging and distribution.
