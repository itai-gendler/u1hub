---
kind: alternate
routes:
  api: API
steps:
  - text: Posts a model marked for print, with its path and the pairing token
    kind: actor
    actor: 3mf-explorer
    entities:
      - entity: model
        effect: reads
        facts:
          - File
    contexts:
      api:
        place: print-request-api
  - text: A gcode linked to the model is already in the library
    kind: condition
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Linked model
      - entity: model
        effect: reads
        facts: []
    contexts:
      api:
        place: print-request-api
  - text: The Product files the request and queues one print of that gcode in Dispatch, whatever the x number in its name
    kind: product
    actor: 3mf-explorer
    entities:
      - entity: print-request
        effect: creates
        to: Requested
        facts:
          - Model file
          - Designer
          - Title
          - Requested at
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
    contexts:
      api:
        place: print-request-api
  - text: It marks the request dispatched with the gcode's piece count
    kind: product
    actor: 3mf-explorer
    entities:
      - entity: print-request
        effect: changes
        from: Requested
        to: Dispatched
        facts:
          - Gcode
          - Pieces
          - Dispatched at
    contexts:
      api:
        place: print-request-api
---

# Request a model whose gcode exists

## Trigger

The model was sliced before.

## Outcome

Dispatch has one print of the plate; how many times to print it is set there like any other job.

## Edge cases

- When the same gcode already waits in Dispatch, the request rides on that job instead of adding another.
