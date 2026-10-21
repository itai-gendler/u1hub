---
entities:
  - entity: notification-settings
    shows:
      - Send notifications
      - ntfy server
      - Topic
      - Events
    collects:
      - Send notifications
      - ntfy server
      - Topic
      - Topic token
      - Events
references:
  - kind: code
    role: implementation
    target: public/modules/notify-ui.js
---

# Phone notifications

The ntfy server, topic and token, the events to send, the one switch, and the last delivery.
