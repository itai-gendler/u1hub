---
kind: primary
routes:
  web: Web
steps:
  - text: Opens a printer's badge on a file, chooses Send to… and picks another printer
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer-file
        as: source
        effect: reads
        facts:
          - Name
      - entity: printer
        as: from
        effect: reads
        facts:
          - Name
      - entity: printer
        as: to
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::files
  - text: The Product streams the file from one printer to the other with live progress
    kind: product
    actor: farm-operator
    entities:
      - entity: printer-file
        as: source
        effect: reads
        facts:
          - Name
          - Size
      - entity: printer
        as: from
        effect: reads
        facts: []
      - entity: printer
        as: to
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::files
  - text: The Product lists the destination again and checks the copy arrived at the same size
    kind: product
    actor: farm-operator
    entities:
      - entity: printer-file
        effect: creates
        facts:
          - Name
          - Size
          - Modified
        as: copy
      - entity: printer
        as: to
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::files
---

# Copy a file to another printer

## Trigger

A file sliced straight to one printer is wanted on another.

## Outcome

The destination printer stores a size-checked copy; the source copy is unchanged.
