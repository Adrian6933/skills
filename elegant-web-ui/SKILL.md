---
name: elegant-web-ui
description: >-
  Design and build beautiful, modern, premium-looking web interfaces. Use this
  whenever the user wants a website, landing page, blog, dashboard or component
  to look "nicer", "more elegant", "more professional", "less AI-made", or asks
  to improve/redesign a UI, pick fonts/colors, or polish layout, spacing and
  micro-interactions. Provides an opinionated design system, component patterns,
  and a quality checklist for tasteful, high-end results (works great with
  Astro/React/Tailwind, but the principles are framework-agnostic).
---

# Elegant Web UI

A practical design system for building web interfaces that look premium and
intentional — not generic or "AI-made". Apply these defaults unless the user
specifies otherwise, then adapt to their brand.

## Core principles

1. **Restraint beats decoration.** Few colors, generous whitespace, one strong
   accent. Clutter reads as amateur.
2. **Hierarchy through size and weight**, not boxes everywhere. Let typography
   and spacing do the work; use borders sparingly and keep them faint.
3. **Consistency is elegance.** One spacing scale, one radius, one accent. Reuse
   tokens; never hardcode random values.
4. **Depth, softly.** Subtle gradients, soft shadows, gentle glows — never harsh
   drop shadows or heavy bevels.
5. **Motion with purpose.** Small, fast transitions (150–250ms) on hover/focus.
   Respect `prefers-reduced-motion`.

## Color & theming

- Build with **semantic tokens** (CSS variables), not raw color utilities:
  `--bg`, `--surface`, `--surface-2`, `--line`, `--fg`, `--fg-muted`, `--brand`,
  `--brand-2`, plus one tasteful accent (e.g. a muted gold) for premium feel.
- **Dark-first is modern and flattering.** Use a deep near-black base (e.g.
  `#08090d`), not pure black. Surfaces a few shades lighter. Provide a light
  theme by flipping the same tokens via `[data-theme]`; add a toggle persisted
  in `localStorage` with an inline no-flash script in `<head>`.
- Add a faint **ambient glow** behind the hero (a large radial gradient in the
  brand color at low opacity) for atmosphere.
- Use `color-mix(in oklab, …)` for tints/borders so they adapt to the theme.

## Typography

- Pair a **display font** for headings with a clean **sans** for body. Safe,
  premium pairings: *Plus Jakarta Sans* / *Inter*; *Sora* / *Inter*;
  *Fraunces* (serif, editorial) / *Inter*. Avoid using a quirky font for body.
- Headings: bold, tight tracking (`-0.02em`), large and confident.
- Body: ~16–17px, line-height ~1.7–1.8, muted color (not pure white/black).
- Use a real type scale; don't eyeball font sizes per element.

## Layout & spacing

- Constrain content width (`max-w-3xl` for reading, `max-w-6xl` for grids) and
  center it. Pad sections generously (`py-14`+ on desktop).
- Use a consistent radius (e.g. `0.875–1rem` for cards, full for pills/buttons).
- Mobile-first: 70%+ of traffic is mobile. Verify at 375px.

## Iconography & imagery

- **Use SVG line icons, never emojis, in UI chrome.** Emojis instantly look
  AI-made and render inconsistently. A small, consistent line-icon set
  (Lucide-style, ~1.75 stroke) looks professional.
- Avoid generic stock photos. If you lack real imagery, generate **on-brand
  illustrated covers** (gradient panel tinted with the section accent + a large
  icon + a label) — consistent, crisp, and clearly communicates the topic.

### Real photos when the build shell has no network

Static-build sandboxes often can't download files, but the **browser rendering
the site does have network** (it loads web fonts), so real photos referenced by
URL still work in preview and production. To source license-clean, thematic
photos without an image-gen tool:

1. Use **WebFetch** on `https://unsplash.com/s/photos/<keyword>` and ask it to
   return the first image URLs that begin with
   `https://images.unsplash.com/photo-1` (the CDN URLs). Grab the id (the part
   after `photo-`, before `?`).
2. Build optimized URLs:
   `https://images.unsplash.com/photo-<id>?auto=format&fit=crop&w=<width>&q=70`.
3. Store ids in a small map (e.g. per category) and pick deterministically by a
   slug hash so items don't repeat.
4. **Always layer a generated illustration behind the `<img>`** and add
   `onerror="this.remove()"` so a failed photo gracefully reveals the fallback.
5. Unsplash License = free, commercial OK, no attribution required. Note to the
   user that for production they may prefer their own/curated licensed images.

## Component patterns that look high-end

- **Header:** sticky, translucent with `backdrop-blur`, faint bottom border. A
  refined logo (gradient emblem + wordmark + tiny accent dot). Compact icon
  buttons in pill shapes.
- **Search:** a **command palette** (centered modal over a blurred backdrop)
  opened from a header button and `Cmd/Ctrl+K` and `/`. Far more elegant and
  useful than an inline box. Make matching forgiving (accent- and
  hyphen-insensitive; every query word must appear).
- **Cards:** surface background, faint border, on hover lift slightly
  (`-translate-y-1`) with a soft brand-tinted shadow and accent border.
- **Buttons:** solid brand for primary (white text), bordered/ghost for
  secondary. Pills for nav/utility, rounded-lg for form actions.
- **CTA sections:** a brand gradient panel with a soft white blur orb in a
  corner.
- **Gradient text** on one hero keyword for a focal point — used once, not
  everywhere.

## What to avoid (the "AI-made" tells)

- Emojis in navigation, buttons, and section titles.
- Pure black/white text, harsh `#ddd` borders, heavy box-shadows.
- Everything in cards/boxes; centered text walls.
- Five accent colors; rainbow gradients.
- Default system font for headings with no hierarchy.

## Quality checklist (run before declaring done)

- [ ] One accent color used consistently; tokens, not hardcoded hex.
- [ ] Display + body font pairing loaded with `display=swap`.
- [ ] Dark and light themes both correct (toggle, no flash).
- [ ] Line icons everywhere (no emojis in chrome).
- [ ] Hover/focus states on all interactive elements; transitions ~200ms.
- [ ] Looks right at 375px (mobile) and on a wide screen.
- [ ] Generous spacing; faint borders; soft shadows only.
- [ ] Verified in a browser preview (screenshot) — not just built.

## Workflow

1. Establish or read the design tokens first; don't scatter literals.
2. Build/adjust components using the patterns above.
3. Run the dev server and **screenshot at desktop and mobile widths**; check a
   dark and a light capture.
4. Iterate against the checklist before finishing.
