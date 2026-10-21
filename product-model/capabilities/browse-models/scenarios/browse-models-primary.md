---
kind: primary
routes:
  web: Web
steps:
  - text: Opens Models
    kind: actor
    actor: farm-operator
    entities:
      - entity: model
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product lists the 3MF files in the models folder, newest first, each with its plate render, a strip of its painted colors and its objects
    kind: product
    actor: farm-operator
    entities:
      - entity: model
        effect: reads
        facts:
          - File
          - Designer
          - Name
          - Plate render
          - Colors
          - Objects
          - Added
      - entity: models-settings
        effect: reads
        facts:
          - Models folder
    contexts:
      web:
        place: hub::dashboard::models
---

# Look through the shelf

## Trigger

The operator looks for something to slice next.

## Outcome

What was just saved is at the top; the twelve biggest designers are one tap away and a search box covers the rest.
