---
id: u1-print-hub
summary: >-
  One dashboard for a farm of Snapmaker U1 printers: see every machine, send prints, plan the week across the farm, track spools and filament, keep a logbook, and get a second pair of eyes before
  printing.
category: 3d-printing
tags:
  - print-farm
  - snapmaker-u1
  - klipper
  - gcode
  - filament
authors:
  - name: dlgambill
    url: https://github.com/dlgambill
license: MIT
languages:
  - en
limitations:
  - 'Nothing is installed on the printers: the Hub works through the software they already run, and what a printer reports is the printer''s own word.'
  - The Hub never starts a print by itself; every print, the next planned one included, starts from a person's tap.
  - One shared password guards the whole Hub, or none at all; there are no user accounts or roles.
  - The AI buttons use the operator's own Anthropic API key and send a short brief only when pressed.
  - Printer types other than the Snapmaker U1 are in beta and work against stock Klipper and Moonraker.
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: doc
    role: context
    target: docs/CHANGELOG.md
  - kind: doc
    role: context
    target: BETA-TESTING.md
  - kind: code
    role: implementation
    target: server.js
  - kind: code
    role: implementation
    target: core/modules.js
---

# U1 Print Hub

U1 Print Hub is a self-hosted web app for a farm of Snapmaker U1 printers, and other Klipper printers in beta. It runs on a computer that stays on, and any browser or phone on the network opens it like a web page, or from anywhere through a Cloudflare tunnel. From one dashboard the farm operator sees every printer's live status and loaded colors, sends sliced gcode to any idle machine with each color mapped to a head, plans the queue across the farm inside the hours someone is around (Dispatch), tracks every roll of filament and what the schedule needs (Spools and Resources), keeps the 3MF projects not yet sliced and hands them to Snapmaker Orca (Models), and keeps a logbook and upkeep schedule per printer. Printers, smart plugs, ntfy, Spoolman, Anthropic and Cloudflare are outside systems the Hub talks to; the model promises only what the Hub itself does.

## Intent

"One dashboard for a whole farm of Snapmaker U1 printers. Other Klipper printers can join in too (that part is in beta)."

"You run the Hub on a computer that stays on. Your phone, or any browser, opens it like a web page. From there you can see every machine at once, send prints, watch cameras, plan your printing week, know what filament to buy before you run out, and - new in 2.28 - ask what settings a model wants before you slice it, and whether a plate is worth printing at all."

"Nothing gets installed on the printers. The Hub talks to the software they already run, and nothing leaves your network unless you turn remote access on, ask for a phone notification, or press one of the two AI buttons with your own key in place." (README)
