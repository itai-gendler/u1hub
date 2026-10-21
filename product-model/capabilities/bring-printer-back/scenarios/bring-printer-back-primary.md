---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Bring this printer back into service on its lane
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
          - Down since
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product marks the printer in service and replans so queued work spreads back onto it
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: changes
        from: Down for maintenance
        to: In service
        facts:
          - Down since
          - Maintenance note
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Logbook closes the outage entry and asks what fixed it
    kind: product
    actor: farm-operator
    entities:
      - entity: logbook-entry
        effect: changes
        facts:
          - Back in service
    contexts:
      web:
        place: hub::dashboard::logbook
---

# Put a repaired printer back to work

## Trigger

The repair is done.

## Outcome

The printer takes work again at once, rather than sitting idle beside a queue it could help with.
