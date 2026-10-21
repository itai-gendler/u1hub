---
kind: primary
routes:
  web: Web
steps:
  - text: With a file selected, picks a head for each color on an idle printer's card and presses Upload
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
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product sends the file to the printer with a live progress bar
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
  - text: It sets the printer's mapping from each file color to the chosen head
    kind: product
    actor: farm-operator
    entities:
      - entity: head
        effect: reads
        facts:
          - Number
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
---

# Send a file without starting it

## Trigger

The file should be ready on the machine, to start later from the touchscreen.

## Outcome

The file is on the printer's storage with its heads mapped; nothing has started and Up next is unchanged.
