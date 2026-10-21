---
kind: alternate
routes:
  web: Web
steps:
  - text: A printer in service starts, or is found printing, a file a queued job is waiting to print
    kind: condition
    unattended: true
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
          - Printing file
      - entity: job
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product attaches the copy to that job so it is not planned again
    kind: product
    entities:
      - entity: job
        effect: changes
        from: Queued
        to: Printing
        facts:
          - Printing on
          - Starting on
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# A queued file starts printing

## Trigger

A print was started from the Dash, the touchscreen, or before Dispatch knew of it.

## Outcome

The copy counts against its job.

## Edge cases

- A copy started from the Hub that never shows as printing within five minutes puts a notice on its job.
