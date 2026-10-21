---
kind: primary
routes:
  web: Web
steps:
  - text: With a file selected, picks a head for each color on an idle printer's card and presses Print
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
          - Print state
      - entity: head
        effect: reads
        facts:
          - Number
          - Loaded color
          - Material
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product sends the file with a live progress bar
    kind: product
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
      - entity: printer-file
        effect: creates
        facts:
          - Name
          - Size
          - Modified
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: It sets the head mapping and starts the print
    kind: product
    actor: farm-operator
    entities:
      - entity: head
        effect: reads
        facts:
          - Number
      - entity: printer
        effect: reads
        facts:
          - Print state
    contexts:
      web:
        place: hub::dashboard::dash
  - text: It checks the file's first entry off Up next
    kind: product
    actor: farm-operator
    entities:
      - entity: queue-entry
        effect: removes
    contexts:
      web:
        place: hub::dashboard::files
  - text: A queued Dispatch job for the same file is held as starting on that printer, so no other printer is handed the same copy
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: changes
        facts:
          - Starting on
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
---

# Send and start a file

## Trigger

A printer is free and the right colors are loaded.

## Outcome

The printer is printing the file with the chosen heads, Up next no longer lists it, and its card shows the progress.

## Edge cases

- Two colors of the file that are the same color may share one head, so a four-color file can print from three rolls.
