---
actors:
  - farm-operator
references:
  - kind: code
    role: implementation
    target: public/app.js#handleUid
  - kind: code
    role: implementation
    target: public/app.js#openBindPanel
---

# Identify a new spool

## Goal

A roll with a tag the Hub has never seen gets an identity.

## Success criterion

Tapping the roll's tag opens its spool card.
