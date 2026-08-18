---
name: writing-proposals
description: Write and review documents that propose a course of action or technical approach for review and decision — design docs, plan docs, RFCs, ADRs, technical proposals. Load writing-core first for the shared foundation; this adds what's specific to a proposal, namely a decision-first structure, an explicit ask, alternatives considered, honest tradeoffs, and bounded scope. Use when authoring or editing a design doc, plan, RFC, or ADR, or when asked to make a proposal clearer or more convincing. Documentation of a system that already exists is writing-documentation; a report of findings is writing-reports.
---

# Writing Proposals

Documents that propose an approach and get a decision made on it — design docs,
plan docs, RFCs, ADRs, technical proposals. **Load `writing-core` first**; this
skill adds only what's specific to a proposal.

**Governing principle: the reader is a reviewer who will critique.** Unlike
documentation (which explains a system that exists) or a report (which a busy
reader skims for the finding), a proposal is read closely by someone who will
engage with the argument, weigh the tradeoffs, and approve, push back, block, or
revisit it later. Every choice below serves that reader: put the decision, the
reasoning, and the weak point where a reviewer can find them.

## Authoring

- **Lead with the problem and the proposed decision.** State what you're solving
  and what you propose before any detail — that decision is the destination (core
  §3), so it goes at the top, not after the reader has waded through the mechanism.
- **Say what you're asking for.** Name the response you want: approval to build,
  input on a direction, or a record of a decision already made (an ADR). The reader
  responds differently to each, and can't calibrate without knowing which.
- **Give alternatives, and why you rejected each.** For every option a reviewer
  might raise, say why not — honestly, against a real version of it, not a straw
  man (core §5). Skip it and reviewers re-raise those options in comments, and the
  decision stalls.
- **State the tradeoffs your choice pays.** Every approach has costs; name the ones
  yours incurs. A proposal that reads as all upside reads as unexamined, and a
  reviewer who finds the hidden cost trusts the rest of it less.
- **Surface the contested decision — don't bury it.** Put the choice most likely to
  draw an objection where a reviewer will find it, so review spends its effort on
  what's actually at stake rather than on what you were confident about anyway.
- **Bound the scope.** State what's in, what's out, and the non-goals. An unbounded
  proposal invites objections about things you never meant to cover.
- **Be precise enough to critique.** Give the interfaces, data flow, and failure
  modes concretely enough that a reviewer can find a flaw — not just nod along. A
  vague proposal gets rubber-stamped and then fails in review-that-matters: the
  build.
- **Order the argument by dependency.** A reviewer following your reasoning should
  never hit a term or component you define later (core §3). This is the one habit
  proposals borrow from documentation.

## Review

Run a review with `writing-review`. Read it as a reviewer who must approve or push
back, then check:

- **Decision up front** — from the top alone, is the problem and the proposed
  decision clear, before the mechanism?
- **The ask** — is it clear whether you want approval, input, or a record?
- **Alternatives** — is each real option listed with an honest reason for rejection,
  not a straw man?
- **Tradeoffs** — are the costs of the chosen approach stated, or does it read as
  all upside?
- **Contested decision** — is the objection-drawing choice surfaced where review
  will find it, not buried?
- **Scope** — are in-scope, out-of-scope, and non-goals explicit?
- **Precision** — could a reviewer find a flaw from what's written, or only nod?
- **Dependency order** — any component or term used before it's defined (§3)?
- **Reachable pointers** — does every link resolve for the reader, with no
  internal-only handoff doc, private KB, or scratchpad path (§9)?
- **Verified claims** — is every assertion about current behavior backed by
  something checkable, and every rationale real, not invented (§8)?
