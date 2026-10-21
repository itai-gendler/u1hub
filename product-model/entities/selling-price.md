---
domain: dash
references:
  - kind: code
    role: implementation
    target: modules/margin.js#quote
  - kind: code
    role: implementation
    target: modules/margin.js#register
---

# Selling price

What a piece of one file actually sells for, saved from the worth-printing line, with the numbers that came out of it.

## Information kept

- **File** — The library file it prices.
- **Price per piece** — What one piece sells for.
- **Pieces** — The pieces on the plate, from the x number.
- **Revenue** — What the whole plate brings in.
- **Per printer hour** — Revenue for each hour the plate holds a printer.
- **Per gram** — Revenue for each gram of filament.
- **Margin** — Revenue less the filament cost, also as a share.
- **Below floor** — Whether a piece sells under the sell floor.
- **Saved** — When the price was saved; the latest price for a file wins.
