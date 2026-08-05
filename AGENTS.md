# AGENTS.md — working in this repo

How to develop and maintain the writing-skills collection. For what it is and how
to install it, see [README.md](README.md).

## Structure

- `skills/<name>/SKILL.md` — one skill each; frontmatter `name:` matches the
  directory name.
- `.claude-plugin/` — `plugin.json` + `marketplace.json`, so the repo installs as
  the `writing` plugin.
- `writing-core` defines the shared principles; the genre skills and
  `writing-conversation` build on it.

## Editing conventions

- **`writing-core` is the single source of truth for shared principles.** If a
  principle applies to more than one skill, it lives in core and the others
  reference it by section number ("core §N"). Don't duplicate — a genre skill holds
  only what's specific to its genre.
- **Each genre skill keeps an Authoring and a Review section on one rubric.** Don't
  split authoring and review into separate skills.
- **Make each `description` concrete about *when to load* the skill** — that's what
  triggers it.
- **Preserve the author's voice.** This is a personal collection; treat the wording
  as intentional and suggest rather than silently rewrite.

## These skills must obey their own rules

The collection is judged against itself: the SKILL.md prose must exemplify what it
teaches. So **load `writing-core` first**, before you edit any SKILL.md, and write
through it — don't just re-read it afterward. Editing a skill *about* writing
without the rules loaded is how these files end up breaking their own advice (a
full-sentence bold, a non-parallel list). The rules that catch them most often:
lead with the point, write plainly and directly, keep lists parallel, order by
importance, define terms, bold a few words (never a whole sentence). Re-check against core before
finishing; a rule the files themselves break isn't ready to ship.

## Cross-reference upkeep

- When you move or renumber a `writing-core` section, update every `§N` / "core §N"
  pointer in the other skills. Find them: `grep -rn "§" skills`.
- Keep cross-references monotonic (core §3) — if they read out of order, the
  sections are probably mis-ordered.

## Validation

After a substantive change, run `writing-review` over the SKILL.md files — the
collection is judged against its own rubric (no AI-ese, parallelism,
importance-order, defined terms, no full-sentence bolds), plus cross-reference
integrity. Fix what it finds, and hold that bar on every substantive change.
