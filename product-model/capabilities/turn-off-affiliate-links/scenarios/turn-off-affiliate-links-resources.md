---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Turn off beside the affiliate note at the bottom of Resources
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
  - text: The Product stops adding the tag to any link
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

# Turn the tag off from Resources

## Trigger

The operator prefers not to send a commission upstream.

## Outcome

The links still work; they carry no tag, and the note says so.
