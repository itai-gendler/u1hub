---
kind: primary
routes:
  web: Web
steps:
  - text: Types the G-code folder and presses Save
    kind: actor
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: reads
        facts:
          - G-code folder
    contexts:
      web:
        place: hub::dashboard::settings
  - text: The Product saves it and reads the library from there; each added printer type's folder sits inside it
    kind: product
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: changes
        facts:
          - G-code folder
      - entity: printer-type
        effect: reads
        facts:
          - Folder
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::settings
---

# Point the library at the slicer's output

## Trigger

The slicer saves somewhere new.

## Outcome

The file list shows that folder's gcode.
