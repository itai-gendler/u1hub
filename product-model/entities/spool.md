---
domain: spools
relations:
  - entity: color-mapping
    verb: is chosen by
    cardinality: one-to-many
references:
  - kind: code
    role: implementation
    target: rfid.js#cleanIdentity
  - kind: code
    role: implementation
    target: modules/resources.js#readShelf
---

# Spool

A physical roll of filament the Hub knows: its identity, where it is loaded, and how much is left. A spool is found by its RFID tag, by the QR label the Hub prints for it, or in the list.

## Information kept

- **Brand** — The maker.
- **Material** — The base material, such as PLA.
- **Variant** — The material line, such as Silk or Matte.
- **Color name** — The color's name.
- **Color** — The color; a measured color when it was picked from the filament library.
- **Colors** — Two or three colors for a gradient or multi-color roll.
- **Hot end temperature** — The recommended nozzle temperature.
- **Bed temperature** — The recommended bed temperature.
- **Tags** — The RFID tags that identify it; a spool can carry none.
- **Origin** — Picked from the filament library, typed in, sampled from a loaded head, or imported from Spoolman.
- **Grams left** — What is left on the roll; blank until someone enters it.
- **Net weight** — A full roll's filament weight; 1000 g unless set.
- **Price per roll** — What the roll cost; never assumed.
- **Buy link** — Where to buy it again.
- **Notes** — Free notes; an imported roll notes its Spoolman number and location.
- **Active** — No for a roll archived or deleted in Spoolman; inactive rolls are left out of color matching.
- **Loaded in** — The printer and head it is in.

## States

### On the shelf

Not recorded in any head.

### Loaded

Recorded in one head of one printer.
