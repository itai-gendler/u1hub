---
kind: primary
routes:
  web: Web
steps:
  - text: With a file selected, presses Print on best printer
    kind: actor
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Colors needed
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product looks at every idle printer in service and picks the one whose loaded heads match every color closest, in the right material
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
      - entity: head
        effect: reads
        facts:
          - Loaded color
          - Material
    contexts:
      web:
        place: hub::dashboard::dash
  - text: It names the printer and counts down five seconds with a Cancel
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: Nobody cancels
    kind: condition
    entities: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: It checks the printer is still idle and still the best match, then sends and starts the file with that mapping
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
      - entity: printer-file
        effect: creates
        facts:
          - Name
          - Size
          - Modified
      - entity: head
        effect: reads
        facts:
          - Number
    contexts:
      web:
        place: hub::dashboard::dash
---

# Send to the printer that already has every color

## Trigger

Any free printer with the right rolls will do.

## Outcome

The print is running on a printer that needed no spool swap, and its card shows the progress.
