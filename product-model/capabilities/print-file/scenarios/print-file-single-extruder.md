---
kind: edge
routes:
  web: Web
steps:
  - text: With a file selected, presses Print on a printer's card
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The file is multi-color or Full Spectrum and the printer reports a single extruder
    kind: condition
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
  - text: The Product warns that it will likely fail or print wrong and asks whether to send anyway
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
  - text: Confirms
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product sends and starts the file
    kind: product
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
    contexts:
      web:
        place: hub::dashboard::dash
---

# Confirm a multi-color file on a single-extruder printer

## Trigger

A file landed in the wrong type's folder, or the printer is a single-extruder machine.

## Outcome

The print starts only because a person said so after the warning.

## Edge cases

- A single-color file sent to a four-head printer gets a note that any one loaded head can print it.
