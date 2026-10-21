---
kind: primary
result: achieved
routes:
  web: Web
steps:
  - text: Clears the bed and presses Bed cleared → next on that printer's lane
    kind: actor
    capability: clear-bed
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product hands back the next planned copy, names the spools to mount and asks to set it up
    kind: product
    capability: clear-bed
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - File
          - Remaining
      - entity: spool
        effect: reads
        facts:
          - Color name
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: Mounts the spools and confirms
    kind: actor
    capability: clear-bed
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product selects the file on the Dash beside that printer's card
    kind: product
    capability: clear-bed
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
  - text: Checks the head for each color and presses Print
    kind: actor
    capability: print-file
    actor: farm-operator
    entities:
      - entity: head
        effect: reads
        facts:
          - Number
          - Loaded color
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product sends and starts the file, and Dispatch holds the copy as starting on that printer
    kind: product
    capability: print-file
    actor: farm-operator
    entities:
      - entity: printer-file
        effect: creates
        facts:
          - Name
          - Size
          - Modified
      - entity: printer
        effect: reads
        facts:
          - Print state
      - entity: job
        effect: changes
        facts:
          - Starting on
    contexts:
      web:
        place: hub::dashboard::dash
---

# From a cleared bed to the next print

## Trigger

A planned print came off the bed.

## Outcome

The next copy is printing and the plan shows it running.
