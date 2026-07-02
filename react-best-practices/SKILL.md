---
name: react-best-practices
description: >-
  Apply React best practices when writing or reviewing React components (.tsx).
  Use when creating React islands/components, fixing re-renders, hooks, state,
  effects, performance, or accessibility in React code. For the Zyrolin project
  this applies to the interactive islands (SearchModal, NewsletterForm).
---

# React Best Practices

Guidelines for correct, performant, accessible React. Recreated locally from
`vercel-labs/agent-skills` (its upstream version is Next.js/RSC-focused; this is
the framework-agnostic core that also fits Astro React islands).

## Components & state

- Keep components small and focused; lift state only as high as needed.
- Derive state instead of duplicating it; compute during render or with
  `useMemo` rather than syncing via `useEffect`.
- Keys must be stable and unique (never the array index for dynamic lists).
- Prefer controlled inputs; keep a single source of truth.

## Effects

- `useEffect` is for synchronizing with external systems (events, subscriptions,
  DOM, network) — not for transforming props/state into other state.
- Always clean up listeners/timers in the effect's return.
- List exact dependencies; don't disable the lint rule to "make it work".

## Performance

- Don't optimize prematurely. Reach for `useMemo`/`useCallback`/`memo` only when
  there's a real cost (large lists, expensive compute, referential stability for
  memoized children).
- Avoid creating new objects/functions in render that feed memoized children.
- Virtualize lists over ~50 items.
- Lazy-hydrate islands: in Astro prefer `client:visible`/`client:idle` over
  `client:load` unless the component must be interactive immediately.

## Accessibility

- Use semantic elements: `<button>` for actions, `<a>` for navigation.
- Icon-only controls need `aria-label`; decorative icons `aria-hidden`.
- Keep visible focus states; never `outline-none` without a replacement.
- Inputs need labels (or `aria-label`), correct `type`, `autocomplete`, and
  `inputmode`; don't block paste.
- Announce async results with `aria-live` where relevant.

## Forms

- Validate on submit; show inline errors and focus the first error.
- Keep the submit button enabled until the request actually starts.
- End loading labels with an ellipsis ("Saving…").

## Installing the upstream version

On a machine with shell internet access:
```
npx skills add vercel-labs/agent-skills --skill react-best-practices
```
Browse more at https://skills.sh.
