---
name: writing-reports
description: Write and review shareable prose deliverables — internal reports, BD/prospect briefs, summary docs, anything shipped as a PDF or pasted into Slack — so a busy human actually reads it. Load writing-core first; this adds human-scannability structure, fact-blocks, trailing-citation linking, and honesty rules. Use when authoring or editing a report or brief, or when the ask is "make this scannable / tighter / less AI-ese / easier to read".
---

# Writing Reports

Shareable prose deliverables: internal reports, BD/prospect briefs, summary docs
— read out of context, in Slack or as a PDF, by a busy human. **Load
`writing-core` first**; the AI-ese (§5), out-of-context (§6), and trailing-citation
(§9) rules are central here. This skill adds the report-specific structure.

**Governing principle: human scannability.** A doc that can't be skimmed won't get
read. The reader scans down the page — headings, bold names, bullets, trailing
citations — they do not read word-for-word. Every choice below serves skimming;
when two options both work, pick the one that's faster to skim.

## Structure

- **Lead with what to do.** Action items / top findings / the ask come first; trends, methodology, and caveats after. The reader's first question
  is "what do I do?" — answer it before the background.
- **Frame each section by its history** (core §3) — lead with the arc ("discovery
  call Dec 2023 → churned Oct 2024 → fresh pain June 2026") so every later line
  lands against a frame the reader already holds.
- **Lead each entry with "the ask"** — one line: what you want this account to do
  or buy. Everything else is judged against that goal.
- **Give each profile a uniform fact-block.** Every entry gets the SAME bullet block above
  its prose, same order, so profiles are scannable at a glance (e.g. **Ask** /
  **Status** / **Contact** / **CRM**). Unknown field → "none on record"; don't drop
  the bullet.
- **Add a TOC and a tight summary** at the top of anything long. The summary
  is skimmable in ~5 seconds, never a wall of text.
- **Put in-depth content before the overview table**, when both exist — that table
  (distinct from the prose summary up top) is a scannable index into detail the
  reader can already reach.
- **Link the table's name column.** A link-less table is just a list — the name
  must jump to the detail entry (`[Name](#slug)`).

## Lists and visual boundaries (the top readability lever)

- **Bullet what gets scanned.** A long run of orgs/items comma-spliced
  into a paragraph is unreadable; one item per bullet: a **bold name**, then ≤1
  short clause and a trailing citation, so the eye runs down the bold left edge. But it's a
  judgment call, not a law: two or three items that read naturally in a sentence
  are often better left inline. Bullet what gets scanned or compared; leave prose
  that flows.
- **Make sub-group labels real headings.** A bold "Net-new companies:" inline butts
  against the previous entry and reads as part of it. Make it a real heading with
  space above, not a bold lead-in.
- **Give each block a clear boundary.** Repeating units (profiles) get a prominent heading, a
  rule or top border, and air between them, so no two blocks look merged. Hierarchy
  must read: section > sub-group > item-name > body.

## Linking

Core §9 governs; report-specific emphasis:

- **Link every issue/PR number.** A bare `#41` is never acceptable → `[#41](url)`.
- **Watch multi-clause sentences.** A sentence stringing several claims together
  (often semicolon-separated) needs a citation on EACH clause. Linking two of three
  is the common miss — go clause by clause.
- **Use the number as link text** (`([#304](url))`); fall back to `(source)` when there's no number. (Repo-specific tooling may inject heading ids for internal PDF
  jump-links — e.g. `[Name](#slug)`; check the project.)

## Quoting evidence

- **Quote when it sharpens the point.** A short direct quote from the actual
  issue/PR is high-signal — it shows the subject said it, in their
  words. Keep it short; still add the trailing citation. Quotes beat paraphrase for
  load-bearing evidence.
- **Blockquote the key quote**, not inline, so the eye catches it. One or two per profile; the rest stay inline or paraphrase.
- **Label evidence "Relevant issues"** (not "Opener"), as a real bulleted list —
  one bullet per issue, short summary + trailing link. Reuse the summaries
  already in the prose.

## Off-limits in the reader's copy

The doc is read out of context (core §6). Beyond that, for reports specifically:

- **No repo/tooling housekeeping** — "`reports/` is gitignored", file paths. A plain
  confidentiality marker (*Private — internal use only*) is the only meta allowed.
- **No internal metrics or analyst jargon** — never print tool counts/buckets ("62
  items", "PR-weighted", "signal: high"). Translate to plain activity language: "a
  sustained, active integration", "a one-off mention". Describe magnitude in words.
- **No unforced judgment.** When the task is to surface
  items, report each uniformly and let the reader judge. Cut the opinion layer: a
  priority ranking ("work these first"), an importance tier ("smaller adopters"), a
  confidence label ("lower confidence"), a tactical instruction ("get in before they
  build"). A wrong call — burying the best lead in a "minor" bucket — is worse than
  no call. Order and group by a *fact* (status, org type), not by your own score,
  unless the reader asked for a ranked list.

## Honesty

- **Date every interaction** you cite (call, meeting, note, issue) — from metadata
  or timestamps. A 2023 call and a last-month one mean different things; flag stale
  facts as stale.
- **Weight by traction.** Don't present a one-off as ecosystem-moving; frame low-traction items honestly as experiments.
- **State what you couldn't verify.** If a status is inferred (e.g. "net-new" from
  the absence of a record), say it's a strong signal, not a guarantee.

## Review

Skim it as the target reader would in 30 seconds:

- Can you tell what to do from the top alone?
- Does every repeating block look distinct (heading + air + rule)?
- Is every org/item list bulleted with bold names?
- Are links trailing citations, not whole sentences? Does every `#number` link?
- Any wall-of-text paragraph, regular-beat triad, fluff, or internal jargon left (§5)?
- Any editorial judgment the facts don't force — a ranking, tier, confidence label,
  tactical instruction, or line about the document itself (§6)? Cut it.
- Are multi-issue pointers a real "Relevant issues" bulleted list, and is each
  profile's one load-bearing quote a blockquote?
- Do the TOC / table / cross-references actually resolve?

Fix anything that fails, then rebuild.
