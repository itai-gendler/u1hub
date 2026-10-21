---
appliesTo:
  - type: capability
    id: send-notification
  - type: capability
    id: change-notification-settings
references:
  - kind: code
    role: implementation
    target: modules/notify.js#register
---

# Notifications off means no request at all

With Send notifications off, or no topic, nothing is posted. A message that fails is recorded and never retried.
