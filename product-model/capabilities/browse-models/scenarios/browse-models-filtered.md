---
kind: alternate
routes:
  web: Web
steps:
  - text: Picks a designer, types a filter, or sorts by designer, name, newest, oldest, random or most printed
    kind: actor
    actor: farm-operator
    entities:
      - entity: model
        effect: reads
        facts:
          - Designer
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product shows that part of the shelf in that order and keeps the choice in the address bar, so a refresh or a shared link opens the same shelf
    kind: product
    actor: farm-operator
    entities:
      - entity: model
        effect: reads
        facts:
          - Designer
          - Name
          - Printed count
    contexts:
      web:
        place: hub::dashboard::models
---

# Narrow and order the shelf

## Trigger

The shelf holds thousands of files.

## Outcome

Most printed counts completed jobs in the printers' own history and says how many it could match, rather than guessing.
