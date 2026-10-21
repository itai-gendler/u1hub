---
kind: edge
routes:
  web: Web
steps:
  - text: A chosen event happens
    kind: condition
    unattended: true
    entities:
      - entity: notification-settings
        effect: reads
        facts:
          - Events
    contexts:
      web:
        place: hub::dashboard::phone-notifications
  - text: ntfy does not answer within eight seconds or refuses
    kind: condition
    entities:
      - entity: notification-settings
        effect: reads
        facts:
          - ntfy server
    contexts:
      web:
        place: hub::dashboard::phone-notifications
  - text: The Product records the failure on the Phone notifications card and does not retry
    kind: product
    entities: []
    contexts:
      web:
        place: hub::dashboard::phone-notifications
---

# ntfy does not answer

## Trigger

The server is down.

## Outcome

The card shows the last error; a stale message thirty seconds later would not help.
