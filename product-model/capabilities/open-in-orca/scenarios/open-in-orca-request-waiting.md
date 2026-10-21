---
kind: alternate
routes:
  web: Web
steps:
  - text: Presses Open in Orca on a requested model
    kind: actor
    actor: farm-operator
    entities:
      - entity: model
        effect: reads
        facts:
          - File
      - entity: print-request
        effect: reads
        facts:
          - Requested at
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product launches Orca and watches the gcode folder
    kind: product
    actor: farm-operator
    entities:
      - entity: orca-session
        effect: creates
        to: Watching
        facts:
          - Model file
          - Opened at
    contexts:
      web:
        place: hub::dashboard::models
  - text: Orca saves a gcode for the model
    kind: condition
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
      - entity: model
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product links the gcode, queues one print of it in Dispatch and marks the request dispatched
    kind: product
    actor: farm-operator
    entities:
      - entity: orca-session
        effect: changes
        from: Watching
        to: Saved
        facts:
          - Saved gcode
          - Verified
      - entity: library-file
        effect: changes
        facts:
          - Linked model
          - Link verified
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
      - entity: print-request
        effect: changes
        from: Requested
        to: Dispatched
        facts:
          - Gcode
          - Pieces
          - Dispatched at
    contexts:
      web:
        place: hub::dashboard::models
---

# Slicing a requested model queues its print

## Trigger

Someone marked the model for print in 3MF Explorer.

## Outcome

The request shows as queued with its piece count; Dispatch has one print of it.
