---
kind: primary
routes:
  web: Web
steps:
  - text: Opens Attributes on a model card, sets the designer or the name, and saves
    kind: actor
    actor: farm-operator
    entities:
      - entity: model
        effect: reads
        facts:
          - Designer
          - Name
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product shows the model under its corrected designer and name, and offers to move the file to match
    kind: product
    actor: farm-operator
    entities:
      - entity: model
        effect: changes
        facts:
          - Designer
          - Name
    contexts:
      web:
        place: hub::dashboard::models
---

# Correct a designer

## Trigger

The folder a model sits in names the wrong designer.

## Outcome

The card reads right; a blank field goes back to what the folders say.
