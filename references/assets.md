# Assets: everything custom

## 1. Icons (custom SVG, one hand)
Draw a set specific to the site; never import an icon library.
- Grid 24×24, stroke 1.4px, round caps and joins, `currentColor`.
- Give each a little **character**: a circle left open at one o'clock, a softly curved arrow shaft, a bin whose lid can lift, a handle ending in a spark. Slight imperfection reads as hand-drawn.
- **Duotone option** for primary nav: an accent "wash" shape slightly off-register behind the line, shown when active.
- Per-feature **glyphs** (one per tool/feature) in the same language, used on cards, inputs, menus and medallions.
- Keep them in one file; name by meaning (`IconLoupe`, `IcDossier`), not by shape.
- Template: `assets/icon-template.tsx`.

## 2. Logo mark + wordmark
A mark that expresses the visual idea (a loupe for clarity, a compass for direction, a seal for trust) drawn as engraver's lines; the wordmark in the display face (often italic). Also make a favicon version (filled background, bolder strokes).

## 3. Environment art (procedural, pre-rendered)
`scripts/render-art.mjs` builds painterly art from SVG primitives pushed through fractal-noise displacement, then rasterises to WebP with sharp:
- **Skies**: gradient + soft cloud banks (displaced, blurred ellipses) + paper grain + horizontal stroke texture. Vary seeds and warmth per section.
- **Foliage**: a branch with leaf clusters (seeded ellipses in 5–6 tones + highlights), transparent background; flip for the other side.
- **Landscape**: layered hills, misty tree line, a path; crop edges after displacement.
Adapt palettes to the brand (cool blue-greys + accent glow, or dusk roses, or night indigos). Run `node scripts/render-art.mjs`, inspect every output image, iterate. Keep images small (skies ~10KB, foliage ~200KB).

Why pre-render: live SVG filters stall the page and cause hydration mismatches; static images are fast and swappable.

## 4. Generated imagery (when the user can run an image model)
Write precise prompts with a shared style line, exact sizes and file names, so real paintings can replace procedural art 1:1. Example style line: "gouache / oil-pastel impressionist illustration, visible brush strokes, palette of <brand colours>, calm, editorial, no people, no text." Leave the procedural version in place until replaced.

## 5. Small illustrations and objects
Inline SVG drawn by hand: emblems (ring of hairline rays + a central object), empty-state scenes, error clouds, stamps, postmarks (text on a circular path + wavy cancellation lines). Use the palette, 1.2–1.6px lines, one accent fill.

## 6. Textures
- Paper grain: an SVG fractal-noise data URI at 6–9% opacity, overlay blend.
- Halftone dots: `radial-gradient` dots masked to a couple of soft regions over skies.
- Light streaks on glass: a blurred white bar rotated ~12°.

## 7. Never
Stock photos, icon packs, AI-looking orbs, clip-art, copied images from a reference site.
