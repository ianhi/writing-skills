---
name: writing-review
description: Review prose for quality against the writing rubric — the /simplify for writing. Dispatch a reviewer subagent (or fan out by lens), report findings ranked by impact, and optionally apply the fixes. Use to review or tighten a doc, report, tutorial, PR, or any prose, or when asked "review this writing / make it clearer / cut the AI-ese".
---

# Writing Review

The `/simplify` for prose: review writing against the collection's rubric, report
findings ranked by impact, and optionally apply the fixes. This skill is the
*runner* — the *rubric* is `writing-core` plus the matching genre skill's Review
section, so load those and don't restate them here.

Dispatch a subagent to keep the analysis out of the main context (as
`writing-teaching`'s reviewer workflow does). You are the confidence filter on what
it returns.

## Workflow

1. **Re-read it yourself first** if the piece is your own draft — `writing-core`
   §10. Reviewers are a second opinion on revised prose, never a substitute for
   that pass.
2. **Scope and calibrate.** Identify the target, its genre, and its audience —
   confirm the audience (`writing-core` §1) if it isn't obvious, since the rubric is
   applied relative to it. Load `writing-core` + the matching genre skill.
3. **Dispatch reviewers — fan out by default.** Run the lenses below as *parallel*
   subagents (each reads the whole piece, grades one lens); each reviewer loads
   `writing-core` and the genre skill on its own — subagents don't inherit your
   loaded skills, and a pasted paraphrase gives them your blind spots, so they
   miss what you missed. Merge and dedupe the findings in the main context. Drop
   to a single reviewer only for a short piece. Reviewers are bounded judgment,
   not authoring, so run them on a cheaper, faster model — Sonnet by default,
   Haiku for the mechanical lenses (parallelism, AI-ese, dead references). A
   general-purpose agent is fine; no bespoke type needed.
4. **Report, ranked by impact.** A broken structure or a misled reader outranks a
   wording nit. Each finding gives its location (`file:line` + the quoted passage),
   the rule it breaks, and the fix shown as a before/after or small proposed diff.
5. **Show before applying.** It's the user's piece (core collaboration) — present
   findings and let them choose. With `--fix`, apply the high-confidence, non-voice
   fixes directly (dead references, AI-ese, non-parallel lists, unsourced claims)
   and report the rest; never auto-rewrite the author's established voice.
6. **Re-run.** Expect two or three rounds on a substantial piece — fixes surface
   new issues. Stop when only minor or subjective items remain.

## Fan-out lenses

Split a large review so no single pass skims; each reviewer sees the whole piece
but grades one lens:

- **Structure & flow** — order, dependency, importance, framing, enumerated sets
  left as prose (§3, §4 + genre).
- **Prose & AI-ese** — plain and direct, subtraction, the AI-ese tells (§4's
  sentence-level rules, §5, §7).
- **Reader-context & honesty** — out-of-context leaks, verified and sourced claims
  (§6, §8, §9).
- **Genre fit** — the matching genre skill's own Review checklist.

## Reviewer subagent prompt

```
Review this writing against the rubric — report problems, don't rewrite.

Target: DOC   (genre: GENRE   audience: AUDIENCE)

1. Load `writing-core` and the GENRE skill yourself (Skill tool), then read the
   piece in full. There is no rubric summary in this prompt on purpose — the
   skills are the rubric.
2. Grade it for THIS audience and genre. Overriding lens: does
   every choice minimize the reader's effort? Judge repeated constructions —
   antithesis, triad — by their count across the whole piece, not one at a time;
   a carve-out that excuses each instance still leaves a signature.
3. Report findings RANKED BY IMPACT. Each: location (`file:line` and the exact
   quoted passage), the rule it breaks (one sentence), and the fix as a before/after
   or small proposed diff, specific enough to apply.

Report only real issues; if a section is good, say so in a line. Don't flag the
author's voice as a defect. Close with the 3 highest-impact fixes.
```
