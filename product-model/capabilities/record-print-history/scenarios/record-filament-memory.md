---
kind: alternate
routes:
  web: Web
steps:
  - text: A print the Hub saw start completes, its file is in the library and spools are recorded in its heads
    kind: condition
    unattended: true
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
      - entity: spool
        effect: reads
        facts:
          - Loaded in
      - entity: head
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product remembers which spool was in each head for that file's content
    kind: product
    entities:
      - entity: filament-memory
        effect: creates
        facts:
          - File
          - Printed
          - Spools used
      - entity: spool
        effect: reads
        facts: []
      - entity: head
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
---

# A print finishes with spools recorded

## Trigger

A print the Hub watched start comes to an end.

## Outcome

The next time the same file is selected, last time's spools are offered.
