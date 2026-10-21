---
kind: validation
routes:
  api: API
steps:
  - text: Posts a model marked for print
    kind: actor
    actor: 3mf-explorer
    entities:
      - entity: model
        effect: reads
        facts: []
    contexts:
      api:
        place: print-request-api
  - text: No file under the models folder matches the path
    kind: condition
    entities:
      - entity: models-settings
        effect: reads
        facts:
          - Models folder
      - entity: model
        effect: reads
        facts: []
    contexts:
      api:
        place: print-request-api
  - text: The Product refuses and names the folder it reads
    kind: product
    actor: 3mf-explorer
    entities: []
    contexts:
      api:
        place: print-request-api
---

# A model outside this Hub's folder

## Trigger

The two apps look at different libraries.

## Outcome

No request is filed, and 3MF Explorer is told which folder this Hub reads.
