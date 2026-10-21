---
kind: primary
routes:
  web: Web
steps:
  - text: Opens Match and taps a printer
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
      - entity: head
        effect: reads
        facts:
          - Loaded color
    contexts:
      web:
        place: hub::dashboard::match
  - text: The Product lists the library files whose colors that printer's heads cover at least half of, best coverage first, the top five until Show all
    kind: product
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
          - Colors needed
      - entity: head
        effect: reads
        facts:
          - Loaded color
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::match
  - text: Presses Print on a file
    kind: actor
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::match
  - text: The Product selects the file on the Dash and scrolls to that printer's card, so the mapping is confirmed there
    kind: product
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
---

# Print something with what is loaded

## Trigger

A printer is free and nobody wants to swap rolls.

## Outcome

The file is selected on the Dash beside that printer's card, ready for Print; nothing starts without that tap.
