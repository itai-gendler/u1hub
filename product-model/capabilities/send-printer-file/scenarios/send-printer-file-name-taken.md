---
kind: validation
routes:
  web: Web
steps:
  - text: Opens a printer's badge on a file, chooses Send to… and picks a destination
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer-file
        effect: reads
        facts:
          - Name
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::files
  - text: A file of that name is already at the destination
    kind: condition
    entities:
      - entity: printer-file
        effect: reads
        facts:
          - Name
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::files
  - text: The Product refuses and asks for that copy to be deleted or renamed first
    kind: product
    actor: farm-operator
    entities:
      - entity: printer-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::files
---

# Refuse to overwrite at the destination

## Trigger

The name is taken where the copy would go.

## Outcome

Nothing is copied and nothing is overwritten, so a file a printer is using can never be replaced underneath it.
