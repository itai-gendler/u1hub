---
kind: alternate
routes:
  web: Web
steps:
  - text: Presses Rescan
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product walks the models folder again in the background while the shelf holds still and only the count line moves
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
          - Models folder
    contexts:
      web:
        place: hub::dashboard::models
---

# Rescan the folder

## Trigger

Files were added outside the Hub.

## Outcome

New files appear once the walk finishes, with no flashing or jumping on the way.
