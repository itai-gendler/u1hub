---
kind: validation
routes:
  web: Web
steps:
  - text: Ticks Send notifications with no topic, or a topic with characters ntfy does not allow
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::phone-notifications
  - text: The Product refuses and asks for a topic of letters, digits, - and _
    kind: product
    actor: farm-operator
    entities:
      - entity: notification-settings
        effect: reads
        facts:
          - Topic
    contexts:
      web:
        place: hub::dashboard::phone-notifications
---

# Notifications need a topic

## Trigger

The topic was left blank.

## Outcome

The Hub never posts to the root of a server.
