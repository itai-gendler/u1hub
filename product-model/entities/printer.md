---
relations:
  - entity: head
    verb: has
    cardinality: one-to-many
  - entity: printer-file
    verb: stores
    cardinality: one-to-many
  - entity: logbook-entry
    verb: is logged in
    cardinality: one-to-many
  - entity: timelapse
    verb: is filmed in
    cardinality: one-to-many
references:
  - kind: code
    role: implementation
    target: core/fleet.js#shapeStatus
  - kind: code
    role: implementation
    target: core/settings.js
  - kind: code
    role: implementation
    target: modules/dispatch.js#maintOf
---

# Printer

One machine in the farm, as the Hub knows it. Name, address, type and plug are kept by the Hub; everything about the print it is running is what the printer itself reports, read live over Moonraker.

## Information kept

- **Name** — The printer's name on its card.
- **Address** — Where the printer answers on the network; two printers cannot share one.
- **Smart plug** — Optional: a Shelly plug (with live watts) or a generic plug with on and off addresses.
- **Plug power** — On or Off, as the plug reports it.
- **Print state** — As the printer reports it: Standby, Printing, Paused, Complete, Cancelled or Error, or Offline when it does not answer.
- **Printing file** — The file the printer is printing or paused on.
- **Progress** — How far the print is, computed the way the touchscreen does.
- **Time left** — The slicer's estimate scaled by progress.
- **Layer** — The current layer of the total.
- **Bed temperature** — The bed's temperature and target.
- **Pause reason** — The firmware's own words for a pause or error.
- **Free storage** — Free space on the printer's storage; warned under 2 GB.
- **Print hours** — The printer's lifetime print time from its own history.
- **Plate objects** — The objects on the plate of a running print and which are skipped.
- **Maintenance note** — Why the printer is down for maintenance.
- **Down since** — When it was taken down; kept when the note is changed.

## States

### In service

Takes work from Dispatch and from Print on best printer.

### Down for maintenance

Taken out of service on purpose; nothing new is planned or sent to it.
