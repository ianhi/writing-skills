# writing-skills

---

We spend a huge amount of time and energy reading agent output. Just as we used to tune our IDEs to our taste with extensions, today we should tune our agents text output to our taste. This is my effort toward that end. I hope it helps you. - Ian

---

A collection of technical-writing skills for AI coding agents — a shared **core**
plus genre specializations. Each specialization covers both **authoring** and
**review** against one rubric, so the standards get baked in at writing time
rather than bolted on afterward.

## The skills

| Skill | Use it for |
|-------|-----------|
| **`writing-core`** | The shared foundation. Load first for any writing task: reader effort, confirming audience, voice, structure, plain/direct prose, avoiding AI-ese, out-of-context reading, verified and sourced claims. |
| **`writing-docs`** | Reference and how-to docs — API docs, READMEs, contributor guides, design docs. |
| **`writing-teaching`** | Tutorials, teaching notebooks, explanatory/blog posts. Narrative arc (ABT), the pedagogy rubric, and a reviewer-subagent workflow. |
| **`writing-comms`** | Short-form you send to others — PR descriptions, commit messages, Slack, issue comments. |
| **`writing-reports`** | Shareable prose deliverables — reports, BD/prospect briefs, summaries read out of context. Human scannability first. |
| **`writing-conversation`** | Talking with the *user* in-session. Always-on (reference from global instructions), not a per-task genre. |
| **`writing-review`** | Review any prose against the rubric — dispatch a reviewer subagent, rank findings, optionally apply. The `/simplify` for writing. |

## How they fit together

`writing-core` holds every principle common to technical writing. The four **genre
skills** are thin and assume it — load core first, then the genre that matches what
you're writing. Review is a section *within* each genre skill, built on the same
rubric as its authoring guidance: read the review bar before drafting.

Two skills sit outside that shape. `writing-conversation` governs the live
back-and-forth with the user rather than producing an artifact, so it's always-on
and defers all shared craft to `writing-core`. `writing-review` is a runner, not a
rubric: it dispatches a reviewer subagent that grades a piece against `writing-core`
plus the relevant genre skill.

## Use

### In Claude Code

Install as a plugin:

```
/plugin marketplace add ianhi/writing-skills
/plugin install writing@ianhi-writing
/plugin reload-plugins
```

`reload-plugins` activates it in the current session; later sessions pick it up on
their own. Remove it with `/plugin disable writing` or `/plugin uninstall writing`.

Update to the latest version:

```
/plugin marketplace update ianhi-writing
/plugin update writing@ianhi-writing
```

Updates track the repo's default branch.

Installing gives you all seven skills plus an **always-on kernel**. A `SessionStart`
hook prints `skills/writing-core/kernel.md` into context at the start of every
session (and again after `/clear` or a compaction), so the writing rules govern from
the first turn without the agent having to choose to load a skill. The genre skills
still auto-load per task from their descriptions; review any prose with
`writing-review`.

### The kernel vs. the full skills

The kernel is small on purpose (~700 tokens): the conversation rules, the core
writing rules, and a checklist to scan before finalizing prose. It is a floor, not
the full rubric — it names `writing-core` and the genre skills and tells the agent
to load them for a real writing task. Sessions stay cheap; the depth loads only when
you are actually writing.

### Any other agent

Plain Markdown, usable by anything that reads instructions. Inject
`skills/writing-core/kernel.md` wherever your agent reads instructions every turn
(that is all the hook does), or load `writing-core` and `writing-conversation`
yourself. Load one genre skill per task alongside core, and review with
`writing-review`.

## Developing

To work on the collection itself — conventions, cross-reference upkeep, the review
bar — see [AGENTS.md](AGENTS.md).

## Lineage

Distilled and refactored from earlier single-purpose skills (`doc-writing`,
`pedagogy-review`, `report-writing`) into one coherent, deduplicated collection.
