---
kind: edge
routes:
  api: API
steps:
  - text: Asks the health address
    kind: actor
    actor: watchdog
    entities: []
    contexts:
      api:
        place: health-check
  - text: The Hub has not started listening yet
    kind: condition
    entities: []
    contexts:
      api:
        place: health-check
  - text: The Product answers that it is still booting
    kind: product
    actor: watchdog
    entities: []
    contexts:
      api:
        place: health-check
---

# Still starting

## Trigger

The Hub just restarted.

## Outcome

The monitor sees not-ready rather than up.
