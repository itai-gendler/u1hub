---
kind: alternate
routes:
  web: Web
steps:
  - text: Unticks the box under Supporting the project in Settings
    kind: actor
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: reads
        facts:
          - Affiliate links
    contexts:
      web:
        place: hub::dashboard::settings
  - text: The Product stops adding the tag to any link, at once
    kind: product
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: changes
        facts:
          - Affiliate links
    contexts:
      web:
        place: hub::dashboard::settings
---

# Untick the box in Settings

## Trigger

Settings is where the operator looked for it.

## Outcome

Off means off on both pages.
