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

`reload-plugins` makes the skills available in the current session, but it does not
replay `SessionStart`, so the always-on rules below don't load until you `/clear` or
start a new session — or run `/writing-core` to load them on the spot. Update later with `/plugin marketplace update ianhi-plugins`
then `/plugin update writing@ianhi-plugins` — both need a version bump in the
plugin manifest to take effect. Remove with `/plugin uninstall writing`.

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

Installing the plugin adds a `SessionStart` hook that tells the agent to load
`writing-core` and `writing-conversation` at the start of every session (and after
`/clear` or a compaction), so the rules govern from the first turn instead of
waiting for the agent to notice it needs them. Genre skills still load per task.

The hook injects the instruction, not the rules themselves. Claude Code truncates
`SessionStart` output to a 2KB preview and spills the rest to a file the model
never reads, so a hook that printed both files (~20KB) would deliver about a tenth
of `writing-core` and none of `writing-conversation`. Loading them therefore costs
a tool call per session. Subagents get nothing either way — `SessionStart` runs
once for the main session, and a subagent inherits only the prompt you hand it, so
tell it to load the skills when you delegate prose work.

The hook only fires when the collection is installed as a plugin — copying or
symlinking the skills into `~/.claude/skills/` makes them loadable but not
always-on. When it's working, a fresh session loads `writing-core` on its first
turn.

## Any agent

The skills are plain Markdown, usable by anything that reads instructions. Inject
`skills/writing-core/SKILL.md` and `skills/writing-conversation/SKILL.md` wherever
your agent reads instructions every turn, then load a genre skill per task. On a
platform with no size limit on injected context this beats the plugin hook, which
has to ask for the files rather than supply them.

## Developing

To work on the collection itself — conventions, cross-reference upkeep, the review
bar — see [AGENTS.md](AGENTS.md).
