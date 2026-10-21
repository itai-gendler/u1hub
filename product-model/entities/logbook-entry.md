---
domain: logbook
references:
  - kind: code
    role: implementation
    target: modules/logbook.js#register
---

# Logbook entry

What happened to one printer and what fixed it, stamped with the printer's print hours at the time.

## Information kept

- **Printer name** — The printer, kept by name too so the log reads right after a rename.
- **Kind** — Issue, Maintenance or Note.
- **What happened** — What went wrong or what was done.
- **Fix** — What fixed it; an issue without one is still open.
- **When** — When it happened.
- **Print hours** — The printer's lifetime print hours at the time.
- **Source** — Written by hand, by the firmware's pause or error, by taking the printer out of service, or by the schedule.
- **File** — The file printing when the firmware paused or failed.
- **Back in service** — For an outage, when the printer came back.
