---
kind: primary
routes:
  web: Web
steps:
  - text: Selects a library file in the list
    kind: actor
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::files
  - text: The Product shows its plate picture, each color and material it prints with and their grams, its estimated time and its pieces per plate
    kind: product
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Thumbnail
          - Colors needed
          - Grams
          - Estimated time
          - Pieces per plate
    contexts:
      web:
        place: hub::dashboard::dash
  - text: Each idle printer's card suggests a head for every color, matching the material first and the color second, and flags a head holding a different material
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
          - Loaded
          - Loaded color
          - Material
    contexts:
      web:
        place: hub::dashboard::dash
---

# See what a file needs

## Trigger

The operator has a file in mind.

## Outcome

The file's needs are on the Dash and every idle printer's card is ready to send it, one head per color.
