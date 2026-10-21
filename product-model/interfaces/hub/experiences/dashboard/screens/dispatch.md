---
entities:
  - entity: job
    shows:
      - File
      - Copies
      - Remaining
      - Deadline
      - Priority
      - Be here at the finish
      - Runtime
      - Colors
      - Notice
      - Pinned printer
      - Pushed back behind
      - Printing on
      - Starting on
      - Source
    collects:
      - Copies
      - Deadline
      - Priority
      - Be here at the finish
      - Runtime
      - Pinned printer
  - entity: bundle
    shows:
      - Name
      - Deadline
    collects:
      - Name
  - entity: printer
    shows:
      - Name
      - Print state
      - Time left
      - Maintenance note
      - Down since
  - entity: dispatch-settings
    shows:
      - Attended hours
      - Week overrides
      - Finish jobs
      - When a print finishes
      - Completion target
      - Locked plan
    collects:
      - Attended hours
      - Week overrides
      - Finish jobs
      - When a print finishes
      - Completion target
  - entity: spool
    shows:
      - Color name
  - entity: library-file
    shows:
      - Name
      - Run times
references:
  - kind: code
    role: implementation
    target: public/modules/dispatch-ui.js
---

# Dispatch

Attended hours, the completion target and its report, Add job, the JOBS list and the plan: a timeline lane per printer.
