---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Turn on beside the affiliate note, or ticks the box in Settings
    kind: actor
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: reads
        facts:
          - Affiliate links
    contexts:
      web:
        place: hub::dashboard::resources
  - text: The Product adds the tag to Amazon links again
    kind: product
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: changes
        facts:
          - Affiliate links
    contexts:
      web:
        place: hub::dashboard::resources
---

# Support the project again

## Trigger

The operator wants purchases to support the creator.

## Outcome

Amazon links carry the tag, and the disclosure shows where they do.
