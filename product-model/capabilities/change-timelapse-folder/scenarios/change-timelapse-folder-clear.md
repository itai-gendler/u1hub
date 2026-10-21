---
kind: alternate
routes:
  web: Web
steps:
  - text: Clears the folder and presses Save
    kind: actor
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: reads
        facts:
          - Timelapse folder
    contexts:
      web:
        place: hub::dashboard::timelapses
  - text: The Product keeps no folder, so no print is filmed
    kind: product
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: changes
        facts:
          - Timelapse folder
    contexts:
      web:
        place: hub::dashboard::timelapses
---

# Stop saving videos

## Trigger

Videos are no longer wanted.

## Outcome

Nothing is captured while there is nowhere for a video to go.
