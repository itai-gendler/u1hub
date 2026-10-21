---
kind: alternate
routes:
  web: Web
steps:
  - text: A U1 being filmed has its print cancelled, or it errors
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
  - text: The Product throws the frames away
    kind: product
    entities:
      - entity: timelapse
        effect: removes
        from: Recording
    contexts:
      web:
        place: hub::dashboard::timelapses
---

# A cancelled or failed print

## Trigger

The print did not finish.

## Outcome

No video is made.
