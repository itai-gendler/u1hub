---
kind: primary
routes:
  web: Web
steps:
  - text: A printer finishes, pauses with a reason, errors, or has not answered for 90 seconds, and that event is chosen
    kind: condition
    unattended: true
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
          - Pause reason
      - entity: notification-settings
        effect: reads
        facts:
          - Send notifications
          - Events
    contexts:
      web:
        place: hub::dashboard::phone-notifications
  - text: The Product posts a message to the topic with the printer, the file and the time it took or the firmware's reason
    kind: product
    entities:
      - entity: notification-settings
        effect: reads
        facts:
          - ntfy server
          - Topic
          - Topic token
      - entity: printer
        effect: reads
        facts:
          - Name
          - Printing file
    contexts:
      web:
        place: hub::dashboard::phone-notifications
---

# A printer finishes, pauses or goes quiet

## Trigger

Something happened the operator asked to hear about.

## Outcome

The phone shows it, a paused print with the firmware's own words.
