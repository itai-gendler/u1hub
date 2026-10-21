---
kind: edge
routes:
  web: Web
steps:
  - text: Presses Save
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::settings
  - text: The settings file cannot be written, such as on a busy network share
    kind: condition
    entities: []
    contexts:
      web:
        place: hub::dashboard::settings
  - text: The Product says the settings could not be saved and why, instead of showing Saved
    kind: product
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: reads
        facts:
          - G-code folder
    contexts:
      web:
        place: hub::dashboard::settings
---

# A save that cannot be written

## Trigger

The share hiccups.

## Outcome

The operator knows nothing changed.
