# Ishaan UI

A design brain for Claude that builds or rebuilds websites to a hand-crafted, premium standard: one clear visual idea, a derived palette, real typography, purposeful motion (intro loader, page transitions, soft-blur reveals, scroll-driven sections, micro-interactions), custom icons and custom art, and real product UI instead of mockups. No icon libraries, no prebuilt component kits, no labels above headings, no AI slop.

Author: Ishaan · Version: see `VERSION`

## What it does
1. **Asks first**: offers to brainstorm, then gathers brand, palette, fonts, references, scope and what's true.
2. **Picks a path**: create a site from scratch, or recreate an existing site (upgrade, or rebuild inspired by a reference).
3. **Applies the craft system**: taste rules, motion system, component patterns, custom asset pipeline.
4. **Verifies and ships** with a checklist.

## Contents
```
ishaan-ui/
├── SKILL.md                 workflow, paths, non-negotiables
├── references/
│   ├── intake.md            the opening questions and direction brief
│   ├── taste.md             principles, colour, type, layout, copy, anti-slop list
│   ├── from-scratch.md      Path A
│   ├── recreate.md          Path B (audit, reference study, rebuild strategy)
│   ├── motion.md            loaders, transitions, reveals, scroll sections, pitfalls
│   ├── components.md        glass surfaces, nav, dock, dials, gauges, objects, states
│   ├── assets.md            custom icons, marks, procedural art, prompts, textures
│   └── checklist.md         ship checklist
├── scripts/render-art.mjs   procedural painted art → WebP (needs `sharp`)
├── assets/glass.css         surface + motion utilities
├── assets/icon-template.tsx custom icon base
├── VERSION · CHANGELOG.md · LICENSE.md
```

## Use it
- Claude Code: it lives in `~/.claude/skills/ishaan-ui/`. Invoke with `/ishaan-ui`, or just ask for a website and it triggers.
- Claude.ai / other environments: upload the packaged `ishaan-ui.skill` (or this folder zipped) as a custom skill.

## Update / upgrade it
Edit the markdown files directly; they are the skill. Keep `SKILL.md` short (it loads on every use) and put depth in `references/`. Bump `VERSION`, add a line to `CHANGELOG.md`, then re-package.

## Package it
With Anthropic's skill-creator scripts:
```
python -m scripts.package_skill ~/.claude/skills/ishaan-ui
```
or zip the folder (the zip must contain the `ishaan-ui/` folder with `SKILL.md` at its top).

## Sell / distribute it
Package as above and list it on any marketplace that accepts Claude/Agent Skills, or sell the zip directly. Set your terms in `LICENSE.md`.
