---
kind: alternate
routes:
  web: Web
steps:
  - text: Holds a spool's tag to the phone, or types its number and presses Look up
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: No spool carries the tag
    kind: condition
    entities:
      - entity: spool
        effect: reads
        facts:
          - Tags
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product says it is a new tag and opens the bind panel with the tag filled in
    kind: product
    actor: farm-operator
    entities:
      - entity: filament-library
        effect: reads
        facts:
          - Swatches
    contexts:
      web:
        place: hub::dashboard::spools
---

# Tap a tag the Hub has never seen

## Trigger

A new roll arrives with a tag.

## Outcome

The operator is in the bind panel, one step from giving the roll an identity.
