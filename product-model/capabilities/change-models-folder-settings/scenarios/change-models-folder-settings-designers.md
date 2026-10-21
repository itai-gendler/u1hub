---
kind: alternate
routes:
  web: Web
steps:
  - text: Writes folder name = Display Name lines in Designer names and presses Save names
    kind: actor
    actor: farm-operator
    entities:
      - entity: models-settings
        effect: reads
        facts:
          - Designer names
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product shows those folders under their display names, merging two folders that are one designer, without moving a file
    kind: product
    actor: farm-operator
    entities:
      - entity: models-settings
        effect: changes
        facts:
          - Designer names
    contexts:
      web:
        place: hub::dashboard::models
---

# Rename or merge designers

## Trigger

A designer's folder is misspelled, or one designer has two folders.

## Outcome

The designer list reads right.
