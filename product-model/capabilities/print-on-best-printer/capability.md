---
availability:
  - place: hub::dashboard
domain: dash
references:
  - kind: code
    role: implementation
    target: public/app.js#pickBestPrinter
  - kind: code
    role: implementation
    target: public/app.js#autoPickCountdown
  - kind: code
    role: implementation
    target: public/app.js#autoPickRefused
---

# Print on best printer

Letting the Hub pick the printer: among idle printers in service that can print colors, the one that already holds every color the file needs, close in shade and the right material, with five seconds to cancel before it sends.
