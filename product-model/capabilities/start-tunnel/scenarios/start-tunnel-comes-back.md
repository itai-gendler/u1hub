---
kind: alternate
routes:
  web: Web
steps:
  - text: The tunnel program exits unexpectedly, with Start with Hub ticked
    kind: condition
    unattended: true
    entities:
      - entity: tunnel
        effect: reads
        facts:
          - Start with Hub
    contexts:
      web:
        place: hub::dashboard::remote-access
  - text: The Product marks the tunnel failed and says why
    kind: product
    entities:
      - entity: tunnel
        effect: changes
        from: Running
        to: Failed
        facts:
          - Public address
    contexts:
      web:
        place: hub::dashboard::remote-access
  - text: It starts the tunnel again after 5 seconds, then 10, doubling up to 5 minutes, and says when the next try is
    kind: product
    entities:
      - entity: tunnel
        effect: changes
        from: Failed
        to: Starting
        facts: []
    contexts:
      web:
        place: hub::dashboard::remote-access
  - text: Once a connection registers the address works again
    kind: product
    entities:
      - entity: tunnel
        effect: changes
        from: Starting
        to: Running
        facts:
          - Public address
    contexts:
      web:
        place: hub::dashboard::remote-access
---

# The tunnel comes back on its own

## Trigger

The tunnel dropped overnight.

## Outcome

Remote access returns without anyone at the Hub.

## Edge cases

- With Start with Hub ticked, the tunnel also starts when the Hub starts.
- A quick tunnel comes back on a new address.
