---
name: frontend-design
description: >-
  Guidance for distinctive, intentional visual design when building new UI or
  reshaping an existing one. Use for aesthetic direction, typography pairing,
  layout, and making choices that don't read as templated/AI-generated defaults.
  Use when asked to design a page, pick a visual direction, make a site feel
  unique/premium, or critique a design for genericness.
---

# Frontend Design

Make interfaces that feel intentional and distinctive — not templated.
Recreated locally from Anthropic's `anthropics/skills` (`frontend-design`).
Pair with `elegant-web-ui` (design system) and `web-design-guidelines` (audit).

## Process: two passes

1. **Brainstorm a compact token system first** — name the subject, its audience,
   and the page's single job. Choose colors, type, spacing, and one signature
   move before writing code.
2. **Critique against generic defaults** — ask "would this look the same on any
   other project?" If yes, push it further. Then build.

## Principles

- **Ground in the subject.** If the brief doesn't pin down what the product/
  subject is, pin it yourself: one concrete subject, its audience, the page's
  single job. Design flows from that, not from a generic template.
- **Hero as thesis.** Open with the most characteristic element from the
  subject's world. Avoid the templated "big number + gradient" hero unless it's
  truly justified by the content.
- **Typography as personality.** Pair display and body faces deliberately — not
  the same families you'd reach for on any other project. Type sets the tone
  more than any other single choice.
- **Structure encodes meaning.** Structural devices (numbered markers, timelines,
  grids) should encode something true about the content, not decorate it.
  Numbered steps only when order actually matters.
- **Intentional motion.** Animation should serve this subject specifically.
  Often less is more — extra animation makes a design feel AI-generated.
- **Match execution to vision.** Maximalist designs require elaborate, detailed
  work; minimal designs demand precision in spacing and alignment. Don't do
  "minimal" as an excuse for sparse.
- **Writing is design material.** Copy exists to aid understanding. Active voice,
  specific language, consistent vocabulary across the whole interface.
- **Restraint — spend boldness in one place.** Pick one element to be bold
  (a hero, a signature color, a type treatment); keep everything around it quiet
  and disciplined. Cut any decoration that doesn't serve the brief.

## Anti-patterns (reads as "templated / AI-made")

- Generic hero: huge gradient headline + three feature cards + CTA, with no tie
  to the actual subject.
- Default font stacks with no deliberate pairing.
- Decoration that doesn't mean anything (random blobs, numbered lists where
  order is irrelevant, motion for motion's sake).
- Five accent colors; everything equally loud (nothing stands out).
- Emojis used as UI iconography.

## Checklist

- [ ] Named the subject, audience, and the page's single job.
- [ ] One signature move; everything else quiet.
- [ ] Deliberate display/body type pairing.
- [ ] Structural devices reflect real content meaning.
- [ ] Motion is minimal and purposeful (respects reduced-motion).
- [ ] Copy is specific, active, and consistent.
- [ ] Asked "would this look the same on any other site?" — and fixed it if yes.

## Installing the upstream version

On a machine with shell internet access:
```
npx skills add anthropics/skills --skill frontend-design
```
