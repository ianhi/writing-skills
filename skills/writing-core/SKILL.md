---
name: writing-core
description: The shared foundation for all technical writing — minimizing reader effort, confirming audience, voice, narrative structure, plain and direct prose, avoiding AI-ese, and verifying and sourcing claims. Load this first for any writing task, then load the genre skill (writing-docs, writing-teaching, writing-comms, or writing-reports) that fits what you're writing.
---

# Writing Core

The principles common to every kind of technical writing — docs, tutorials,
blog posts, reports, PRs, commit messages, chat. Load this first, then the **genre
skill** that fits (`writing-docs`, `writing-teaching`, `writing-comms`, or
`writing-reports`). Each genre skill holds an Authoring and a Review section on
one rubric: read its review bar *before* drafting.

Talking with the user in-session isn't a genre — the always-on
`writing-conversation` covers it, as addendums to this core: the craft rules here
apply to dialogue too; the audience and out-of-context gates do not, because the
user is present and shares your context.

## The overriding principle: make it easy for the reader

Every rule below serves one goal: **spend the reader's effort on your ideas**, not
on parsing your writing. Attention is a fixed budget — whatever they burn
decoding a clumsy sentence or hunting for a source is gone from understanding the
point. When a choice is unclear, pick what costs the reader less.

## Writing is collaborative — keep the user in the loop

The work is **collaborative**, but the piece is **the user's**: you do the drafting
and the craft; they decide the direction.

So don't disappear and return with a finished draft built on guesses. Involve
them at the decisions that shape the piece — **who it's for** (§1), **the voice
and structure**, and **any rewrite of prose they already wrote** (§2). When a
choice would change its direction, surface it and ask rather than deciding
silently.

## 1. Confirm the audience before you write

Every other judgment — what to assume, what to cut, how to sequence — is made
relative to one audience. So pin it down *first*: treat confirming it as a **gate**
you clear before drafting prose. Unless the audience is genuinely obvious,
**confirm it with the user** rather than guessing.

Common audiences and what they change:

- **End users** — "how to use"; hide internals.
- **Contributors** — "how it works"; show internals.
- **Learners / researchers** — "why"; build from first principles.
- **Decision-makers** — "what it does and why it matters."

**Code comments and docstrings** are a special case, outside this gate. They're
part of the code, with a fixed audience (the next developer in this file) and
their own conventions — write them with your normal coding latitude.

For **prose**, the gate scales with the cost of guessing wrong:

- **Confirm first** when a standalone piece would be written differently for
  different readers — a doc, a tutorial, a report, a blog post, a README written as
  its own deliverable. One line — "who's the reader: end users, contributors, or
  decision-makers?" — saves a whole rewrite.
- **Just proceed** when the reader is obvious or the writing rides along with a
  task the user already scoped: a commit message, a reply in an ongoing thread,
  routine docs generated as part of a build.

Once set, hold the audience constant through every section — drift within a page
is confusing.

### Introduce only what the audience doesn't already know

The audience fixes what you can take for granted, and therefore what you must
introduce before relying on it.

- **Concepts** — build up an idea, mechanism, or piece of background the audience
  lacks before you lean on it; don't re-derive one they already hold. (At the
  section scale, the same move is *problem before solution* — see `writing-teaching`.)
- **Terms** — define a term this audience won't know the first time you use it. An
  undefined term is one of the easiest ways to lose a reader; one they already know
  needs no gloss.

When you're unsure whether to explain something, that uncertainty usually means the
audience isn't pinned down yet.

## 2. Match the voice — don't impose one

Detect the voice from existing content; if none exists, ask. A blog post wants
personality; reference docs want precision; a tutorial wants warmth; a commit
message wants terse directness.

When the user has written prose, treat their phrasing as intentional. Fleshed
prose is the author's: **don't rewrite it without confirming first** — propose the
change and let them decide, rather than silently replacing their words. Skeleton
and TODO stubs are fair game to draft.

## 3. Structure the piece

Structure is the highest-leverage way to cut reader effort — order and framing do
more than any sentence-level edit. A human takes in a document line by line, not
all at once, so each line must land against a frame they already hold. A few
primitives are universal:

- **Start with the destination.** The most important idea goes at the top as a
  motivating hook, not buried after the building blocks.
- **Frame first, then detail.** For anything with history, lead with the arc —
  "talked in 2024 → churned → fresh pain in 2026".
- **Order by dependency.** If A references B, define B first. A bare forward
  reference — a "see below", a term used before it exists — is close to
  unacceptable: it forces the reader to hold an undefined thing in mind or go
  hunting. The one legitimate forward pointer is a *deliberate, signposted* one
  that answers a question the
  reader is already forming — "wondering how this scales? good instinct — we get
  there in §7."
- **Order by importance, monotonically.** Within a list or section, let importance
  move one way — build up to the most important, or lead with it and taper — never
  bounce (big, trivial, huge, minor). You take the whole list in at once, so this
  is a place your own instinct won't warn you: check it deliberately.
- **Keep cross-references monotonic.** When the text points to its own sections,
  they should come up roughly in order. If you catch yourself citing §7 before §3,
  that's a smell the sections themselves are mis-ordered — fix the order, not the
  reference.
- **Write the intro and summary last.** They're easier, and far less vague, once
  the body exists. Drafting them first produces generic hedging ("this document
  explores various aspects of…") you'll just rewrite.

The *shape* those primitives take is genre-specific — don't force one mold on
every piece; the genre skill you loaded defines its shape.

## 4. Write plainly and directly

The default register for all technical writing.

- **Lead with the answer.** No preamble, no wind-up that defers the point ("so
  the first question is…"). The first sentence carries the point.
- **Hold one altitude.** Set the level of detail the point needs and stay there;
  drop into a specific or climb to a generalization only on purpose, signposted. A
  deliberate foray into detail is good writing; an unmarked slide between the
  abstract and the concrete mid-passage is the tell.
- **Cut filler and hedging.** "it's worth noting", "in order to", "basically",
  "essentially", "I think", "as we can see" — delete them. One strong sentence
  beats three.
- **Prefer plain words.** "use" not "utilize", "helps" not "facilitates". Skip
  throat-clearing adjectives ("robust", "seamless", "powerful", "comprehensive")
  unless they carry real information.
- **Pin every referent.** Every "this", "it", "that", "here" resolves to one
  unambiguous antecedent; the reader should never reread to find what it points at.
  "welcome here" → "welcome in this repo".
- **One name per thing.** Once you name a concept, use that exact name everywhere;
  a synonym ("the runner" / "the executor" for the same component) reads as a
  second concept.
- **Format visually when it helps.** The layout of the text — bullets, short
  headers, tables — as opposed to §3's organization. Good when it aids scanning;
  reach for it freely. Don't split a single thought across bullets, and don't use
  formatting to dress up padding.
- **Bold a few words.** Not whole sentences — emphasis works by contrast. Bold the
  two or three words that carry the point, or none.
- **Keep parallel things parallel.** Headings at one level, and bullets in one
  list, should share grammatical form — all imperatives, or all noun phrases, not a
  mix.

## 5. Avoid AI-ese

The tells that mark writing as machine-generated — empty phrases that carry no
information and erode trust. Treat the list below as *tells, not a banned-words
list*: ban the emptiness, not the word.

One general test catches shapes no list can enumerate: does a sentence carry a
fact, or only *comment on* the content — how to feel about it, that it's coming,
that it matters? The second kind is the tell.

- **The regular-beat triad.** Three short parallel phrases restating one idea in
  the same rhythm — "fully net-new, no warm path, straight cold." Say it once, with
  the real fact; vary sentence length.
- **"X isn't just Y — it's Z."** And its cousins: "not only… but…", and the plain
  antithesis "A, not B". A hype frame masquerading as insight — state what X is.
  The antithesis is empty when B is a straw man ("a decision, not a default" names
  nothing) and earns its place when B is a real mistake the reader might make
  ("comment the code, not the change" names the error).
- **Pileups.** Em-dash pileups and adjective stacks. One em-dash per sentence at
  most. Also decorative bold-lead-in stacks — every bullet opening with a bold
  *label* that carries no real content. (A bold *proper-noun name* used as a
  scannable index is different and good — see `writing-reports`.)
- **Editorial fluff / hype conclusions.** Lines that tell the reader how to feel
  or restate the obvious with drama: "getting in front of it is the whole game",
  "make no mistake". State the fact; let the reader draw the conclusion.
- **Promissory framing.** The forward-looking twin of a hype conclusion:
  announcing or labeling what follows instead of just saying it — its importance
  ("the two reasons are worth separating", "here's the subtle part", "the key
  bit"), or its status as a list, aside, or boilerplate ("two things worth
  confirming:", "the one piece of ceremony:"). State the thing; if it matters,
  that shows.
- **Words used as texture.** "situational awareness", "worth noting", "at the end
  of the day", "de facto" — often reached for as tone, not fact. But any can be
  exact in the right spot ("the *de facto* standard"); cut only the empty use, not
  the word.

## 6. Don't rely on context only you have

The reader sees only the final artifact, read cold — in Slack, as a PDF, pasted
elsewhere, or opened five years later. They may know the subject well; what they
don't have is *your* context — this session, the process, the earlier drafts. Cut
anything that only makes sense to the person who wrote it.

One principle, code and prose alike: **comment the code, not the change**; **write
the document, not its edit history**. Describe what *is*, not how it came to be.

- **No process narration.** How many items you sampled, when you re-checked, "ordered
  roughly by leverage", "verified against X".
- **No prior-draft references.** "we cross-checked and the picture changed", "as
  discussed", "now updated to".
- **Don't describe the document.** "this report covers four prospects",
  "each section sets up the problem so you can decide", "read this through the lens
  of the table". State the substance; let the structure speak.
- **Don't address a specific person** ("you asked…") in something that ships to
  others.

## 7. Subtract to perfect

> *"Perfection is achieved, not when there is nothing more to add, but when there
> is nothing left to take away."* — Antoine de Saint-Exupéry

Most writing improves by *removal* — a tangent cut, a caveat deferred, a second
example that earns its place or goes. When adding and cutting both fix a problem,
prefer the cut. Brevity is not the goal, though — low reader effort is. Cut what
doesn't serve the reader; keep (and make explicit) what does.

**Proportion space to load.** The claim a piece exists to make earns more room
than the detail supporting it. Terseness is a default, not a quota — when the one
idea the reader came for is compressed into a subordinate clause, they read
straight past it. Before cutting, find the sentence that carries the piece; state
it plainly, on its own, with its consequence made concrete. Cut around it, not
into it.

## 8. Verify before you write it

Every claim must trace to something checkable, never to invention.

- **Claims match reality.** An assertion about behavior isn't acceptable until
  something confirms it — a run, a test, a worked example, a verifiable fact.
  The code (or the data) is ground truth; the prose describes what it shows.
- **Don't invent rationale.** If you can't find why something is the way it is,
  don't fabricate a reason. Remove it, or flag it as an open question.
- **Accurate references.** Citations, titles, and attributions are correct, not
  guessed. Anything that reads like an invented attribution is a defect.
- **Real artifacts over constructed ones.** Actual diffs, real command output,
  real paths are more convincing than polished synthetic examples.

## 9. Link and cite your claims

Linking *between* documentation pages is genre-specific — see `writing-docs`. What
is universal is sourcing your claims — enough that a reader can check them, not so
much that links become noise:

- **Link every load-bearing claim** — a specific blocker, a surprising behavior, a
  named person's experience, a number. A claim with no link reads as unsupported
  opinion.
- **Don't over-link.** Link what a skeptical reader would actually want to verify;
  skip the obvious, and don't re-link the same source at every mention. A page of
  blue text is as hard to read as one with no links.
- **Cite with a compact trailing link**, not a whole-sentence hyperlink — whole-phrase
  links bleed together and kill scanning.
  - Bad: `They [reproduced corruption in production](url) and [worked around it](url).`
  - Good: `They reproduced corruption in production ([#304](url)) and worked around
    it with a per-store lock ([#158](url)).`
- **Reference code at the line level** — permalinks to specific lines, not just
  files. Show both the problem location and the fix.
- **Never invent a URL.** If a claim can't be sourced, cut it or flag it — don't
  fabricate a link.

## 10. Re-read before you finalize

One deliberate pass, not a skim; the failure is not looking. Scan for:

- a winding preamble before the point → lead with the answer
- the central claim buried in a subordinate clause → give it its own sentence
- an unmarked jump between abstract and concrete → hold one altitude
- a vague "this / it / here" with no antecedent → name it
- a 3-beat triad, "X isn't just Y — it's Z", or an "A, not B" where B names no
  real mistake → say it once, plainly
- a sentence that only announces or rates what follows ("the key part", "worth
  noting") → cut it
- a whole-sentence bold, an em-dash pileup, or an adjective stack → cut
- process narration, a prior-draft reference, or a line describing the document
  → cut it
- an assertion nothing confirmed, or a rationale you couldn't find → verify,
  flag, or cut
- a non-parallel list → match the grammatical form
- a term used before it's defined → define it on first use
- a load-bearing claim with no source → link it or cut it
