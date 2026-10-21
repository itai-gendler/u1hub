---
appliesTo:
  - type: entity
    id: head
    effect: changes
    facts:
      - Loaded color
permits:
  - actors:
      - farm-operator
    when:
      - fact: Official spool
        is: 'No'
      - fact: Loaded
        is: 'Yes'
      - entity: printer
        fact: Print state
        is-not: Printing
      - entity: printer
        fact: Print state
        is-not: Paused
references:
  - kind: code
    role: implementation
    target: core/filament.js
---

# Only an idle printer's untagged heads change color

A head's color is set from the Hub only while its printer is neither printing nor paused, only when filament is loaded, and never for an official Snapmaker RFID spool, whose color comes from its tag. The printer's own read-back decides whether it took.
