---
kind: alternate
routes:
  web: Web
steps:
  - text: Types words into the filter, such as baby* -test
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::files
  - text: The Product keeps the names that match every word, reading * and ? as wildcards and a word starting with a minus as one to exclude
    kind: product
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::files
---

# Narrow the list with a filter

## Trigger

The list is too long to scan.

## Outcome

Only matching files are listed, in the chosen order: newest, oldest, name or size.
