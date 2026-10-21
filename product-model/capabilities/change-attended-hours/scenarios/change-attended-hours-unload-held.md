---
kind: edge
routes:
  web: Web
steps:
  - text: Opens the When a print finishes choice
    kind: actor
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: reads
        facts:
          - When a print finishes
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: Unloading after prints is paused while nozzle clogs are investigated
    kind: condition
    entities: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product keeps every roll loaded and says why the other choices are held
    kind: product
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: reads
        facts:
          - When a print finishes
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# The unload setting is held

## Trigger

The operator wants rolls unloaded after each print.

## Outcome

Every roll stays loaded for now.
