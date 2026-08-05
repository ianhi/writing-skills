---
name: writing-core
description: The shared foundation for all technical writing — minimizing reader effort, confirming audience, voice, narrative structure, plain and direct prose, avoiding AI-ese, and verifying and sourcing claims. Load this first for any writing task, then load the genre skill (writing-docs, writing-teaching, writing-comms, or writing-reports) that fits what you're writing.
---

# Writing Core

The principles common to every kind of technical writing — docs, tutorials,
blog posts, reports, PRs, commit messages, chat. Load this first, then load the
**genre skill** that fits. A *genre skill* is one of the four below, each covering
a single kind of writing:

- **`writing-docs`** — reference and how-to documentation.
- **`writing-teaching`** — tutorials, teaching notebooks, anything whose job is
  to teach a concept.
- **`writing-comms`** — short-form sent to others: PR descriptions, commit
  messages, Slack, issue comments.
- **`writing-reports`** — shareable prose deliverables: reports, BD/prospect
  briefs, summaries read out of context.

The genre skills are thin: each holds only what's specific to its genre and
assumes everything in this core.

Talking with the user in-session isn't a genre — that's the always-on
`writing-conversation`. The craft principles here (plain prose, no AI-ese,
honesty, subtraction) apply to it too; its audience and out-of-context gates do
not, because the user is present and shares your context.

## The overriding principle: make it easy for the reader

Every rule below serves one goal: **spend the reader's effort on your ideas**, not
on parsing your writing. Attention is a fixed budget — whatever they burn
decoding a clumsy sentence or hunting for a source is gone from understanding the
point.

This is what motivates the specifics: structure and dependency order (§3), plain
prose (§4), relentless subtraction (§7), linked claims (§9) — each moves effort
off the reader and onto the writer. When a choice is unclear, pick what costs the
reader less.

## Writing is collaborative — keep the user in the loop

Two things that sound opposed but aren't: the work is **collaborative**, and the
piece is **the user's**. Collaboration is about process — you keep them in the
loop; ownership is about authority — the final say is theirs, not yours. You do
the drafting and the craft; they decide the direction.

So don't disappear and return with a finished draft built on guesses. Involve
them at the decisions that shape the piece — **who it's for** (§1), **the voice
and structure**, and **any rewrite of prose they already wrote** (§2). When a
choice would change its direction, surface it and ask rather than deciding
silently. Drafting freely is fine; deciding *for* them is not.

## Author, then review — one bar, used twice

Every genre skill has an **Authoring** section and a **Review** section built on
the *same* rubric. That is deliberate: the standards you review against are the
standards you write to. Read the review rubric *before* drafting so the rules
are baked in from the start — review is a check that you hit the bar, not a
rescue for having ignored it.

## 1. Confirm the audience before you write

Every other judgment — what to assume, what to cut, how to sequence — is made
relative to one audience. So pin it down *first*: treat confirming it as a **gate**
you clear before drafting prose. Unless the audience is genuinely obvious,
**confirm it with the user** rather than guessing — getting this wrong wastes the
whole draft.

Common audiences and what they change:

- **End users** — "how to use"; hide internals.
- **Contributors** — "how it works"; show internals.
- **Learners / researchers** — "why"; build from first principles.
- **Decision-makers** — "what it does and why it matters."

**Code comments and docstrings** are a special case, outside this gate. They're
part of the code, with a fixed audience (the next developer in this file) and
their own conventions — write them with your normal coding latitude; never stop
to confirm an audience for a docstring while building a codebase.

For **prose**, the gate scales with the cost of guessing wrong:

- **Confirm first** when a standalone piece would be written differently for
  different readers — a doc, a tutorial, a report, a blog post, a README for a new
  project. One line — "who's the reader: end users, contributors, or
  decision-makers?" — saves a whole rewrite.
- **Just proceed** when the reader is obvious or the writing rides along with a
  task the user already scoped: a commit message, a reply in an ongoing thread,
  routine docs generated as part of a build.

Once set, hold the audience constant through every section — drift within a page
is confusing.

### Introduce only what the audience doesn't already know

The audience fixes what you can take for granted, and therefore what you must
introduce before relying on it. Over-explaining what they know wastes attention
and reads as condescending; under-explaining what they don't loses them. This
governs two things:

- **Concepts** — build up an idea, mechanism, or piece of background the audience
  lacks before you lean on it; don't re-derive one they already hold. (At the
  section scale, the same move is *problem before solution* — see `writing-teaching`.)
- **Terms** — define a term this audience won't know the first time you use it. An
  undefined term is one of the easiest ways to lose a reader, who then stalls or
  reads on confused; a term they already know needs no gloss.

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
  "talked in 2024 → churned → fresh pain in 2026" — so every later line lands
  against a frame the reader already has.
- **Order by dependency.** If A references B, define B first. A bare forward
  reference — a "see below", a term used before it exists — is close to
  unacceptable: it forces the reader to hold an undefined thing in mind or go
  hunting, the exact tax this whole skill exists to prevent. The one legitimate
  forward pointer is a *deliberate, signposted* one that answers a question the
  reader is already forming — "wondering how this scales? good instinct — we get
  there in §7." That works because it manages the reader's expectation instead of
  assuming they already have the answer.
- **Order by importance, monotonically.** Within a list or section, let importance
  move one way — build up to the most important, or lead with it and taper — never
  bounce (big, trivial, huge, minor). A human reads in sequence and loses the thread
  when the stakes jump around. You take the whole list in at once, so this is a
  place your own instinct won't warn you: check it deliberately.
- **Keep cross-references monotonic.** When the text points to its own sections,
  they should come up roughly in order. If you catch yourself citing §7 before §3,
  that's a smell the sections themselves are mis-ordered — fix the order, not the
  reference.
- **Write the intro and summary last.** They're easier, and far less vague, once
  the body exists — only then do you know what to introduce and what to sum up.
  Drafting them first produces generic hedging ("this document explores various
  aspects of…") you'll just rewrite.

But the *shape* those primitives take is genre-specific — a teaching narrative
arc, a scannable report, a reference catalog are structured very differently.
Don't force one mold on every piece; the genre skill you loaded defines its shape.

## 4. Write plainly and directly

The default register for all technical writing.

- **Lead with the answer.** No preamble, no wind-up that defers the point ("so
  the first question is…"). The first sentence carries the point.
- **Cut filler and hedging.** "it's worth noting", "in order to", "basically",
  "essentially", "I think", "as we can see" — delete them. One strong sentence
  beats three.
- **Prefer plain words.** "use" not "utilize", "so" not "in order
  to", "helps" not "facilitates". Skip throat-clearing adjectives ("robust",
  "seamless", "powerful", "comprehensive") unless they carry real information.
- **Format visually when it helps.** The layout of the text — bullets, short
  headers, tables — as opposed to §3's organization. Good when it aids scanning;
  reach for it freely. Don't split a single thought across bullets, and don't add
  formatting to padding.
- **Bold a few words.** Not whole sentences — emphasis works by contrast, and a
  fully bolded sentence has no focal point. Bold the two or three words that carry
  the point, or none.
- **Keep parallel things parallel.** Headings at one level, and bullets in one
  list, should share grammatical form — all imperatives, or all noun phrases, not a
  mix. A tense or form swap mid-list is a speed bump the reader feels even if they
  can't name it.

## 5. Avoid AI-ese

The tells that mark writing as machine-generated — empty phrases that carry no
information and erode trust. Cut them wherever they add nothing, which is almost
always. But treat the lists below as *tells, not a banned-words list*: a phrase
that genuinely does work stays. Ban the emptiness, not the word.

Beyond the named tells, one general test catches shapes this list can't
enumerate: does a sentence carry a fact, or only *comment on* the content — how to
feel about it, that it's coming, that it matters? The second kind is the tell.

The shapes it most often takes (the test catches the rest):

- **The regular-beat triad.** Three short parallel phrases restating one idea in
  the same rhythm — "fully net-new, no warm path, straight cold"; "real budget,
  real scale, production reliance." Say it once, with the real fact; vary sentence
  length.
- **"X isn't just Y — it's Z."** And its cousins: "not only… but…", and the plain
  antithesis "A, not B" ("a demo, not a dataset"; "a decision, not a default"). A
  hype frame masquerading as insight. State what X is.
- **Pileups.** Em-dash pileups and adjective stacks. One em-dash per sentence at
  most. Also decorative bold-lead-in stacks — every bullet opening with a bold
  *label* that carries no real content. (A bold *proper-noun name* used as a
  scannable index is different and good — see `writing-reports`.)
- **Editorial fluff / hype conclusions.** Lines that tell the reader how to feel
  or restate the obvious with drama: "getting in front of it is the whole game",
  "the arc is the whole pitch", "make no mistake", "the key thing here". State the
  fact; let the reader draw the conclusion.
- **Promissory framing.** The forward-looking twin of a hype conclusion:
  announcing or labeling what follows instead of just saying it — its importance
  ("the two reasons are worth separating", "here's the subtle part", "the key
  bit"), or its status as a list, aside, or boilerplate ("two things worth
  confirming:", "the one piece of ceremony:"). The frame spends a sentence to add
  nothing; a reader judges importance from the content. State the thing; if it
  matters, that shows.
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
  roughly by leverage", "verified against X". The reader wants findings, not how they
  were made.
- **No prior-draft references.** "we cross-checked and the picture changed", "as
  discussed", "now updated to". A reader only sees the doc as
  it is; references to earlier state are noise.
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
prefer the cut — unless what's being compressed is the claim the piece exists to
make. Brevity is not the goal, though — low reader effort is. Cut what doesn't
serve the reader; keep (and make explicit) what does.

**Proportion space to load.** The claim a piece exists to make earns more room
than the detail supporting it. Terseness is a default, not a quota — when the one
idea the reader came for is compressed into a subordinate clause, they read
straight past it. Before cutting, find the sentence that carries the piece; state
it plainly, on its own, with its consequence made concrete. Cut around it, not
into it.

## 8. Verify before you write it

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
  blue text is as hard to read as one with no links — over-linking taxes the
  reader like any other clutter.
- **Cite with a compact trailing link**, not a whole-sentence hyperlink — whole-phrase
  links bleed together and kill scanning.
  - Bad: `They [reproduced corruption in production](url) and [worked around it](url).`
  - Good: `They reproduced corruption in production ([#304](url)) and worked around
    it with a per-store lock ([#158](url)).`
- **Reference code at the line level** — permalinks to specific lines, not just
  files. Show both the problem location and the fix.
- **Never invent a URL.** If a claim can't be sourced, cut it or flag it — don't
  fabricate a link.
