---
domain: dispatch
relations:
  - entity: job
    verb: groups
    cardinality: one-to-many
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#pruneBundles
---

# Bundle

Several plates that are one thing to deliver, such as a body and a head, planned as one deadline.

## Information kept

- **Name** — The bundle's name, or the first file's name plus how many more.
- **Deadline** — Applies to every job in it, unless a job's own deadline is earlier.
