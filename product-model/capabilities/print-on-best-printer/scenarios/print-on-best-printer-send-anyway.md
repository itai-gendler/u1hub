---
kind: alternate
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
  - text: No idle printer holds every color, and the closest misses only one or two
    kind: condition
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
      - entity: head
        effect: reads
        facts:
          - Loaded color
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product names the closest printer, the colors it is missing, and which loaded roll would stand in for each, warning where the material differs
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
      - entity: head
        effect: reads
        facts:
          - Number
          - Loaded color
          - Material
    contexts:
      web:
        place: hub::dashboard::dash
  - text: Presses Send to that printer anyway
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product counts down five seconds with a Cancel
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
  - text: It checks the printer is still idle with the same rolls in the same heads, then sends and starts the file with those stand-ins
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
      - entity: printer-file
        effect: creates
        facts:
          - Name
          - Size
          - Modified
    contexts:
      web:
        place: hub::dashboard::dash
---

# Send to the closest printer anyway

## Trigger

A light blue can stand in for cyan, and the operator's eye beats the threshold.

## Outcome

The print runs with the stand-in colors the operator saw before it was sent.
