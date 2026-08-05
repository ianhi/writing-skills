---
name: writing-comms
description: Write short-form technical communication you send to other people — PR descriptions, commit messages, Slack, issue comments. Load writing-core first; this adds format conventions for each type. Use when drafting a PR body, a commit message, or a Slack update. (Talking with the user in-session is writing-conversation, not this.)
---

# Writing Comms

> **Critical gate.** Confirm AI-authored communication is welcome here before you
> draft. This is someone else's venue, and many projects, teams, and communities
> restrict or ban AI-written contributions. Unless you already know it's accepted,
> check with the user before drafting anything sent under their name, and follow
> the venue's disclosure norms.

Short-form communication you send to other people — PR descriptions, commit
messages, Slack, issue comments. (Talking with the *user* in-session is
`writing-conversation`, not this.) **Load `writing-core` first** — plain/direct
prose (§4), no AI-ese (§5), and writing for readers without your context (§6) do
most of the work here. This skill adds per-format conventions.

## PR descriptions

- **Lead with what changed and why** — the reviewer's first question. One or two
  sentences before any detail.
- **Motivate, then summarize.** What problem this solves → what the change does →
  anything non-obvious for the reviewer (risky areas, follow-ups, how it was
  tested).
- **Link the issue and key code** (§9). Reference specific lines for anything a
  reviewer should look at closely.
- Write for someone reading it cold in the PR list months later (§6) — not "as
  discussed in standup."

## Commit messages

- **Subject: imperative, specific, ~50 chars.** "Fix cache eviction under
  concurrent writes", not "fixes" or "update code."
- **Body: why, not what.** The diff shows what changed; the message explains why it
  needed to. Wrap ~72 chars.
- **Describe the whole staged change**, not just the part most salient to you right
  now.
- Follow the project's and the user's commit conventions (trailers, attribution,
  scope prefixes). Check local instructions.

## Slack / issue comments

- **One point per message.** Don't bury a question under context — ask it, then
  give the context.
- **Front-load the ask.** If you need a decision or an action, say so in the first
  line; thread the reasoning below.
- **Link, don't paste** long logs or code — a permalink keeps the channel scannable.

## Review

Before sending, reread once as the recipient:

- Is the answer / ask / change in the first line?
- Any AI-ese, filler, or hedging to cut (§4, §5)?
- Does it make sense to someone without your session context (§6)?
- Are issues, PRs, and code linked rather than described?
