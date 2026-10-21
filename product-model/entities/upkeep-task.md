---
domain: logbook
relations:
  - entity: printer
    verb: is scheduled for
    cardinality: many-to-many
references:
  - kind: code
    role: implementation
    target: modules/logbook.js#dueOf
  - kind: code
    role: implementation
    target: modules/logbook.js#appliesTo
---

# Upkeep task

Upkeep that comes round again on the Logbook's schedule: every so many print hours, every so many days, or both, whichever runs out first.

## Information kept

- **Task** — What to do, such as lubricating the rods.
- **Printers** — One printer, or all of them.
- **Every print hours** — The interval in print hours.
- **Every days** — The interval in days.
- **Notes** — Free notes.
- **Last done** — For each printer: when it was last done and at how many print hours.
- **Due** — For each printer: OK, soon (85 percent of the interval used), due, or unknown until its hours are read.
