---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Suggest settings on a model card, picks the printer and presses Ask
    kind: actor
    actor: farm-operator
    entities:
      - entity: model
        effect: reads
        facts:
          - File
          - Name
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::models
  - text: 'The Product measures the model from its meshes: size, how much overhangs, undersides that float, bed contact, painted faces and volume'
    kind: product
    actor: farm-operator
    entities:
      - entity: model
        effect: reads
        facts:
          - Objects
          - Colors
    contexts:
      web:
        place: hub::dashboard::models
  - text: It sends those numbers, the designer's own project settings, the printer's loaded heads and the plate render to Claude with the operator's key
    kind: product
    actor: farm-operator
    entities:
      - entity: model
        effect: reads
        facts:
          - Plate render
      - entity: head
        effect: reads
        facts:
          - Loaded color
          - Material
      - entity: ai-settings
        effect: reads
        facts:
          - Anthropic API key
          - Claude model
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::models
  - text: It shows a table of setting, value to use, the designer's value and why, mapping the project's colors to loaded heads and listing what to watch
    kind: product
    actor: farm-operator
    entities:
      - entity: head
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::models
---

# Ask what a model wants

## Trigger

A designer's profile was made for another printer.

## Outcome

The suggestions are on screen, with Open in Orca with these settings beneath them; the file itself is untouched.

## Edge cases

- The same model on the same loadout is answered from the local store for free; Ask again bypasses it.
- Without a key nothing is sent and Settings is named.
