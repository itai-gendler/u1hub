---
kind: edge
routes:
  web: Web
steps:
  - text: With a file selected, presses Print on best printer
    kind: actor
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Colors needed
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product names the printer and counts down five seconds
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: When the countdown ends the printer is no longer idle, or is no longer the best match
    kind: condition
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
      - entity: head
        effect: reads
        facts:
          - Loaded color
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product sends nothing and says why, naming the new best printer when there is one
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
---

# The printer changes during the countdown

## Trigger

Someone started a print on that printer or swapped a roll while the countdown ran.

## Outcome

No file is sent to a printer that changed under the countdown.
