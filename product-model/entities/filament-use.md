---
domain: spools
relations:
  - entity: spool
    verb: takes grams from
    cardinality: many-to-many
references:
  - kind: code
    role: implementation
    target: modules/resources.js#register
---

# Filament use

The grams one finished print took off the rolls in the heads that printed it, listed under Filament used by finished prints with an Undo.

## Information kept

- **Printer** — The printer that finished.
- **File** — The file it printed.
- **Finished** — When the print finished.
- **Grams per roll** — For each roll: grams taken, and its grams before and after; a roll that reaches zero is marked empty.
- **Cost** — What the grams cost at each roll's price; partial when some rolls have no price.
- **Spoolman status** — For imported rolls with write-back on: in Spoolman, waiting, or taken back out.

## States

### Deducted

The grams are off the rolls.

### Undone

The grams were put back; the record stays.
