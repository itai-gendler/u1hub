---
singleton: true
domain: dispatch
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#register
---

# Dispatch settings

How Dispatch plans the farm: when someone is around, when the queue must be done, and whether the plan may move.

## Information kept

- **Attended hours** — A standing week of up to six blocks a day when someone is around to swap spools and clear beds; 08:00-22:00 on weekdays and 09:00-22:00 at weekends unless changed.
- **Week overrides** — Hours for one calendar week only; the newest 26 weeks are kept.
- **Finish jobs** — Anytime (prints may run while nobody is around, the default) or only while someone is here.
- **When a print finishes** — Keep every roll loaded, unload the rolls the next job on that printer does not use, or unload every roll the print used. Held at keep every roll loaded for now.
- **Completion target** — One moment the whole queue should be done by; a fallback for jobs with no deadline of their own.
- **Locked plan** — The placed copies frozen when the plan was locked.

## States

### Fluid

The plan is recomputed as printers finish and work changes.

### Locked

The plan the operator locked is held still; copies that ran or were removed drop off it and new work is reported, not placed.
