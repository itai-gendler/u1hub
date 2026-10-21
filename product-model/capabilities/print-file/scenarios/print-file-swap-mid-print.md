---
kind: alternate
routes:
  web: Web
steps:
  - text: With a five-color file selected, maps two different colors to the same head on an idle printer's card and presses Print
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
  - text: The file carries a filament-change pause (M600 or PAUSE)
    kind: condition
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Colors needed
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product names the head, its two colors and how many pauses the file has, and asks whether to send anyway
    kind: product
    actor: farm-operator
    entities:
      - entity: head
        effect: reads
        facts:
          - Number
      - entity: library-file
        effect: reads
        facts:
          - Colors needed
    contexts:
      web:
        place: hub::dashboard::dash
  - text: Confirms
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product sends the file, sets the mapping and starts the print
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
---

# Print more colors than heads with a pause to swap

## Trigger

A file needs one more color than there are heads, and the slicer put a pause where the roll is swapped.

## Outcome

The print starts; when the printer stops at the pause, the roll on that head is swapped by hand.
