---
kind: primary
routes:
  web: Web
steps:
  - text: With a file selected, picks the printer it is going to and presses AI pre-flight
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
  - text: >-
      The Product writes a brief of a few thousand characters: the file name, the slicer settings in the file, the filaments it was sliced for, its objects, and what is recorded in that printer's
      heads
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
          - Material
      - entity: spool
        effect: reads
        facts:
          - Material
          - Hot end temperature
          - Bed temperature
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: It sends the brief to Claude with the operator's key, on Sonnet, Haiku or Opus as chosen
    kind: product
    actor: farm-operator
    entities:
      - entity: ai-settings
        effect: reads
        facts:
          - Anthropic API key
          - Claude model
    contexts:
      web:
        place: hub::dashboard::dash
  - text: It shows GO, CHECK or STOP and the reasons, most important first, with what the answer cost
    kind: product
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dash
---

# Get GO, CHECK or STOP

## Trigger

A file is about to go to a printer and a second pair of eyes is wanted.

## Outcome

The verdict is on the card: a wrong material or temperature for a head, an empty head a color needs, a missing prime tower or a wrong bed temperature is called out before printing.

## Edge cases

- Never the gcode itself, the meshes or the printers' addresses are sent.
- Only one review runs at a time.
