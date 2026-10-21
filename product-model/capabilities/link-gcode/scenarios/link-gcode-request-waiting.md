---
kind: alternate
routes:
  web: Web
steps:
  - text: Links a gcode to a model that has a print request waiting
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
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product links the gcode, queues one print of it in Dispatch and marks the request dispatched
    kind: product
    actor: farm-operator
    entities:
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

# Linking answers a waiting request

## Trigger

The requested model's gcode exists but was never linked.

## Outcome

The request shows as queued.
