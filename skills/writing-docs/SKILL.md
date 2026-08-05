---
name: writing-docs
description: Write and review user-facing documentation — how-to guides, conceptual explanations, API/reference docs, READMEs, contributor guides, design docs. Load writing-core first for the shared foundation; this adds what's specific to documentation: completeness, dependency ordering, consistent format, scope notes, and code/prose integration. Use when authoring or editing docs, or when asked to make docs clearer or better structured. Step-by-step lessons that teach a concept are writing-teaching.
---

# Writing Docs

User-facing documentation — the guides and explanations people read to understand
and use a system, plus the reference material they consult. **Load `writing-core`
first**; this skill adds only what's specific to documentation.

Lead with the *understanding-oriented* docs — how-to guides and conceptual
explanations. Those carry the most weight; reference material (API docs, config
keys) is more formulaic, mostly completeness and consistent format. Step-by-step
lessons that *teach a concept* to a newcomer are `writing-teaching`, not here: the
line is the job. Teaching walks a learner from zero to a mental model; docs serve
a user who already has context and needs to understand or do one specific thing.

Doc types and their key concern:

| Type | Key concern |
|------|-------------|
| Explanation / concept guide | The right mental model, motivated before detail |
| How-to guide | A concrete goal, reached in ordered steps |
| Reference docs | Completeness, consistent format, dependency ordering |
| Contributor guide | Internals focus, verified claims, the "why" behind decisions |
| README | Fast orientation: what it is, why, how to start — in that order |
| Design doc | The problem and the decision; alternatives considered and why not |
| Research notebook | Reference kept separate from experiments, each part labeled |

## Authoring

Everything in `writing-core` applies. The doc-specific additions:

- **Scope notes.** When a page covers only part of a system, say so up top: "This
  page covers types persisted to storage. For in-memory types, see session.md."
- **No speculation about design rationale.** If you can't find why a decision was
  made in the source or its history, don't invent one — flag it as an open
  question (core §8). It's the most common docs failure.
- **Separate reference from exploration.** Don't mix spec/definition content with
  experiments or exploratory work on one page. If a page has both, split them:
  reference at the top, exploration below, each clearly labeled.
- **Consistent format across entries.** Reference entries (functions, config
  keys, endpoints) follow the same template in the same order every time, so the
  reader learns the shape once and scans the rest.
- **Order by dependency, completely.** Reference docs must define before use with
  no forward references — a reader landing mid-page should never hit an undefined
  term.
- **Hide boilerplate.** In examples, show the lines that demonstrate the API; elide
  setup/ceremony. For notebooks, `hide-input` on figure-only cells.
- **Keep diagrams true, not complete.** A *wrong* diagram teaches a wrong mental
  model and is always a defect: verify every node and edge against the actual code.
  Comprehension is the bar, not coverage — a simpler diagram that omits detail is
  fine when it stays true and the omission is signposted. Prefer fewer nodes with
  clear labels over architectural completeness, and use sequential panels for a
  process rather than one dense end-state diagram.
- **Pre-compute outputs for static builds.** For Jupyter Book / Sphinx renders,
  all outputs must be saved in the `.ipynb` (`jupyter execute --inplace`); empty
  outputs won't render.
- **Give images alt text** that describes what they show, so the doc works for
  screen readers and when images fail to load.

### Linking between pages

Core §9 covers sourcing claims. Documentation adds linking the docs together:

- **Link everything linkable.** Language concepts → language docs; domain terms →
  an authoritative reference; internal types → sibling pages or anchors.
- **Symmetric and prominent.** When two pages are complementary, both link to the
  other, near the top (a callout), not buried mid-paragraph.

## Review

Run a review with `writing-review` — it owns the mechanism (dispatch the subagent,
fan out, rank, apply). Grade against `writing-core` and the checklist below, for
the doc's audience and type. Skim as the target reader, then check:

- **Scope** — is it clear at the top what the doc covers and what it doesn't?
- **Orientation** — from the opening alone, can a newcomer tell what this is and
  how to get started?
- **Forward references** — any term used before it's defined? Any "see below"?
- **Audience consistency** — does any section drift to a different reader (§1)?
- **Tone & substance** — do the depth and register match the audience (§1)?
- **Format consistency** — do like entries share a template?
- **Verified claims** — is every behavioral assertion backed by a run/test/example
  (§8)? Any invented rationale?
- **Crosslinks** — do claims carry source links (§9), and do terms and
  complementary pages link out both ways (Linking between pages, above)?
- **Diagrams** — verified against source, and simple enough to grasp at a glance?
