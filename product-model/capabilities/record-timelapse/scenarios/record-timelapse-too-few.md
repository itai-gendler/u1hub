---
kind: edge
routes:
  web: Web
steps:
  - text: A filmed print completes
    kind: condition
    unattended: true
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
    contexts:
      web:
        place: hub::dashboard::timelapses
  - text: Too few frames are usable, such as with the chamber light off
    kind: condition
    entities:
      - entity: timelapse
        effect: reads
        facts:
          - Frames
    contexts:
      web:
        place: hub::dashboard::timelapses
  - text: The Product discards the frames
    kind: product
    entities:
      - entity: timelapse
        effect: removes
        from: Recording
    contexts:
      web:
        place: hub::dashboard::timelapses
---

# Too few usable frames

## Trigger

A very short print, or a dark chamber.

## Outcome

No video worth keeping, so none is saved.
