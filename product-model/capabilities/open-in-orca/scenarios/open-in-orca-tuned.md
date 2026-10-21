---
kind: alternate
routes:
  web: Web
steps:
  - text: Presses Open in Orca with these settings under a settings suggestion
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
  - text: The Product writes a scratch copy of the project with the suggested values filled in as changes, converting a project for another printer to U1 first; the library file is never written
    kind: product
    actor: farm-operator
    entities:
      - entity: model
        effect: reads
        facts:
          - File
      - entity: models-settings
        effect: reads
        facts:
          - U1 template
      - entity: library-file
        effect: reads
        facts: []
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::models
  - text: It launches Orca with the copy and watches the gcode folder
    kind: product
    actor: farm-operator
    entities:
      - entity: orca-session
        effect: creates
        to: Watching
        facts:
          - Model file
          - Opened at
          - Tuned copy
    contexts:
      web:
        place: hub::dashboard::models
---

# Open with the suggested settings

## Trigger

The operator wants to start from Claude's suggestion.

## Outcome

Orca opens with the suggestions marked as changes, each one easy to put back; the scratch copy cleans itself up after three days unless kept with Save As.

## Edge cases

- The suggestion on screen is the one loaded, never a fresh ask.
