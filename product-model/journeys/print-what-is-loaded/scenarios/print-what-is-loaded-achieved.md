---
kind: primary
result: achieved
routes:
  web: Web
steps:
  - text: Opens Match and taps a free printer
    kind: actor
    capability: find-printable-files
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
      - entity: head
        effect: reads
        facts:
          - Loaded color
    contexts:
      web:
        place: hub::dashboard::match
  - text: The Product lists the files its loaded colors cover, best match first
    kind: product
    capability: find-printable-files
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
          - Colors needed
    contexts:
      web:
        place: hub::dashboard::match
  - text: Presses Print on a file
    kind: actor
    capability: find-printable-files
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::match
  - text: The Product selects the file on the Dash and scrolls to that printer's card
    kind: product
    capability: find-printable-files
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: Confirms the suggested heads and presses Print
    kind: actor
    capability: print-file
    actor: farm-operator
    entities:
      - entity: head
        effect: reads
        facts:
          - Number
          - Loaded color
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product sends and starts the file
    kind: product
    capability: print-file
    actor: farm-operator
    entities:
      - entity: printer-file
        effect: creates
        facts:
          - Name
          - Size
          - Modified
      - entity: printer
        effect: reads
        facts:
          - Print state
    contexts:
      web:
        place: hub::dashboard::dash
---

# From Match to Print

## Trigger

A printer is idle and nobody wants to swap rolls.

## Outcome

The printer is printing a file that needed nothing mounted.
