# writing-skills

---

We spend a huge amount of time and energy reading agent output. Just as we used to tune our IDEs to our taste with extensions, today we should tune our agents text output to our taste. This is my effort toward that end. I hope it helps you. - Ian

---

A collection of technical-writing skills for AI coding agents — a shared **core**
plus genre specializations. Each specialization covers both **authoring** and
**review** against one rubric, so the standards get baked in at writing time
rather than bolted on afterward.

## Install

In Claude Code, install from the `ianhi-plugins` marketplace:

```
/plugin marketplace add ianhi/claude-plugins
/plugin install writing@ianhi-plugins
/plugin reload-plugins
```

`reload-plugins` activates it in the current session; new sessions pick it up on
their own. Update later with `/plugin marketplace update ianhi-plugins` then
`/plugin update writing@ianhi-plugins`; remove with `/plugin uninstall writing`.

You get all seven skills — they auto-load per task from their descriptions — with
the core and conversation rules [always on](#always-on). Using a different agent?
The skills are plain Markdown; see [Any agent](#any-agent).

## The skills

| Skill | Use it for |
|-------|-----------|
| **`writing-core`** | The shared foundation. Load first for any writing task: reader effort, confirming audience, voice, structure, plain/direct prose, avoiding AI-ese, out-of-context reading, verified and sourced claims. |
| **`writing-docs`** | Reference and how-to docs — API docs, READMEs, contributor guides, design docs. |
| **`writing-teaching`** | Tutorials, teaching notebooks, explanatory/blog posts. Narrative arc (ABT), the pedagogy rubric, and a reviewer-subagent workflow. |
| **`writing-comms`** | Short-form you send to others — PR descriptions, commit messages, Slack, issue comments. |
| **`writing-reports`** | Shareable prose deliverables — reports, BD/prospect briefs, summaries read out of context. Human scannability first. |
| **`writing-conversation`** | Talking with the *user* in-session. Always-on, not a per-task genre. |
| **`writing-review`** | Review any prose against the rubric — dispatch a reviewer subagent, rank findings, optionally apply. The `/simplify` for writing. |

## How it fits together

`writing-core` holds every principle common to technical writing. The four **genre
skills** are thin and assume it — load core first, then the genre that matches what
you're writing. Review is a section *within* each genre skill, on the same rubric as
its authoring guidance.

Two skills sit outside that shape. `writing-conversation` governs the live
back-and-forth with the user rather than producing an artifact, so it's always-on.
`writing-review` is a runner, not a rubric: it dispatches a reviewer subagent that
grades a piece against `writing-core` plus the relevant genre skill.

## Always-on

Installing the plugin adds a `SessionStart` hook that prints `writing-core` and
`writing-conversation` into context at the start of every session (and after
`/clear` or a compaction), so the rules govern from the first turn without the
agent having to choose to load a skill. Together they're ~5k tokens — cached, a
fraction of a percent of context — and they're the full rubric, so there's no
smaller summary to keep in sync. Genre skills still load per task.

The hook only fires when the collection is installed as a plugin — copying or
symlinking the skills into `~/.claude/skills/` makes them loadable but not
always-on. To verify it's working, start a fresh session and ask whether the
writing-core rules are in context.

## Any agent

The skills are plain Markdown, usable by anything that reads instructions. Inject
`skills/writing-core/SKILL.md` and `skills/writing-conversation/SKILL.md` wherever
your agent reads instructions every turn (that is all the hook does), then load a
genre skill per task.

## Developing

To work on the collection itself — conventions, cross-reference upkeep, the review
bar — see [AGENTS.md](AGENTS.md).
