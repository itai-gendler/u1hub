---
kind: primary
routes:
  web: Web
steps:
  - text: Types a folder for finished videos and presses Save
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
  - text: The Product keeps the folder, creates it if needed, and says whether it found ffmpeg
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

# Choose where videos go

## Trigger

Timelapses were just turned on.

## Outcome

The next U1 print is filmed and its video lands in that folder.
