---
domain: dispatch
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#createJob
  - kind: code
    role: implementation
    target: modules/dispatch.js#completeCopy
---

# Job

A file Dispatch is to print a number of times, planned across the farm. A job leaves the list when its last copy finishes.

## Information kept

- **File** — The library file to print.
- **Copies** — How many copies were asked for, 1 to 999.
- **Remaining** — Copies still to print.
- **Deadline** — When its copies must be done, if it has one.
- **Priority** — 1 to 5, 3 being normal; breaks ties between jobs that share a deadline.
- **Be here at the finish** — Plan its copies to finish while someone is around.
- **Runtime** — Minutes per copy: typed by the operator, learned from earlier runs, or the slicer's estimate, in that order.
- **Colors** — The colors the file prints with, and whether it needs a multi-color printer.
- **Source** — Where it was added from: the Dispatch tab, an Orca session or a print request.
- **Notice** — Something the operator should know, such as a copy that ended without completing.
- **Pinned printer** — The printer the operator moved it to, if any.
- **Pushed back behind** — The job it waits for, if it was pushed back.
- **Starting on** — The printer a copy was just started on, until that printer reports it printing; five minutes at most.
- **Printing on** — The printer running one of its copies.

## States

### Queued

Waiting for a printer; its copies are planned.

### Paused

Held out of the plan by the operator.

### Printing

One of its copies is on a printer.
