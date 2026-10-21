---
kind: primary
routes:
  web: Web
steps:
  - text: Opens Folder, sets the models folder, the Orca location or the U1 template, and saves
    kind: actor
    actor: farm-operator
    entities:
      - entity: models-settings
        effect: reads
        facts:
          - Models folder
          - Orca location
          - U1 template
      - entity: model
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product keeps them, says whether each was found, and rescans the shelf
    kind: product
    actor: farm-operator
    entities:
      - entity: models-settings
        effect: changes
        facts:
          - Models folder
          - Orca location
          - U1 template
    contexts:
      web:
        place: hub::dashboard::models
---

# Point the shelf at a folder

## Trigger

The model library lives on a network share.

## Outcome

The shelf reads the new folder.

## Edge cases

- A blank field keeps what was set rather than clearing it.
