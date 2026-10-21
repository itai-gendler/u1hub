---
kind: primary
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
          - Name
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product launches Snapmaker Orca with the file and starts watching the gcode folder
    kind: product
    actor: farm-operator
    entities:
      - entity: orca-session
        effect: creates
        to: Watching
        facts:
          - Model file
          - Opened at
      - entity: models-settings
        effect: reads
        facts:
          - Orca location
    contexts:
      web:
        place: hub::dashboard::models
  - text: Orca saves a gcode whose title, ignoring the designer, matches the model's
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
  - text: The Product links the gcode to the model and offers to select it or send it to Dispatch
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
      - entity: model
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::models
---

# Slice a model and catch the gcode

## Trigger

A model is ready to slice.

## Outcome

The saved gcode sits under Opened in Orca with Select and Send to Dispatch; the line goes away once the file is in Dispatch, and the model's printed count will include its prints.
