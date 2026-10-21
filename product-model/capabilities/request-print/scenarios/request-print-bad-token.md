---
kind: validation
routes:
  api: API
steps:
  - text: Posts a model marked for print with a wrong or missing token
    kind: actor
    actor: 3mf-explorer
    entities:
      - entity: model
        effect: reads
        facts: []
    contexts:
      api:
        place: print-request-api
  - text: The Product refuses the request
    kind: product
    actor: 3mf-explorer
    entities: []
    contexts:
      api:
        place: print-request-api
---

# A request without the pairing token

## Trigger

3MF Explorer was paired with another Hub, or not at all.

## Outcome

No request is filed; pairing again with the token from the Folder panel fixes it.
