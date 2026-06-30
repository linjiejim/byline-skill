# Publish Config (optional)

> A plain-language description of where a finished draft should go and in what shape. The agent reads this in Phase 6 and follows it literally.
>
> **If you don't create `profile/publish.md`, byline-skill stops at a finished draft in `drafts/` and you take it from there.** Create it only if you want the agent to write the article into your blog/repo for you.
>
> **Hard limit, regardless of what you write here: the agent writes files only. It never runs git** (no commit, no push). You review and ship yourself. This keeps an article published under your name from going live without your hand on it.

## Example: write into a static-site blog repo

> Delete this and write your own. Plain language is fine; be specific about path and format.

- **Destination:** write the MDX/Markdown file to `/Users/you/blog/content/writing/<slug>.md`
- **Filename:** English kebab-case slug derived from the title.
- **Format:** use the frontmatter shape defined in `profile/voice.md`. Set `draft: true` until I confirm; I'll flip it myself.
- **After writing:** tell me the file path and the local URL it will serve at. Do not stage, commit, or push anything; I'll review the diff and commit it myself.

## Example: just hand me the file

- **Destination:** leave it in `drafts/<slug>.md`. (This is the default with no publish.md at all; you only need this file if you want a non-default destination.)
