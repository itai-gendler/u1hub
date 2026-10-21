---
kind: edge
routes:
  web: Web
steps:
  - text: Ticks In-app slicing
    kind: actor
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: reads
        facts:
          - Features
    contexts:
      web:
        place: hub::dashboard::settings
  - text: The Product warns that in-app slicing is not ready and asks whether to enable it anyway, unticking it if not
    kind: product
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::settings
---

# Turn on in-app slicing

## Trigger

Someone explores Settings.

## Outcome

Nobody turns it on without being told first.
