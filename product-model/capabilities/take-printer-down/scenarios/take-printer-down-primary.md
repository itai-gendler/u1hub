---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Take this printer down for maintenance on its lane
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product marks the printer down, keeping when it went down
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: changes
        from: In service
        to: Down for maintenance
        facts:
          - Down since
          - Maintenance note
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: It replans from scratch so the printer's share of the queue goes to the others; pins to it wait for its return
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - Pinned printer
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Logbook opens an outage entry for the printer
    kind: product
    actor: farm-operator
    entities:
      - entity: logbook-entry
        effect: creates
        facts:
          - Printer name
          - Kind
          - What happened
          - When
          - Print hours
          - Source
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::logbook
---

# Route work around a printer under repair

## Trigger

A printer's extruder is being rebuilt.

## Outcome

The printer's card and lane say down for maintenance, a print already on its bed is left alone, and the rest of the farm has its work.

## Edge cases

- Print on best printer and claim running prints skip a printer that is down.
