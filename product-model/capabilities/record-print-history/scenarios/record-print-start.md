---
kind: primary
routes:
  web: Web
steps:
  - text: A printer goes from not printing to printing
    kind: condition
    unattended: true
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
          - Printing file
    contexts:
      web:
        place: hub::dashboard::files
  - text: The Product stamps the file's last-printed time
    kind: product
    entities:
      - entity: library-file
        effect: changes
        facts:
          - Last printed
    contexts:
      web:
        place: hub::dashboard::files
---

# A print starts

## Trigger

Any print starts, from the Hub or the touchscreen.

## Outcome

The file list shows when the file was last printed.

## Edge cases

- A print that was already running when the Hub started, or one resumed from a pause, is not a new start.
