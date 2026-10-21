---
kind: alternate
routes:
  web: Web
steps:
  - text: Presses Send to Dispatch on an Orca session that saved a gcode
    kind: actor
    actor: farm-operator
    entities:
      - entity: orca-session
        effect: reads
        facts:
          - Saved gcode
          - Model file
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product creates one queued job for the saved gcode and records it on the session
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: creates
        to: Queued
        facts:
          - File
          - Copies
          - Remaining
          - Deadline
          - Priority
          - Be here at the finish
          - Runtime
          - Colors
          - Source
      - entity: orca-session
        effect: changes
        facts:
          - Queued job
    contexts:
      web:
        place: hub::dashboard::models
---

# Send a freshly sliced gcode to Dispatch

## Trigger

A model was just sliced in Orca.

## Outcome

The gcode is in Dispatch; pressing again answers with the same job instead of adding another, and the session leaves the strip.
