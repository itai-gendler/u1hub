---
kind: alternate
routes:
  web: Web
steps:
  - text: Presses Open in Orca on a model card
    kind: actor
    actor: farm-operator
    entities:
      - entity: model
        effect: reads
        facts:
          - File
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product launches Orca and watches the gcode folder
    kind: product
    actor: farm-operator
    entities:
      - entity: orca-session
        effect: creates
        to: Watching
        facts:
          - Model file
          - Opened at
    contexts:
      web:
        place: hub::dashboard::models
  - text: Gcode files change in the folder but none matches the model's title
    kind: condition
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
      - entity: model
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product links the first one, marked unverified on the card so Link gcode can correct it
    kind: product
    actor: farm-operator
    entities:
      - entity: orca-session
        effect: changes
        from: Watching
        to: Saved
        facts:
          - Saved gcode
          - Verified
      - entity: library-file
        effect: changes
        facts:
          - Linked model
          - Link verified
    contexts:
      web:
        place: hub::dashboard::models
---

# A gcode that does not match by title

## Trigger

Two slices land in the folder at the same time, or the gcode was given another name.

## Outcome

The link is there but flagged as a guess.
