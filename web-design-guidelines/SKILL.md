---
name: web-design-guidelines
description: >-
  Review UI code for Web Interface Guidelines compliance. Use when asked to
  "review my UI", "check accessibility", "audit design", "review UX", "make the
  site more attractive/professional", or "check my site against best practices".
  Fetches Vercel's Web Interface Guidelines and reviews the given files against
  them, reporting concrete findings in file:line format.
---

# Web Design Guidelines (UI review)

Audit web UI against the **Web Interface Guidelines** — a comprehensive,
community-standard checklist for interaction, layout, accessibility, typography,
forms, performance and polish. Recreated locally from Vercel's
`vercel-labs/agent-skills` (which installs via `npx skills add` when the shell
has internet).

## Workflow

1. **Fetch the latest guidelines** before each review (they evolve), using
   WebFetch on:
   ```
   https://raw.githubusercontent.com/vercel-labs/web-interface-guidelines/main/command.md
   ```
   That document contains the full rule set and the expected output format.
   If the fetch fails (no network), fall back to the principles in the sibling
   `elegant-web-ui` skill.

2. **Determine the files to review.** If the user named files or a pattern, use
   them. Otherwise ask which files/components to review (e.g. a page, a header,
   a form), or default to the most prominent UI (home, header, article page).

3. **Check the code against every applicable rule** in the fetched guidelines —
   interaction states, keyboard/focus, semantics/ARIA, contrast, hit targets,
   layout/overflow, motion/`prefers-reduced-motion`, font/CLS, forms, etc.

4. **Report findings** concisely in `file:line — issue (rule)` format, grouped
   by severity (blocking / important / polish). Then offer to apply the fixes.

## Notes

- Prefer fixing real, verifiable issues over subjective taste; pair this with
  `elegant-web-ui` for the "make it prettier" / design-system side.
- After applying fixes, verify in a browser preview (screenshot + interaction),
  not just a build.

## Installing the upstream version

On a machine with shell internet access, install the original instead of this
local copy with:

```
npx skills add vercel-labs/agent-skills --skill web-design-guidelines
```

Browse more skills at https://skills.sh (top sources: `vercel-labs/agent-skills`,
`anthropics/skills`).
