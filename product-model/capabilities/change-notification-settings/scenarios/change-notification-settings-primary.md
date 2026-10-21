---
kind: primary
routes:
  web: Web
steps:
  - text: Sets the topic, picks the events, ticks Send notifications and saves
    kind: actor
    actor: farm-operator
    entities:
      - entity: notification-settings
        effect: reads
        facts:
          - ntfy server
          - Topic
          - Events
          - Send notifications
    contexts:
      web:
        place: hub::dashboard::phone-notifications
  - text: The Product keeps them and sends the chosen events from now on
    kind: product
    actor: farm-operator
    entities:
      - entity: notification-settings
        effect: changes
        facts:
          - ntfy server
          - Topic
          - Topic token
          - Events
          - Send notifications
    contexts:
      web:
        place: hub::dashboard::phone-notifications
---

# Get a message when a print finishes

## Trigger

The operator wants to know without watching the page.

## Outcome

The phone gets the chosen events; untick one box and no request is made at all.

## Edge cases

- Send a test posts a test message with what is typed, before saving.
