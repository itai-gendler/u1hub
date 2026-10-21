---
kind: primary
routes:
  web: Web
steps:
  - text: Ticks or unticks features and presses Save
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
  - text: The Product saves the choice and says it applies on the next Hub restart
    kind: product
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: changes
        facts:
          - Features
    contexts:
      web:
        place: hub::dashboard::settings
---

# Switch a module off

## Trigger

A one-color farm has no use for Spool Match.

## Outcome

After a restart the module is gone from every page.
