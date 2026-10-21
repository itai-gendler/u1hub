---
appliesTo:
  - type: entity
    id: printer-file
    effect: changes
permits:
  - actors:
      - farm-operator
    when:
      - fact: Printing now
        is: 'No'
      - fact: Writable
        is: 'Yes'
references:
  - kind: code
    role: implementation
    target: core/library.js#printerFileOpGuard
---

# Only a copy the printer is not using, and allows writing, is renamed

Before renaming a copy on a printer, the Hub asks the printer live what it is printing; never from a cached answer.
