---
singleton: true
domain: settings
references:
  - kind: code
    role: implementation
    target: modules/notify.js#compose
---

# Notification settings

Where and when the Hub pushes phone notifications through ntfy.

## Information kept

- **Send notifications** — The one switch; off means no request is ever made.
- **ntfy server** — https://ntfy.sh unless a self-hosted server is set.
- **Topic** — The ntfy topic; required before notifications can be turned on.
- **Topic token** — An access token, only for protected topics.
- **Events** — Which events notify: print finished, paused, error, printer unreachable and maintenance due are on by default; printer back online, print started and print cancelled are off.
