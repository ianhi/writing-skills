---
name: writing-teaching
description: Write and review teaching material — tutorials, teaching notebooks, explanatory blog posts, workshop content — so it actually teaches. Load writing-core first; this adds the pedagogy rubric (problem before solution, one running example, cognitive load, correctness). Use when authoring or reviewing anything whose job is to teach a concept, or when asked for a "pedagogy review" / "does this teach well?". To run a review, use writing-review.
---

# Writing Teaching

Material whose job is to *teach* — tutorials, teaching notebooks, explanatory
posts, workshops. **Load `writing-core` first**; this adds the pedagogy-specific
rubric and review workflow.

## Guiding principles

The reader's attention is the scarce resource. On top of core:

- **Meet the reader where they are.** Every judgment is made against a specific
  audience (core §1).
- **Subtract to perfect** (core §7). Most teaching material improves by removal.
- **Comprehension beats coverage.** It is more valuable to understand *all* of a
  slightly incomplete tutorial than 50% of a rigorously complete one. When
  completeness or precision fights understanding, understanding wins — but never
  teach a wrong mental model; a clearly-flagged simplification is a feature.
- **Do the reader's work for them.** Never make the reader derive what you can
  state — the intermediate value, why this follows, the name of the thing.
  Implicit-but-guessable is a tax; spend their attention on the lesson, not the
  plumbing.
- **Sequence deliberately.** Order is a teaching instrument. Each idea lands only
  after its prerequisites; each section raises the question the next answers. When
  something reads as confusing, suspect the ordering before the wording.

## Tell a story — And-But-Therefore

Core §3 gives the structural skeleton; teaching and blog writing need a *narrative*
on top of it, because a story holds attention where a flat sequence of facts loses
it. The simplest reliable shape is **And-But-Therefore (ABT)**: setup (*and*) →
complication (*but*) → resolution (*therefore*).

> The store worked AND it scaled fine, BUT concurrent writes corrupted it,
> THEREFORE we added a per-store lock.

The *but* is the engine. A piece that is all "and… and… and…" is a list, not a
story — find the real tension and put it at the center. This is why rubric A leads
with *problem before solution*: the problem is the "but."

## The rubric (A–F)

Author to this; review against it.

### A. Motivation & narrative
1. **Problem before solution** — every mechanism is preceded by a *concrete*
   example of what fails without it. "A mouse brain is ~an exabyte — you can't
   store the labels" beats "useful for large data."
2. **Introduce before use** — no concept, function, or term used before it's
   introduced. Prefer **works-then-breaks** ordering — show it working, then expose
   where it fails.
3. **Each section answers the previous section's question** — flag orphaned sections.
4. **Start with the destination** (core §3) — the top motivates the whole doc;
   bookends written last.
5. **Order by dependency** (core §3) — no forward references.

### B. The running example
6. **Thread one example, laddering up** — the same scenario carries across
   sections, each step *continuing* the last and adding *exactly one* new concept
   (1-D → 2-D → nonlinear). Flag steps that introduce two ideas at once or reset to
   a fresh unrelated toy.
7. **Ground in the real & named** — anchor abstractions in a concrete, real-world,
   named phenomenon (heat on a metal ring, brain slices, a fisheye lens), ideally
   with a citation.
8. **Data embodies the lesson** — the toy data physically demonstrates the point
   (put the hot spot *on the seam* so the seam problem is visible).

### C. Cognitive load & altitude
9. **Only what they need** — show the essential; hide/pre-fill boilerplate. In
   exercises, blank *only the core method*; provide the plumbing.
10. **The teaching line is the star** — setup/plotting must not bury the one line
    that shows the concept. `hide-input` for figure-only cells.
11. **One idea per cell/paragraph.**
12. **Distinguish near-neighbors** — when two mechanisms look similar, state the
    distinction and when to use each.

### D. Signposting & structure
13. **Numbered, hierarchical headings** — number sections and nest sub-examples so
    the reader always knows where they are in the sequence: which step they're on,
    and how many there are in all. Give the progression an explicit name so they see
    the whole arc ("1-D → 2-D → nonlinear"), not just the current step.
14. **Scope notes** — a page covering part of a system says so up top.
15. **Crosslinks** (core §9) — terms link out; complementary sections link both ways.

### E. Correctness & integrity
> Judged through the lens of *comprehension beats coverage*: a wrong mental model
> is always a finding, but a deliberate, clearly-signposted simplification is not.
16. **Claims match reality** — for notebooks, confirmed by a cell's actual output;
    for prose, by a worked example or verifiable fact.
17. **Accurate references** — citations and attributions correct, not guessed.
18. **Deterministic, transparent examples** — no hidden randomness or lucky search
    (`for _ in range(500): if ...: break`); pick the illustrative case directly.
19. **Show, don't tell** — claims are demonstrated, and each demo ends with the
    takeaway.

### F. Prose
20. **Concision** (core §4) — cut filler and hedging.
21. **Consistency** — terminology, notation, capitalization, identifier formatting.
22. **Respect the author's voice** (core §2) — suggest, don't replace fleshed prose.

## Review

Run a review with `writing-review` — it owns the mechanism (dispatch the subagent,
fan out, rank, apply). It grades against the A–F rubric and Guiding Principles
above, plus `writing-core`, for the piece's audience and doc type. Teaching-specific
notes for that review:

- **Ranking** — by teaching impact; a broken mental model outranks a wording nit.
- **Notebooks** — read cells via the Jupyter MCP *with outputs*, so rubric 16
  (claims match reality) is checked against what the cell actually produced.
- **Notebook fixes** — edit in place via the Jupyter MCP, never regenerate the
  `.ipynb`, and keep the build green (`nbconvert --execute`).
