---
availability:
  - place: hub::dashboard
domain: spools
references:
  - kind: code
    role: implementation
    target: rfid.js#loadSnapshot
  - kind: code
    role: implementation
    target: scripts/refresh-filament-db.js
---

# Update the filament library

Pulling the current FilamentColors.xyz catalog on request. Nothing is fetched on a scan, so a farm with no internet keeps the shipped library.
