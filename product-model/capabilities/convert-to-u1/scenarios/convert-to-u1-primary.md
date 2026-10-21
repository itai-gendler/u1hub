---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Convert to U1 on a model card
    kind: actor
    actor: farm-operator
    entities:
      - entity: model
        as: original
        effect: reads
        facts:
          - File
          - Name
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product writes the project as a U1 copy named with (U1) beside the original, taking the U1 machine and filament presets from the U1 template
    kind: product
    actor: farm-operator
    entities:
      - entity: models-settings
        effect: reads
        facts:
          - U1 template
      - entity: model
        effect: creates
        facts:
          - File
          - Designer
          - Name
          - Size
          - Added
        as: copy
      - entity: model
        as: original
        effect: reads
        facts:
          - File
    contexts:
      web:
        place: hub::dashboard::models
  - text: It lists which settings were kept, which were changed and which could not be carried
    kind: product
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::models
---

# Make a U1 copy of a Bambu project

## Trigger

A downloaded project is set up for another printer.

## Outcome

The U1 copy is on the shelf next to the original, with the original's designer; the original is never touched.
