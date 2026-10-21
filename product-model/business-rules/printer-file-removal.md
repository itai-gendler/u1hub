---
appliesTo:
  - type: entity
    id: printer-file
    effect: removes
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

# Only a copy the printer is not using, and allows writing, is deleted

The file a printer is printing or paused on cannot be deleted from the Hub.
