---
appliesTo:
  - type: capability
    id: track-job-copies
  - type: entity
    id: job
    effect: changes
    facts:
      - Remaining
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#sameFile
  - kind: code
    role: implementation
    target: modules/dispatch.js#endedWithout
---

# A copy is done only when its printer says complete

A copy counts as printed only when the printer holding it reports complete with the job's file, of the same printer type and path. A print that is cancelled, errors or returns to standby leaves the copy owed and frees the printer.
