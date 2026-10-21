---
appliesTo:
  - type: capability
    id: add-upkeep-task
  - type: entity
    id: upkeep-task
    effect: creates
references:
  - kind: code
    role: implementation
    target: modules/logbook.js#register
---

# A new upkeep task counts from the day it is added

Unless never done yet is ticked, every printer the task covers starts its clock at the moment the task is added, at its current print hours; a printer added to the farm later starts its clock when its hours are first read.
