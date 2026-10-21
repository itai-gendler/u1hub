---
kind: alternate
routes:
  web: Web
steps:
  - text: With a file selected, presses Send to Dispatch
    kind: actor
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product opens Dispatch with the file ready under Add job
    kind: product
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
      - entity: job
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: Sets the copies and presses Add
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product creates a queued job for the file
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
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Send the selected file to Dispatch

## Trigger

A phone has no drag and drop; this is the way in from the Dash.

## Outcome

The file is a job in Dispatch.
