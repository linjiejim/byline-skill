# byline-skill

**English** · [中文](README.zh-CN.md)

**Interview-first ghostwriting, as an agent skill.** Point it at a topic; it researches, interviews you with a few sharp questions, and drafts a finished article *in your own voice* from your confirmed answers. Every opinion in the piece is one you actually hold.

It works with [Claude Code](https://claude.com/claude-code) or any agent that loads skills. It inverts the usual AI-writing flow: not *AI drafts, you edit*, but **AI asks, you answer, AI drafts.** The hard part of writing isn't word-choice, it's thinking clearly; structured questions do that work.

## The one rule that matters

> **Conversation is not confirmation.** Even when you've already talked the idea through, byline-skill still interviews you. Chat is informed input, but no claim ships until you confirm it through Q&A. This is the guard that keeps the byline honest, and it's the whole point.

## Quickstart

```bash
git clone <your-fork-url> byline-skill
# install as a skill, e.g. symlink into your agent's skills dir:
ln -s "$PWD/byline-skill" ~/.claude/skills/byline-skill
```

Then set up your profile, either way:

- **Copy the templates** and fill them in:
  ```bash
  cd byline-skill && cp examples/*.md profile/
  # edit profile/author.md, profile/voice.md, profile/work.md
  ```
- **Or just run it** and let the skill interview you to build `profile/author.md` and `profile/work.md` on the first pass. Point `work.md` at wherever your existing writing lives (a folder or a URL) so voice has a real source.

Invoke it by asking your agent to "interview me and write a post about X", or `/byline-skill` in Claude Code.

## What you maintain

Everything in `profile/` is yours and is gitignored, so your fork never leaks personal data:

| File | What it holds |
|------|---------------|
| `profile/author.md` | Who you are: identity and background only. |
| `profile/voice.md` | Your language, punctuation, structure, and house format. |
| `profile/work.md` | Where your past writing lives, plus a one-line index of each piece. |
| `profile/publish.md` | *Optional.* Where finished drafts should be written. Omit it to stop at `drafts/`. |

Voice and positions are re-derived from your **real past articles** each time (indexed in `work.md`), not from a static description, so they never go stale. The body of work is the compounding asset.

## Layout

```
SKILL.md                  the loop (load → research → interview → draft → cite → review → publish)
references/
  interview-method.md     how to ask: question types, follow-up logic
  drafting.md             voice, provenance, two-tier citations
  red-lines.md            the non-negotiables + pre-delivery checklist
examples/                 templates you copy into profile/ (committed)
profile/                  your private data (gitignored)
drafts/                   generated articles (gitignored)
```

## Output and publishing

byline-skill writes a finished article to `drafts/<slug>.md` as plain Markdown. If you create `profile/publish.md`, it will also write the file into your blog/repo in your format. **It never runs git** (no commit, no push), so nothing goes live under your name without your hand on it. You review and ship.

## Honest limitations

A skill is not a silver bullet. Be clear-eyed:

- **No structural guard on the byline.** The same agent interviews *and* drafts, so it *can* "helpfully" complete your thought. A purpose-built app prevents this structurally; a skill can't. The Phase 5 self-review (`references/red-lines.md`) is the only substitute, so it's done honestly, every time.
- **The surprising follow-up is hard.** The model reliably asks competent questions; catching the contradiction you didn't see is the part the method pushes on but doesn't fully solve.
- **Citations need your check.** The "verify yourself" list is not optional; AI citation-finding carries hallucination risk.
- **It's still text.** It doesn't capture the hesitation and tone a face-to-face interview would. Carrying your context across sessions means fewer questions, which only partly compensates.

## Why a skill, not a product

A hosted app can't see your past work, so it can't help a new piece build on or cross-reference your old ones. Writing compounds, and that compounding lives locally. Most people who write already have an agent they like; the leverage is in layering a refined SOP onto the tool they already use, not in learning another mediocre UI. And a skill is customizable and version-controlled: your voice, format, and publishing rules are plain files you own and can track in git. This project distills the core SOP and hands the rest back to you.

## License

MIT. See [LICENSE](LICENSE).
