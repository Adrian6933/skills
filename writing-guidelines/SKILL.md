---
name: writing-guidelines
description: >-
  Review docs/prose/blog articles for Writing Guidelines compliance. Use when
  asked to "review my article/docs", "check writing style", "audit prose",
  "improve the writing", "review voice and tone", or "check this against the
  writing handbook". Great for polishing Zyrolin blog posts before publishing.
---

# Writing Guidelines (prose review)

Review written content (blog articles, docs, marketing copy) against Vercel's
Writing Guidelines — a handbook for clear, concise, well-structured prose.
Recreated locally from `vercel-labs/agent-skills`.

## Workflow

1. **Fetch the latest guidelines** before each review (they evolve), with
   WebFetch on:
   ```
   https://raw.githubusercontent.com/vercel-labs/writing-guidelines/main/command.md
   ```
   That document contains the full rule set and the expected output format. If
   the fetch fails (no network), apply the fallback principles below.

2. **Determine the text to review.** Use the file(s) the user named, or ask. For
   Zyrolin, articles live in `zyrolin/src/content/articles/<lang>/<category>/`.

3. **Check the prose against every rule** and **report findings** concisely as
   `file:line — issue → suggested fix`, grouped by severity. Then offer to apply.

## Fallback principles (if the guidelines can't be fetched)

- **Lead with the point.** No "In today's world…" warm-ups. First sentence
  states what the reader gets.
- **Be concise.** Cut filler ("very", "really", "in order to" → "to"). Short
  sentences. One idea per sentence.
- **Active voice and second person.** "You set the budget", not "the budget is
  set". Speak to the reader.
- **Concrete over vague.** Specific steps, numbers, examples — not adjectives.
- **Consistent terminology.** Don't switch synonyms for the same concept.
- **Scannable structure.** Descriptive H2/H3, short paragraphs, lists and tables
  where they help, a clear conclusion.
- **Typography.** Real ellipsis `…`, curly quotes, en dashes for ranges
  (10–20), non-breaking spaces in measurements.
- **Honest tone.** No hype, no exclamation overload, no unverifiable claims.
  Add disclaimers for finance/health.
- **Accessibility of language.** Plain words over jargon; define terms on first
  use; write for a beginner.

## Installing the upstream version

On a machine with shell internet access:
```
npx skills add vercel-labs/agent-skills --skill writing-guidelines
```
