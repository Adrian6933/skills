---
name: zyrolin-article
description: >-
  Create a new tutorial/guide article for the Zyrolin blog (the Astro site in
  zyrolin/). Use this whenever the user wants to write, add, draft, or translate
  a Zyrolin article, a "how-to" post, or content for a category like ai, tech,
  money, recipes, gaming, etc. Produces a ready-to-publish Markdown file with the
  correct frontmatter, structure (intro, steps, table, FAQ, conclusion), tone,
  and file location — and updates nothing else (routing/search/sitemap are
  automatic).
---

# Zyrolin Article Generator

Generate publish-ready articles for the Zyrolin tutorial blog. The site lives in
`zyrolin/` and uses Astro Content Collections — dropping a correctly-formatted
Markdown file in the right folder is all that's needed. The homepage, category
pages, search index, related-articles and sitemap update automatically.

## Where the file goes

```
zyrolin/src/content/articles/<lang>/<category>/<slug>.md
```

- `<lang>`: `en` (base), `es`, `de`, or `fr`.
- `<category>`: one of the slugs in `zyrolin/src/data/categories.ts`:
  ai, tech, money, recipes, home, pets, mobile, gaming, hardware, save-energy,
  software-config, internet, health, productivity, travel, design.
- `<slug>`: kebab-case, English, descriptive (e.g. `how-to-clean-your-pc`).
  **Keep the same slug across languages** so translations link together.

## Required frontmatter

```markdown
---
title: "How to Do X (Clear, Benefit-Driven Title)"
description: "One sentence, ~150 chars, with the keyword. Used for SEO + cards."
category: "tech"            # must match a category slug
type: "tutorial"            # tutorial | guide | list | comparison | fix
pubDate: 2026-06-24         # YYYY-MM-DD
author: "Zyrolin Team"      # "Equipo Zyrolin" (es), "Zyrolin-Team" (de), "Équipe Zyrolin" (fr)
featured: false             # true = appears in homepage "Trending"
tags: ["keyword", "topic"]
---
```

Optional: `updatedDate`, `cover` (path to a real image), `coverAlt`, `readingTime`.

### Optional visual blocks (attention-grabbing — use them when they fit)

These render automatically in the article template, so prefer them over plain
text when an article has numbers or key points:

```yaml
keyTakeaways:                 # a "Key takeaways" / TL;DR box near the top
  - "First key point in one sentence."
  - "Second key point."
stats:                        # a row of big highlighted numbers
  - { value: "50%", label: "Needs" }
  - { value: "20%", label: "Savings" }
chart:                        # a simple horizontal bar chart
  title: "The 50/30/20 split"
  unit: "%"                   # optional suffix shown after each value
  data:
    - { label: "Needs", value: 50 }
    - { label: "Wants", value: 30 }
    - { label: "Savings", value: 20 }
```

Guidance: add `keyTakeaways` (2–4 items) to most how-to articles; add `stats`
when there are punchy numbers; add a `chart` when comparing a few quantities.
Keep them honest and consistent with the article body. Translations should
include translated versions of these fields too.

## Article structure (this is what makes it rank and read well)

1. **Intro** (2–3 sentences): hook + what the reader will achieve. No "In today's
   world…" filler.
2. **`## H2` sections**: these auto-populate the table of contents, so write clear,
   descriptive H2s. For tutorials use `## Step 1: …`, `## Step 2: …`.
3. **At least one Markdown table** where it adds clarity (comparison, ratios,
   settings). Tables look great in the design and help skim-readers.
4. **One short `> blockquote` tip or warning** where useful.
5. **`## FAQ`** near the end with 2–3 real questions as `**bold**` lines followed by
   a one-paragraph answer. (Good for Google "People also ask".)
6. **`## Conclusion`**: 2–3 sentences summarizing the key actions.

## Tone

Friendly, direct, practical. Write for a beginner. Short paragraphs. Explain the
"why", not just the "what". Avoid hype and obvious AI filler. Match the language's
natural voice when translating (don't translate literally).

## Sensitive niches

For `money` and `health`, include a brief disclaimer blockquote near the top:
"This is general information, not financial/medical advice."

## Workflow

1. Confirm category, language, and the keyword/topic.
2. Pick a kebab-case slug (reuse the English slug for translations).
3. Write the Markdown file at the path above.
4. Tell the user the file path. Optionally run `npm run build` in `zyrolin/` to
   verify (the schema validates frontmatter).
5. For translations, set the localized `title`/`description`/`author`, keep the
   same `category`, `slug`, and `pubDate`, and place under the right `<lang>` folder.

## Quick example

`zyrolin/src/content/articles/en/tech/how-to-free-up-disk-space.md` →

```markdown
---
title: "How to Free Up Disk Space on Windows"
description: "Out of storage? Reclaim gigabytes with these safe, built-in Windows tools — no risky cleaners needed."
category: "tech"
type: "tutorial"
pubDate: 2026-06-24
author: "Zyrolin Team"
tags: ["windows", "storage", "cleanup"]
---

Running out of space slows everything down. Here's how to safely reclaim gigabytes…

## Step 1: Run Storage Sense
…

## FAQ
**Will this delete my files?**
No — these tools only remove temporary and system junk.

## Conclusion
…
```
