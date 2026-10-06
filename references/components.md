# Components: build them for the brand

Write every component yourself. These are proven patterns; adapt their shape to the visual idea.

## Surfaces
- **glass**: translucent warm-white gradient, `backdrop-filter: blur(28px) saturate(1.4)`, 1px white/70 border, inset top highlight, long soft shadow. Only over an environment (art, blurred sky), never over flat colour.
- **glass-strong**: more opaque, for dense content and popovers.
- **glass-inset**: white/40 with inner shadow, for inputs, chips, icon wells.
- Radii: 12px controls, 18–24px cards, 28–32px panels.
- Provide `prefers-reduced-transparency` and print fallbacks (solid surface).

## Buttons
- Primary: accent fill, ink text, inset top highlight, small accent-tinted shadow, 1px press. Secondary: glass-inset or a warm neutral fill. Rectangular with soft corners (10–14px) reads more premium than full pills for most brands.
- Every async button: spinner + present-tense verb, disabled while busy.

## Inputs
- glass-inset, 48px tall, 12px radius, accent focus ring (`0 0 0 4px accent/30%`).
- Big "front door" input for the product's core action: a glass bar with the tool's own glyph in a well, a primary action, and quiet example chips ("try …") under it.

## Navigation
- **Marketing nav**: transparent → floating glass pill on scroll (animate max-width); hover mega-menu in the display face; signed-in visitors get "Your studio" + an avatar menu (Overview, Saved items, Sign out).
- **App dock**: vertical glass dock fixed left, centered; logo (with "Back to home" name-tag), primary destinations, divider, tools popover, avatar menu (Home, All tools, Sign out). Bottom dock on mobile. A `layoutId` bead marks the active item.
- There is always a visible way home and a way to sign out from every page.

## Headings
- Masthead: big display heading with an italic turn and a one-line lede. **Nothing above it.**
- Section headings: two lines, second italic; optionally scroll-filled.

## Data visuals (custom, never default chart skins)
- **Bezel dial**: 60 hairline ticks around a ring, score arc in a status tone, numeral in the display face, sweeping + counting on change.
- **Ink-well gauge**: glass test-tube filling with accent liquid, looping wave surface, bubbles, faster slosh on hover. Great for quotas/usage.
- **Glass lanes**: horizontal glass tubes for comparisons.
- **Seals/stamps** as status markers (filled seal = good, hollow ring = pending, dashed = never).
- If a chart library is used, restyle everything: palette, gridlines at low alpha, glass tooltip, gradient area fill.

## Lists and rows
- Glass list with white/60 dividers; row hover lightens; leading glyph well; serif title + muted subtitle; trailing dials, relative date (computed after mount), open arrow, and a lid-lifting delete.
- Filters as a glass segmented control with a sliding bead.

## Objects from the metaphor (use one or two per site)
- Postcard (auth): picture side with "Greetings from *Brand*", message side with perforated stamp (CSS radial mask), circular postmark with text on a path, faint address rules, pointer tilt.
- Ticket (billing/plan): glass ticket with notches (radial mask at the tear line), dashed perforation, a stub that tilts on hover, a vertical serial number.
- Arched window: rounded-top panel with mullions and a light streak, art inside, text over a bottom gradient.
- Emblem: engraved line-art badge with radial hairlines.

## Empty, loading, error states
- Empty: a small custom illustration (e.g. a floating sheet over an open folder), a two-line serif heading with an italic word, one action.
- Loading: skeleton in the page's shape + brand-object loader line (`motion.md`).
- Error: friendly, specific, with retry ("A passing *cloud*").

## Real UI in marketing
- Export presentational pieces from real features (verdict, list, dial, group) and give them `demo` props (no saving, links to public pages).
- Feed them sample data from one `samples` module using obviously fictional `.example` names; compute any derived data with the product's real logic.
- Make them breathe: auto-cycle states while in view, let clicks take over, animate value changes.
