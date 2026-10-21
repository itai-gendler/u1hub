---
kind: primary
routes:
  web: Web
steps:
  - text: Opens a spool's card, picks a printer's head and presses Load here
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Color name
          - Loaded in
      - entity: printer
        effect: reads
        facts:
          - Name
      - entity: head
        effect: reads
        facts:
          - Number
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product records the spool in that head
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: changes
        from: On the shelf
        to: Loaded
        facts:
          - Loaded in
      - entity: head
        effect: reads
        facts:
          - Number
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
---

# Record where a roll went

## Trigger

A roll was mounted on a printer.

## Outcome

The spool shows as loaded in that head; deductions and the AI pre-flight read it from there.

## Edge cases

- A spool already loaded elsewhere moves: a roll is in one place at a time.
- A head number beyond what the printer reports is refused.
