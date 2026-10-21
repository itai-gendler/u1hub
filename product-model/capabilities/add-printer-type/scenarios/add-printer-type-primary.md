---
kind: primary
routes:
  web: Web
steps:
  - text: Names the type, such as SV06 Plus ACE, and presses + Add printer type
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer-type
        effect: reads
        facts: []
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::printers
  - text: The Product creates the type with its own subfolder of the G-code folder and the next accent color, and adds its switcher tab
    kind: product
    actor: farm-operator
    entities:
      - entity: printer-type
        effect: creates
        facts:
          - Name
          - Accent color
          - Folder
          - Built-in
          - Printers
      - entity: hub-settings
        effect: reads
        facts:
          - G-code folder
    contexts:
      web:
        place: hub::dashboard::printers
---

# Add a new kind of printer

## Trigger

The farm adds a different printer model.

## Outcome

The type's folder and tab are ready; printers can be added into it.
