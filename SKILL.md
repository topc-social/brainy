---
name: brainy
description: Reads and writes an entity's brain, its long-term memory in Basic Memory (one project per entity: a company, a product, a person, a family). Use before answering a question about what the entity has decided, is, has or does, and whenever a session settles a new fact or decision about it, or finds that a known fact changed. Not for notes that only matter to the current session.
---

# Brainy: one memory per entity, kept true

Each entity gets its own brain: a Basic Memory project named after it (`acme`, `my-family`). Read it before answering from scattered files, and keep it true as you work. Why it's written this way: the eval in this repo's README.

## Reading

- Search facts, not whole notes: `bm_search` with `items: ["observation"]` on the entity's project. Long notes drown out whole-note search.
- Prefer `#current` facts. A `#replaced` fact is history: use it only when the question is about the past ("what did we think in October?").
- Say where an answer came from: the fact's date and source.
- Nothing found? Say so, then fall back to other docs. Don't guess.

## Writing

**One note per thing.** A thing is anything with properties: a project, a person, a product, a rule area. Folder `things/`. Title = the thing's plain name. Decisions can live as their own source notes (`decisions/`) that things link to.

**One fact per line**, as a Basic Memory observation:

```
- [property] value (since YYYY-MM-DD, source <link or [[note]]>) #current
```

- The property is short and specific (`focus`, `price`, `how work is handed in`).
- Every fact has a date and a source: a decision note, an issue, a PR, a doc, or "<who> in chat" with the date. No source, no fact.

**When a value changes**, edit the old line, never delete it:

```
- [focus] validation tool (from 2026-10-10, source …) #replaced, now: distribution only (2026-11-12)
- [focus] distribution only (since 2026-11-12, source …) #current
```

Only mark a fact replaced when the new one is clearly about **the same thing and the same property**. A newer fact about a different thing (another list, another product, another lens) gets its own, more specific note or property, and both stay current. Getting this wrong was the main error in the eval.

**Links** go under `## Relations`: `- part_of [[Acme]]`, `- has_product [[Widget]]`.

## When

- A session settles a decision or a fact about the entity: write it before the session ends.
- You notice a fact in the brain is wrong or stale: fix it as above, with the new source.
- Keep each brain to one entity. Facts about someone's private life don't go in a company's brain.
