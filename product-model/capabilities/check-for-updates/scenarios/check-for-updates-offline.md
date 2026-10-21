---
kind: edge
routes:
  web: Web
steps:
  - text: The daily check comes round on a farm network with no route out
    kind: condition
    unattended: true
    entities:
      - entity: hub-settings
        effect: reads
        facts:
          - Update checks
    contexts:
      web:
        place: hub::dashboard::hub-version
  - text: The Product records that the check was skipped, quietly
    kind: product
    entities:
      - entity: hub-settings
        effect: reads
        facts:
          - Latest version
    contexts:
      web:
        place: hub::dashboard::hub-version
---

# No internet

## Trigger

An isolated LAN.

## Outcome

Offline looks exactly like no update known; no banner, no retry loop.
