# Voice & Output Format

> Your style and the mechanical rules for the finished article. The agent calibrates *tone* from your real articles (see `work.md`); this file holds the things real articles won't reliably teach it: your language, punctuation, structure, and the fixed bits of your house format.
>
> Copy this file to `profile/voice.md` and edit. Defaults below produce clean plain Markdown; change anything to match where you publish.

## Language
- **Write in:** <e.g. English / 中文 / your language>. The interview is conducted in this language too.
- **Inline terms:** <e.g. "keep technical terms in English inline" — or delete if not applicable>

## Punctuation & symbols
- <e.g. "No em-dashes anywhere; break with commas, periods, colons, or parentheses." Keep or change.>
- <quote style, if you care>

## Structure & mechanics
- **Headings:** `##` for sections, `###` for sub-sections.
- **Paragraphs:** 3 to 5 sentences; don't let them run long.
- **Bold:** sparing, at most one `**bold**` per paragraph.
- **Blockquote:** use `>` to lift out the core claim or a key line.
- **Lists:** for genuinely parallel points only; don't make the whole piece a list.
- **Open** with a concrete scene, number, or sharp question. **Don't** write a "summary/conclusion" wrap-up.

## Don'ts (things voice-matching won't catch on its own)
- No tutorial voice ("let's", "let me show you").
- No filler scaffolding ("firstly... secondly... finally").
- No emoji in body text.
- No invented opinions or experiences (see `references/red-lines.md`).

## Closing section
- Every piece closes with a section carrying your personal judgment, not a generic summary.
- **Heading to use:** <e.g. "My take", or your own phrasing in your language>.

## References / citations format
How shipping citations should appear in the article. Default: a `## References` section with one Markdown link per bullet.

```md
## References

- [Title of source](https://...)
- Author, "Work title" (year)   <!-- for sources with no URL -->
```

## Frontmatter (only if you publish to a static-site generator)
If your blog needs frontmatter, put the exact shape here so drafts are publish-ready. Delete this section for plain Markdown.

```yaml
---
title: "..."
date: "YYYY-MM-DD"
tags: ["..."]
summary: "..."
draft: false
---
```

## Length norms
Reference ranges, not hard limits; density beats word count.
- **Short / reflective:** <range>
- **Standard essay:** <range>
- **Deep / technical:** <range>
