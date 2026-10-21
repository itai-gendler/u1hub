---
kind: primary
routes:
  api: API
steps:
  - text: Posts a model marked for print, with its path and the pairing token
    kind: actor
    actor: 3mf-explorer
    entities:
      - entity: model
        effect: reads
        facts:
          - File
    contexts:
      api:
        place: print-request-api
  - text: The Product finds the model by its place inside the models folder, whatever drive letter or network path 3MF Explorer used
    kind: product
    actor: 3mf-explorer
    entities:
      - entity: model
        effect: reads
        facts:
          - File
          - Designer
          - Name
      - entity: models-settings
        effect: reads
        facts:
          - Models folder
    contexts:
      api:
        place: print-request-api
  - text: It files the request under Requested on the Models tab
    kind: product
    actor: 3mf-explorer
    entities:
      - entity: print-request
        effect: creates
        to: Requested
        facts:
          - Model file
          - Designer
          - Title
          - Requested at
      - entity: model
        effect: reads
        facts: []
    contexts:
      api:
        place: print-request-api
---

# File a request for a model not yet sliced

## Trigger

Someone browsing 3MF Explorer presses Mark for print.

## Outcome

The model shows as requested on the Models tab, waiting for its gcode.

## Edge cases

- The same file marked again after it moved replaces the request filed under its old place.
